# Development

### Sprint

- Base
    - implement base qml-gui project
    - create gui design draft
    - add keypad buttons
        - read button inputs
    - add logs area & dummy logs (added artifically)
    - success generate new logs as multithread
- Bluetooth
    - add winrt via vcpkg
    - implement simple ble
    - restructure codebase
    - implement ble funcs: scan, connect, notify, send, show rssi
        - test ble notify with dummy esp32
        - test ble send to dummy esp32
    - connect keypad input with ble send
    - connect notify with logs
    - add unit tests using pytest

---

### Project Structure

source: https://chat.deepseek.com/a/chat/s/b8bdbb47-ad21-4048-abbd-07476c56b902

```
wheel-balancer-app/
├── .vscode/                     # VSCode-specific configs
│   ├── launch.json
│   ├── tasks.json
│   └── settings.json
├── cmake/                       # CMake modules
│   └── FindQMLModules.cmake
├── src/
│   ├── main.cpp                 # Application entry point
│   ├── main.qml                 # Root QML file
│   ├── qml/                     # QML components
│   │   ├── components/          # Reusable UI components
│   │   │   ├── Button/
│   │   │   │   ├── PrimaryButton.qml
│   │   │   │   └── SecondaryButton.qml
│   │   │   ├── LogViewer.qml
│   │   │   └── RobotStatus.qml
│   │   ├── screens/             # Application screens/views
│   │   │   ├── Dashboard.qml
│   │   │   ├── LogsScreen.qml
│   │   │   └── ControlScreen.qml
│   │   ├── dialogs/             # Modal dialogs
│   │   │   ├── ConnectDialog.qml
│   │   │   └── SettingsDialog.qml
│   │   └── themes/              # Style/Theming
│   │       ├── Colors.qml
│   │       ├── Fonts.qml
│   │       └── Metrics.qml
│   ├── core/                    # C++ business logic
│   │   ├── CMakeLists.txt
│   │   ├── ble/
│   │   │   ├── BLEClient.h
│   │   │   ├── BLEClient.cpp
│   │   │   └── BLEManager.h
│   │   ├── robot/
│   │   │   ├── RobotController.h
│   │   │   ├── RobotController.cpp
│   │   │   └── commands/
│   │   ├── logging/
│   │   │   ├── LogManager.h
│   │   │   └── LogManager.cpp
│   │   └── models/              # QAbstractListModel derivatives
│   │       ├── LogModel.h
│   │       └── LogModel.cpp
│   └── utils/                   # Utilities
│       ├── Settings.h
│       ├── Validator.h
│       └── Formatters.h
├── resources/                   # Static resources
│   ├── images/
│   ├── fonts/
│   └── translations/            # i18n files
├── tests/                       # Unit/integration tests
│   ├── unit/
│   └── integration/
├── docs/                        # Documentation
│   ├── architecture.md
│   └── api/
├── thirdparty/                  # External dependencies
├── scripts/                     # Build/deployment scripts
├── CMakeLists.txt              # Root CMake
├── README.md
├── LICENSE
└── .gitignore
```