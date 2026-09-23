# Enterprise Monitor Com1

Update Release for Tahmid IT Park Software

## Overview

Enterprise Monitor Com1 is a monitoring and release management project for Tahmid IT Park Software. This repository contains the code and resources used to build, deploy, and manage releases for enterprise monitoring components.

┌──────────────────────────────────────────────────────────────--───┐
│                     ELECTRON (Master Process)                     │
│                                                                   │
│  ┌──────────┐   ┌──────────────-┐   ┌──────────────────────────┐  │
│  │  Tray    │   │  BrowserWindow│   │  Preload (Context Bridge)│  │
│  │  Manager │   │  (Renderer)   │   │  • Secure IPC Bridge     │  │
│  └──────────┘   └──────┬──────-─┘   └──────────────────────────┘  │
│                        │ IPC Handlers                             │
│  ┌─────────────────────┴───────────────────────────────────────┐  │
│  │ Main Process: spawn → port.info handshake → ApiClient       │  │
│  └─────────────────────────────────────────────────────────────┘  │
│          │ HTTP (dynamic port)                                    │
└──────────┼───────────────────────────────────────────────────--───┘
           │
           ▼
┌────────────────────────────────────────────────────────────────--─┐
│              PYTHON BACKEND (Child Process)                       │
│          ┌─────────────┐  ┌─────────────────┐                     │
│          │   Windows   │  │     macOS        │                    │
│          │  (pywin32,  │  │  (AppleScript,   │                    │
│          │  UIAuto)    │  │  pyobjc, TCC)    │                    │
│          └─────────────┘  └─────────────────┘                     │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │  FastAPI + Uvicorn (dynamic port, 127.0.0.1 only)            │ │
│  │  • JWT Auth  • REST API  • CORS  • Lifecycle Hooks           │ │ 
│  │  • Graceful Shutdown Endpoint (/api/shutdown)                | │
│  └──────────────────────────────────────────────────────────────┘ │
│                                                                   │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────────────┐    │
│  │Screenshot│ │App       │ │Browser   │ │Keylogger           │    │
│  │Monitor   │ │Tracker   │ │Tracker   │ │(pynput)            │    │
│  └──────────┘ └──────────┘ └──────────┘ └────────────────────┘    │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────────────┐    │
│  │Clipboard │ │Screen    │ │Sync      │ │Data Cleanup Service│    │
│  │Monitor   │ │Recorder  │ │Service   │ │(7-day database)    │    │
│  │          │ │(OpenCV)  │ │(v2 - 6)  │ └────────────────────┘    │
│  └──────────┘ └──────────┘ └──────────┘                           │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │  SQLite (WAL mode, shared connection, thread-safe Lock)      │ │
│  │  • screenshots • app_activity • browser_activity             │ │
│  │  • clipboard_events • text_logs • video_recordings           │ │
│  │  • device_config                                             │ │
│  └──────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────--┘

## Features

- Release automation and packaging
- Monitoring configuration and dashboards
- Deployment scripts and utilities

## Getting Started

These instructions will help you set up the project locally for development and testing purposes.

### Prerequisites

- Git
- Node.js (if parts of the project use JavaScript/Node)
- Python 3.x (if parts of the project use Python)
- Docker (optional, for containerized components)

### Installation

1. Clone the repository:

   git clone https://github.com/Ashraful-Anik-890/Enterprise-Monitor-Com1.git
   cd Enterprise-Monitor-Com1

2. Inspect project folders and README files in subdirectories to find component-specific setup steps.

3. Install dependencies where applicable. Example (Node.js):

   npm install


## Usage

- Check the `scripts/` or `deploy/` directory for deployment and release scripts.
- Use the included configuration files in `config/` to customize monitoring targets and thresholds.

## Contributing

Contributions are welcome. Please open an issue to discuss major changes before creating a pull request. When contributing:

1. Fork the repository
2. Create a new branch for your feature or bug fix
3. Commit your changes with clear messages
4. Open a Pull Request describing your changes

## License

This repository does not include a license file. Add a LICENSE file to specify the project license.

## Contact

For questions about releases or the Tahmid IT Park Software updates, contact the repository owner.
