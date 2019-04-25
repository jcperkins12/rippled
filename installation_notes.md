# My notes for how I installed rippled on a windows machine
## curent environment

1. MSVS2017
2. protoc.exe version 2 saved to 'C:\lib\protoc.exe'
3. Win64 OpenSSL v1.0.2r installed at 'C:\lib\OPENSSL'
3. Boost_1_68_0 saved to 'C:\lib\boost'
4. the CMakeSettings.json file recommended by ripple and located at the root of this project

note: I was not able to get the code compiled with Boost_1_70_0

I used the integrated CMake and followed the instructions on the .\\Builds\\... instructions
# Build using Visual Studio integrated CMake

In Visual Studio 2017, Microsoft added [integrated IDE support for
cmake](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/cmake-support-in-visual-studio/).
To begin, simply:

1. Launch Visual Studio and choose **File | Open | Folder**, navigating to the
   cloned rippled folder.
2. Right-click on `CMakeLists.txt` in the **Solution Explorer - Folder View** to
   generate a `CMakeSettings.json` file. A sample settings file is provided
   [here](/Builds/VisualStudio2017/CMakeSettings-example.json). Customize the 
   settings for `BOOST_ROOT`, `OPENSSL_ROOT` to match the install paths if they
   differ from those in the file.
4. Select either the `x64-Release` or `x64-Debug` configuration from the
   **Project Setings** drop-down. This should invoke the built-in CMake project
   generator. If not, you can right-click on the `CMakeLists.txt` file and
   choose **Cache | Generate Cache**.
5. Select either the `rippled.exe` (unity) or `rippled_classic.exe` (non-unity)
   option in the **Select Startup Item** drop-down. This will be the target
   built when you press F7. Alternatively, you can choose a target to build from
   the top-level **CMake | Build** menu. Note that at this time, there are other
   targets listed that come from third party visual studio files embedded in the
   rippled repo, e.g. `datagen.vcxproj`. Please ignore them.

For details on configuring debugging sessions or further customization of CMake,
please refer to the [CMake tools for VS
documentation](https://docs.microsoft.com/en-us/cpp/ide/cmake-tools-for-visual-cpp).

If using the provided `CMakeSettings.json` file, the executable will be in
```
.\build\x64-Release\Release\rippled(_classic).exe
```
or
```
.\build\x64-Debug\Debug\rippled(_classic).exe
```
where these paths are relative to your cloned git repository.
