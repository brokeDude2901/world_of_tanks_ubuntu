## Running World of Tanks on Ubuntu

[![Watch](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DzaFduGi5rWU)](https://www.youtube.com/watch?v=zaFduGi5rWU)

# Preparation:
- Make sure GPU drivers are installed correctly (ie: NVIDIA GPU, AMD GPU, ..)
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/aecbee61-3b9b-43b4-9844-889edf89be64)

- If using NVIDIA GPU, connect your display to your Intel HD iGPU to enjoy Wayland
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/533c9753-1128-4740-978b-31896defa2dc)

- If using AMD GPU, just switch to Ubuntu on Wayland at login screen
 
- Set Power Mode to Performance (or use gamemoderun)
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/c5d5e9d2-e151-4dcf-9606-5a124f924677)
- Install Steam via .deb package (DO NOT USE CONFINED SNAP VERSION OF STEAM)
```
https://store.steampowered.com/about/
```
- Install Gamescope to allow WoT Client to run properly in background
```bash
sudo apt install gamescope
```

# Steam version of World of Tanks:
- Enable Proton Play and select Proton Experimental for all other titles
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/40007dc4-0c34-49b9-b1ef-6d97507f8d0b)
- Install the game from Steam or add your old SteamLibrary that contains World of Tanks (SteamLibrary must be in EXT4, not NTFS)
- Add gamescope stuff in World of Tanks Launch Options
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/970ad920-f61e-41f4-a0cc-d7ff684ce915)

Example:
Your display is 1080p 72hz, and dGPU is used for rendering
```
gamescope -h 1080 -r 72 -f --prefer-vk-device 10de:1e82 --immediate-flips %command%
```
Your display is 4k 144hz, directly connected to your dGPU
```
gamescope -h 2160 -r 144 -f --immediate-flips %command%
```
- Run the Game and disable Browser Hardware Acceleration
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/6bfa4825-60e1-47ae-a53c-f30a861229e9)


# Wargaming Center version of World of Tanks:
- Instead of installing World of Tanks directly from Steam Library, download world_of_tanks_install.exe from Wargaming website, add it as Non-Steam game with Proton Experimental
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/2c9631eb-711b-4674-8a62-68885d46b57d)
- Install or locate the game as you normally would
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/d4d6ac32-50f8-4ac9-9da9-5fce9b2281ff)
- Add gamescope stuff in this non-steam game Launch Options

Example: 
Your display is 1080p 72hz, and dGPU is used for rendering
```
gamescope -h 1080 -r 72 -f --prefer-vk-device 10de:1e82 --immediate-flips %command%
```
Your display is 4k 144hz, directly connected to your dGPU
```
gamescope -h 2160 -r 144 -f --immediate-flips %command%
```
- Run the Game and disable Browser Hardware Acceleration
![image](https://github.com/brokeDude2901/world_of_tanks_ubuntu/assets/46110534/f06b2477-15f5-48c5-980d-bb0620b1b17c)

# Optional: MangoHud and GOverlay
- Install GOverlay from the official Ubuntu Repo
```bash
sudo apt install goverlay
```
- If using NVIDIA GPU, you need to compile MangoHud to get GPU stats working (NVML), see https://github.com/flightlessmango/MangoHud#building-with-build-script
- Run GOverlay to config MangoHud options 


# Known Bugs / Workarounds:
- Store cannot load: Disable in-game Browser Hardware Acceleration
- Store still cannot load: use a VPN (Cloudflared Zero Trust or Mudfish)
- Game doesn't start: Steam fails to stop the game properly last time, open System Monitor and kill wgc.exe, wgc_api.exe, WargamingError... processes
- Laggy, low fps at the beginning of battle: use Gamescope to allow WoT Client to run in the background and load the map faster
