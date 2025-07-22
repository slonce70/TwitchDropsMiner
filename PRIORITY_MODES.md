# Priority Modes Documentation

This document explains how the different priority modes work in TwitchDropsMiner.

## Overview

Priority modes determine the order in which campaigns are processed for mining. There are three available modes:

## 1. Priority List Only

**Behavior**: Only mines games that are explicitly added to your priority list.

**How it works**:
- Only campaigns for games in your priority list will be considered
- Games are processed in the order they appear in your priority list
- All other campaigns are completely ignored
- Exclude list still applies

**Use case**: When you only want to mine specific games and ignore everything else.

## 2. Ending Soonest

**Behavior**: Mines campaigns that are ending soonest first, **completely ignoring priority list order**.

**How it works**:
- All eligible campaigns are sorted by their end time (earliest first)
- Priority list is used only to determine which games to include/exclude (not for ordering)
- Games not in priority list are still included unless explicitly excluded
- Exclude list still applies

**Use case**: When you want to maximize drop collection by focusing on time-sensitive campaigns.

**Important**: This mode ignores the priority list order entirely. If you have a priority list, it will only be used to filter which games to include, not to determine the mining order.

## 3. Low Availability First

**Behavior**: Mines campaigns with fewer available channels first, while respecting priority list order.

**How it works**:
- Campaigns are first sorted by priority list order
- Within each priority level, campaigns with lower availability (fewer channels) are processed first
- Games not in priority list are processed last, sorted by availability
- Exclude list still applies

**Use case**: When you want to mine rare drops (with few streamers) while maintaining your priority preferences.

## Priority List vs Exclude List

- **Priority List**: Determines which games to prioritize and in what order (except in "Ending Soonest" mode)
- **Exclude List**: Always prevents specific games from being mined, regardless of priority mode

## Examples

### Example 1: Priority List Only
- Priority List: [Game A, Game B, Game C]
- Available Campaigns: Game A, Game B, Game C, Game D, Game E
- **Result**: Only mines Game A → Game B → Game C (in that order)

### Example 2: Ending Soonest
- Priority List: [Game A, Game B, Game C]
- Available Campaigns: Game A (ends in 5 days), Game B (ends in 2 days), Game D (ends in 1 day), Game E (ends in 3 days)
- **Result**: Mines Game D → Game B → Game E → Game A (sorted by end time, priority list ignored for ordering)

### Example 3: Low Availability First
- Priority List: [Game A, Game B, Game C]
- Game A: 10 channels available
- Game B: 3 channels available  
- Game D: 1 channel available
- **Result**: Mines Game B (3 channels) → Game A (10 channels) → Game D (1 channel)