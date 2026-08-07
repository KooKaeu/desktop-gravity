# Desktop Gravity

Desktop Gravity makes explicitly selected Windows windows fall and also offers a desktop-icon mode where real icons collide, bounce, and pile up along the bottom.

> **Safety:** Select windows without important unsaved work. Press `Ctrl + Shift + G` or click **Stop and restore** at any time.

Requires Windows 10 22H2/Windows 11 x64 and the .NET 8 Desktop Runtime. Build with `dotnet build DesktopGravity.sln -c Release`, test with `dotnet test DesktopGravity.sln -c Release`, and run `dotnet run --project src/DesktopGravity.App/DesktopGravity.App.csproj`.

Refresh the list, explicitly select windows, then start gravity. The app runs locally without elevation, networking, telemetry, registry changes, or title history. Settings are stored under `%LOCALAPPDATA%\DesktopGravity`.

Before using icon gravity, disable **Auto arrange icons** in the desktop View menu. Icon physics currently targets the primary monitor only. Known limitations include elevated/system windows, applications that resist repositioning, and behavior that depends on DPI or monitor topology. Window-to-window collision remains excluded.

See [architecture](docs/architecture.md), [safety](docs/safety.md), and the [MIT License](LICENSE).
