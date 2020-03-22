# Qt Visual Studio Code Tools

> This extension is work in progress, so some command/settings can change over time.

> <span style="color:red; font-weight:bold;">This is NOT an offical tool by The Qt Company!!</span>

This is a Qt extension for VSCode. It is designed to be an similar tool to the [Qt Visual Studio Tools](https://marketplace.visualstudio.com/items?itemName=TheQtCompany.QtVisualStudioTools-19123) from The Qt Company, but it try to cooperate with other extensions for some functionality like f.e. debugging.

At the moment the extension extracts the Qt file locations from CMake only (from [CMake Tools extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) setting `cmake.buildDirectory`), so choosing and different Qt version from disk is not supported at the moment (but if you use cmake already, everything is automatically detected :-) ).

## Features
* [x] Launch Qt Designer
* [x] Edit `.ui` file in Qt Designer
* [x] Launch Qt Assistant
* [x] Launch Qt Creator<br>
  `.ui` and `.qrc` files can be opened in Qt Creator. You can also open the whole workspace in Qt Creator too.<br>
  This extension try to detect the Qt Creator installation automatically (on Windows and MacOS). You can set the executable path via `qttools.creator` settings if the extension can't find Qt Creator (for whatever reason)
* [x] Extract the Qt file locations from the cmake cache (`CMakeCache.txt`). The cmake build directory is extracted from the vscode extension [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) setting `cmake.buildDirectory`. 
  So you need to configure your project for the first time and afterwards every Qt tool is found automatically (when it is installed on your disk ;-) ).
* [x] Debugger extensions (via natvis files)<br>
  The Qt natvis file from this extension will automatically get injected into your existing `launch.json` file (per default). If you don't like that feature you can turn it of via `qttools.injectNatvisFile` setting.<br>
  You can also set your custom created/downloaded qt natvis file instead of the bundled one (which implement a few Qt types) by setting `qttools.visualizerFile` to a filepath or url (f.e. you can set `qttools.visualizerFile` to the natvis file from the offical [Qt Visual Studio Tools](https://code.qt.io/cgit/qt-labs/vstools.git/tree/src/qtvstools/qt5.natvis.xml) `https://code.qt.io/cgit/qt-labs/vstools.git/plain/src/qtvstools/qt5.natvis.xml`). When you set an url, the extension will only download it ones and cache it and will use the cached local version<br>
  NOTE: I cannot bundle the Qt Visual Studio Tools natvis file into the extension itself because of it's license restrictions (MIT vs GPL)!
* [ ] qml language support (there are already some VSCode extensions)
* ...

## Requirements
* You need to have the [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) installed, because this extension extracts some data from it!
* [C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) is highly recommended

## Limitations
* There are some situation where the automatic detection mechanism of Qt is not working. If that is the case you can always trigger the `Scan for Qt kits` command in the command palette.
* The debugger extension use normal natvis xml files (used via the `launch.json` setting `visualizerFile` from the [C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) ). They work really well on windows, but on mac and linux there are some problems, because it is not based on the same implementation. If you have any problems with them create an issue on their issue tracker.

## Contributions
Pull requests are welcome :-D

## License
MIT
