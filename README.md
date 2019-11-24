# GPU Proof of Spacemesh Time Init (aka Smeshing Setup) Prototype

## Current functionality
- A c libraray implementing the POST API setup method for cpu, cuda and openCL compute platforms.

## System Requirements
- Windows 10 Pro.
- Microsoft Visual Studio 2017 (any edition should be okay. Visual Studio 2019 is not supported. You may also need to install specific versions of the Windows SDK when prompted when attempting to build for the first time.
- NVIDIA GPU Computing Toolkit 10.0 (but not later versions), and an NVIDIA GPU supporting CUDA 10.0 computation for CUDA testing.
- An AMD GPU supporting OpenCL 2.0 or newer for OpenCL testing.

## Biulding
1. Load solution spacemesh.sln info Visual Studio 2017.
2. Set "test" as startup project. In the Solution Explorer right click on "test", select "Set as StartUp Project".
3. Set "Release" configuration and "x64" platform.
4. Build: Build menu -> Rebuild Solution.
5. Run test: Debug menu -> Start Without Debugging.

## Initial Benchmarks

|Date      |Reporter|impl     |cpu / gpu                       |notes                                 |kh/s |mh/s|x factor over 1 4ghz cpu native thread|x factor over 12 4ghz cpu native threads|
|----------|--------|---------|--------------------------------|--------------------------------------|-----|----|--------------------------------------|----------------------------------------|
|11/19/2019|ae      |go-scrypt|mbp + Intel i9 @ 2.9ghz - 1 core|go scrypt crypto lib (not scrypt-jane)|7    |0.01|1                                     |1                                       |
|11/19/2019|ae      |sm-scrypt|Ryzen 5 2600x @ 4ghz - 1 core   |scrypt-jane c code                    |7    |0.01|1                                     |1                                       |
|11/19/2019|ae      |sm-scrypt|Nvidia Gefroce RTX 2070 8GB     |pre-optimized prototype               |1,920|1.92|290                                   |24.17                                   |
|11/19/2019|ae      |sm-scrypt|AMD Radeon RX 580               |pre-optimized prototype               |500  |0.50|76                                    |6.29                                    |
|11/19/2019|ar      |sm-scrypt|Nvidia GTX 1060 6G              |pre-optimized prototype               |979  |0.98|148                                   |12.32                                   |
|11/19/2019|ar      |sm-scrypt|AMD Radeon 570 4GB              |pre-optimized prototype               |355  |0.36|54                                    |4.47                                    |

