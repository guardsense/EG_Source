# System Manual

## Minimum Requirements 
The following requirements must be met in order to fully develop all aspects of the application.

### CPU
Intel 12th or 13th-gen i5 processor or above, with at least 4 E-cores and 2 P-cores.

### Operating System
Windows 11, version 22H2 or above

### IDE
[Visual Studio 2022](https://visualstudio.microsoft.com/vs/), version 17.5.2 or above

## Visual Studio 2022 Setup
### Select Visual Studio 2022 Workloads
Open Visual Studio 2022, and open Tools &rarr; Get Tools and Features.
Install the following **Workloads** presented in the Workloads tab:
1. .NET Desktop Development
  - From the list of optional components, also select:
    - Windows App SDK C# Templates
    - MSIX Packaging Tools

2. Desktop Development with C++
    - From the list of optional components, also select:
        - C++/CLI support for v143 build tools (Latest)
        - Windows App SDK C++ Templates
    - Check that the following optional component(s) for the **workload** will be installed:
        - MSVC v143 - VS 2022 C++ x64/x86 build tools
        - Windows 11 SDK (10.0.22621.0)
        - Windows 10 SDK (10.0.19041.0)

3. Universal Windows Platform Development
    - Check that the following optional component(s) for the **workload** will be installed:
        - C++ (v143) Universal Windows Platform tools
        - Windows 11 SDK (10.0.22621.0)
        - Windows 10 SDK (10.0.19041.0)

*NB: When selecting a workload, ensure not to unselect any components in the optional tab that are selected by default.*

### Select Individual Components for Installation
From the same Tools and Features window, switch tabs from **Workloads** to **Individual Components**.

Select Individual Components:
1. Windows Universal C Runtime
2. Windows 10 SDK (10.0.19041.0)

### Install
Select the **Modify** (or Install) button in the bottom right corner of the Tools and Features window to install all the selected components and workloads.

## Setting up NuGet Package Manager
From the toolbar, Open Tools &rarr; Nuget Package Manager &rarr; Package Manager Settings.
1. Click **Clear All NuGet Storage** in the General tab.
2. Click on **Package Sources** under the NuGet Package Manager tab on the Options window.
3. Ensure the **nuget.org** package source is set up correctly, with the Source set to the following (URL)[https://api.nuget.org/v3/index.json].
If any changes were made, make sure to click the **Update** button to save changes,
4. Add a new package source:
    - Set the name to **Microsoft Labs Community Toolkit**
    - Set the Source to the following (URL)[https://pkgs.dev.azure.com/dotnet/CommunityToolkit/_packaging/CommunityToolkit-Labs/nuget/v3/index.json]
    - Click **Update** to save changes.
5. Click **Ok** on the Options window and close

## Running the App
1. Clone the project from the following GitHub [link](https://github.com/guardsense).
2. Open **Core.sln** inside the Core folder from the root directory. 
3. Visual Studio will automatically detect the Energy Performance startup project
4. Either click one of the two *Run* buttons at the top bar of Visual Studio, next to *Energy Performance (Package)* **OR** on the toolbar, under Debug, press either *Start Debugging* or *Start Without Debugging*.
5. Building the project for the first time may take a while, as Visual Studio will download and install all NuGet packages required for the application. On future runs, deployment will be much faster.
6. After the project is built, the app will start. To exit the app, either press the *Stop* button in Visual Studio (if started with debugging) or right click on the new icon in the taskbar tray for EnergyGuard, and press **Exit**.

## Deploying the App for Publishing
1. Open the *Solution Explorer* window in Visual Studio.
2. Right click on the **Energy Performance** project and select Package and Publish &rarr; Create App Package.
3. To distribute the app to the Microsoft Store, select *Microsoft Store under a new app name* and follow the instructions displayed.
4. For standard distribution to all other sources, select *Sideloading* and click next:
    1. Select *Yes, select a certificate* and either:
        - Select a package signing certificate from a trusted source if you already have one available.
        - Select *Create* to create a new **self-signed test certificate** for testing deployment. Enter a publisher name and password and click 'OK'. Select **Trust** on the newly created certificate to trust this certificate on your system.
    2. Click Next &rarr; Next &rarr; Create, using the default installation settings already selected.
    3. Once Visual Studio has finished creating the package, a new window will open showing the *Output location* of the newly created package. Open this folder and navigate to the new EnergyPerformance directory with the latest version name.
    4. Open the .msix file in this file and click **Install** to install the distributed version of the app on your device.
    5. You can now find the app installed on your system through the Start Menu.
