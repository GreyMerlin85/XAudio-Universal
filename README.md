# XAudio Universal

Audio wrapper for classic Windows games: DirectSound, DirectSound3D, EAX, A3D 1.x and OpenAL, with XAudio2 output.

**For 32-bit games on Windows 10 and 11.**

## Installation

1. Close the game and back up its original DLL files.
2. Copy **`xaudiouniv.dll` and `xaudiouniv.ini`** next to the game's executable.
3. For a standard DirectSound/EAX setup, also copy **`dsound.dll`, `dsound.ini`, `eax.dll` and `eax.ini`** from the pack into the same folder. Back up the original `eax.dll` before replacing it.
4. Add other files as needed for the game's audio API:

| Game audio | Files to add |
|---|---|
| DirectSound / DirectSound3D | `dsound.dll` and `dsound.ini` |
| EAX through `eax.dll` | `eax.dll` and `eax.ini` |
| A3D 1.0 / 1.2 | `a3d.dll` and `a3d.ini` |
| Games that also require `A3DAPI.dll` | `A3DAPI.dll` and `A3DAPI.ini` |
| OpenAL | `OpenAL32.dll` and `OpenAL32.ini` |
| waveOut / PlaySound | `winmm.dll` and `winmm.ini` |

If the game requires `wrap_oal.dll`, `ct_oal.dll` or `soft_oal.dll`, use the matching DLL and INI supplied in the pack.

5. Launch the game and enable **EAX**, **A3D** or **3D sound** in its audio settings, where available.

Use files from the same pack and install them only in the game folder.

## Settings

The supplied settings are enough to get started. Leave the `[Wrapper]` section unchanged.

### OpenAL and OpenALEFX

To use OpenAL and OpenALEFX instead of the original EAX path, change the corresponding **OpenAL** and **OpenALEFX** options from **`0` to `1`** in the supplied INI configuration. Set them back to `0` to disable them.

### Speaker channels

Choose the number of output channels in `xaudiouniv.ini`:

```ini
[XAudio2]
Channels=2
```

`2` = stereo/headphones · `4` = four speakers · `6` = 5.1 · `8` = 7.1.

For headphones, also select the game's headphone setting if available. The game may override the requested channel count.

Upmixing and additional bass processing are disabled by default.

**Restart the game after changing an INI file.**

## Compatibility and tested games

The wrapper covers the DirectSound, DirectSound3D, EAX and Aureal A3D audio families. EAX version coverage includes EAX 1–5, with partial EAX 5 support. A3D support currently covers versions 1.0 and 1.2.

The following games have been tested by the project author:

- Demolition Racer 1
- Max Payne 1 and 2
- Colin McRae Rally 04
- Diablo II — original version, patch 1.14d
- Die Hard Trilogy — Aureal A3D

These tests confirm compatibility with the tested games; they do not establish full support for every feature of every API version.

## Limitations

- A3D 1.0 / 1.2 only. `A3DAPI.dll` is an auxiliary stub; A3D 2/3 and acoustic geometry are not implemented.
- EAX 5 support is partial.
- The game must already offer EAX or A3D features to use them.
- Compatibility may vary between games.

## Uninstallation

Remove the added files and restore the original files from your backup.

## Components

Based on DSOAL, OpenAL Soft and eaxefx and indirectsound re-a3d-api idea.
