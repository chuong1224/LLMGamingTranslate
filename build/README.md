# Build Scripts

This directory contains all build-related files for creating standalone executables.

## Structure

```
build/
├── windows/               # Windows build files
│   ├── TranslateBook.spec    # PyInstaller spec for Windows
│   ├── build_exe.bat         # Windows build script
│   └── install_chatterbox.bat # Chatterbox TTS installer
└── README.md              # This file
```

## Building Executables

### Windows

```bash
cd build/windows
build_exe.bat
```

The executable will be created at: `../../dist/TranslateBook.exe`

## GitHub Workflows

The GitHub Actions workflow automatically uses these files:
- [.github/workflows/build-windows.yml](../../.github/workflows/build-windows.yml)

## Output

All builds output to the root `dist/` directory, which is git-ignored.
