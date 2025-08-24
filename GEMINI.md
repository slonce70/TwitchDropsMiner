## Project Overview

This project, "Twitch Drops Miner," is a Python application designed to automatically "mine" timed Twitch drops. It allows users to collect drops without actively watching the streams, thereby saving bandwidth. The application features a graphical user interface (GUI) built with Tkinter and supports various customization options, such as game prioritization and exclusion lists. It is packaged for both Windows (using PyInstaller) and Linux (using AppImage and PyInstaller).

The project is a fork of an existing Twitch Drops Miner, with added features like unrestricted drops mining and delayed claiming. It also contains a `TwitchMultiMiner` sub-directory which appears to be a newer, more modular version of the application with its own service-based architecture and test suite.

## Development Environment Setup

To set up the local development environment, run the `setup_env.bat` script. This will:
1.  Create a Python 3.10 virtual environment in the `./env` directory.
2.  Install all necessary dependencies from `requirements.txt`.

```bash
.\setup_env.bat
```

## Building and Running

### Running the Application
Once the environment is set up, you can run the application using the development script:
```bash
.\run_dev.bat
```
This script will ask whether to run the application with a visible console window.

### Running Tests
The `TwitchMultiMiner` sub-project has a dedicated test suite. To run all tests, execute the following command from the project root:
```bash
.\env\Scripts\python.exe .\TwitchMultiMiner\tests\run_tests.py
```

### Building the Application
To build the Windows executable, use the `build.bat` script. This will use PyInstaller and the `build.spec` file to create a distributable `.exe` file.
```bash
.\build.bat
```

## Development Conventions

*   **Linting**: The project uses `flake8` for linting, configured by the `.flake8` file in the `TwitchMultiMiner` directory. The `tests` and `twitch_miner_source` directories are excluded from linting.
*   **CI/CD**: GitHub Actions are used for continuous integration and deployment. The workflow in `.github/workflows/ci.yml` handles building, testing, and creating releases for Windows and Linux.
*   **Code Structure**: The project is structured into a main application and a `TwitchMultiMiner` sub-project. The latter seems to follow a more modern, service-oriented architecture with its own tests and configuration.
*   **Localization**: The `lang` directory contains JSON files for multiple languages.
*   **Version Control**: The `tatus` file appears to be a shorthand log for checking recent git history.