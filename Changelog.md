OpenCore Changelog
==================

#### v0.5.8
- Fixed invalid CPU object reference in SSDT-PLUG
- Fixed incorrect utilities and resources packaging
- Fixed `Custom` `UpdateSMBIOSMode` modifying SMBIOSv3 table
- Updated docs to cover separating SMBIOS via `UpdateSMBIOSMode`
- Fixed rendering macOS installer icons in OpenCanopy
- Added APFS support with Fusion Drive and enhanced security
- Added AppleEvent mouse support in OpenCanopy
- Fixed AppleEvent and OpenCanopy compatibility with OVMF TPL restrictions
- Added mouse drivers to the package as OVMF needs one
- Added memory region reservation support
- Added RtcRw tool to manipulate RTC memory
- Added `PatchAppleRtcChecksum` kernel quirk
- Added `AppleRtcRam` protocol implementation
- Renamed `Protocols` to `ProtocolOverrides` for clarity
- Added ResetSystem tool to allow shutdown/reset actions in the menu
- Added experimental `BootProtect` `Security` option
- Fixed kext injection in 10.8 installer
- Added timeout support to OpenCanopy user interface

#### v0.5.7
- Added TimeMachine detection to picker
- Added early preview version of OpenCanopy
- Fixed FS discovery on NVMe with legacy drivers
- Added `DirectGopCacheMode` option for FB cache policy
- Added `KeyFiltering` option to workaround buggy KB drivers
- Added tool and custom entry separation in audio assistant
- Added `OpenControl` tool to configure full NVRAM access from Shell
- Added `boot.efi` debug protocol support for 10.15.4+
- Added `boot.efi` performance logging for 10.15.4+
- Added `ProtectUefiServices` quirk to fix `DevirtualiseMmio` on Z390
- Replaced `BOOTCAMP Windows` with `Windows` to match the original
- Added bundled `OpenShell` originally available as OpenCoreShell
- Rework `readlabel` utility into `disklabel` with encoding support
- Renamed `FwRuntimeServices` driver to `OpenRuntime`
- Renamed `AppleUsbKbDxe` driver to `OpenUsbKbDxe`
- Update builtin firmware
- Fixed `PowerTimeoutKernelPanic` on 10.15.4
- Fixed 4K section alignment in `OpenRuntime` to fix Linux booting on SKL
- Introduced `SyncRuntimePermissions` to fix multiple memory permission flaws
- Introduced `RebuildAppleMemoryMap` to fix macOS booting on Dell 5490
- Removed `ShrinkMemoryMap` in favour of more advanced `RebuildAppleMemoryMap`
- Marked `EnableWriteUnprotector` as deprecated on modern systems
- Introduced `ProtectMemoryRegions` to fix memory region handling
- Removed `ProtectCsmRegion` in favour of `ProtectMemoryRegions`
- Renamed `PickerAttributes` to `ConsoleAttributes`
- Introduced `PickerAttributes` as a matter of UI configuration

#### v0.5.6
- Various improvements to builtin text renderer
- Fixed locating DMG recovery in APTIO IV firmwares on FAT32
- Fixed loading DMG recovery in APTIO IV firmwares on FAT32
- Removed `AvoidHighAlloc` quirk due to removed I/O over 4GB
- Moved `ConsoleMode`, `Resolution` options to `Output` section
- Moved console-related UEFI quirks to `Output` section
- Replaced `ConsoleControl` and `BuiltinTextRenderer` with `TextRenderer`
- Removed `ConsoleBehaviourOs` and `ConsoleBehaviourUi`
- Fixed providing ConsoleOutHandle GOP when running from Shell
- Added `PickerAttributes` option to colour picker
- Added `ProtectSecureBoot` option through FwRuntimeServices
- Replaced `RequireVault` and `RequireSignature` with `Vault`
- Added `BootKicker` tool to support launching Apple BootPicker
- Added BootPicker support as an external UI in OC through `PickerMode`
- Added `DirectGopRendering` option to use direct GOP output
- Multiple memory corruption and performance fixes for PNG support
- Fixed `DefaultBackgroundColor` variable handling
- Added `HideAuxiliary` and `Auxiliary` options
- Fixed picker timeout and log timestamps for VMware
- Fixed NULL parent DeviceHandle for launched tools
- Added bundled HiiDatabase driver for very old firmwares
- Added SSE2 support in memory intrinsics for better performance
- Improved ACPI PM timer CPU frequency calculation performance
- Improved LapicKernelPanic compatibility with newer macOS versions
- Fixed drivers starting with `#` not being skipped
- Added audio support through AudioDxe with optional boot chime
- Added VoiceOver accessability support in boot.efi for 10.13+
- Added `PickerAudioAssist` option for audio assistance in picker
- Added `HdaCodecDump.efi` tool in default package
- Added legacy AudioDxe and Microsoft namespaces to Reset NVRAM
- Merged `OcSupportPkg` with `OpenCorePkg` for easier bisection
- Disabled warnings in release versions of NVMe and XHCI drivers

#### v0.5.5
- Fixed CPU bus ratio calculation for Nehalem and Westmere
- Fixed CPU package calculation on MacPro5,1 and similar
- Improved OpenCore rerun detection for new versions
- Fixed loading picker on boot failure when it is hidden
- Added PMC ACPI sample for 300-series chipsets
- Improved driver connection performance on APTIO IV
- Fixed boot option saving in LogoutHook.command
- Added support for OEM information in `ExposeSensitiveData`
- Improved `SanitiseClearScreen` to avoid mode switching
- Replaced `SupportsCsm` with `AdviseWindows` enabling UEFI mode
- Fixed issues with default boot path selection on some boards
- Update builtin firmware versions
- Fixed `AdviseWindows` not setting `FirmwareFeatures` in NVRAM
- Added `TakeoffDelay` option for improved action hotkey support
- Added Mac GOP support to `ProvideConsoleGop` quirk
- Added experimental `BuiltinTextRenderer` boot option
- Added `DummyPowerManagement` kernel quirk to disable CPU PM

#### v0.5.4
- Added Enter key handling in boot menu for quick proceed
- Update builtin firmware versions
- Bundled FwRuntimeServices driver with OpenCore
- Allowed writing to non-volatile variables with disabled write
- Fixed microcode reading on Intel CPUs
- Fixed SMBIOS Type4 External Clock values
- Improved Windows compatibility on some setups (acidanthera/bugtracker#614)
- Added `SupportsCsm` and option in `PlatformInfo/Generic`
- Added `OSInfo` protocol support
- Added `SignalAppleOS` `Booter` quirk to enable IGPU on Macs in other OS
- Added `AppleSmcIo`protocol support (replaces `VirtualSmc` UEFI driver)
- Added `AuthRestart` security property for VirtualSMC authenticated restart
- Fixed input protocol initialisation on VMware fusion
- Added arrow key handling in boot menu
- FileVault 2-like key input is now the only supported input in boot menu
- Fixed 5 second delay when exiting Shell to OpenCore Picker
- Added default boot option update and `AllowSetDefault` `Security` option
- Fixed CPU package detection on configurations with multiple CPUs
- Bundled CleanNvram and VerifyMsrE2 tools for debugging
- Added screen clearing after choosing boot entry in picker
- Added `WriteFlash` NVRAM option to enable writing variables in `Add`
- Added `LegacyOverwrite` NVRAM option to allow overwriting variables by nvram.plist
- Added `AppleXcpmForceBoost` kernel quirk to maximise select Xeon performance
- Bundled NvmExpressDxe and XhciDxe drivers for platforms that need them
- Added `IncreasePciBarSize` kernel quirk for select platforms with PCI space issues

#### v0.5.3
- Update builtin firmware versions
- Fixed interpreting letters in boot menu
- Fixed timeout abortion with PollAppleHotKeys quirk
- Fixed rare kext injection failure due to plist-only kext in prelinkedkernel
- Fixed error reporting for dmg loading
- Added various debugging improvements
- Added new crypto stack resulting in vault key format changes
- Added `UnblockFsConnect` UEFI quirk to fix missing filesystems on some laptops
- Added `RequestBootVarFallback` UEFI quirk to circumvent firmware boot option issues
- Added `ThirdPartyDrives` kernel quirk fixing SSD trim and 10.15 SATA hibernation (thx @lvs1974)
- Removed `ThirdPartyTrim` kernel quirk in favour of `ThirdPartyDrives`
- Added Intel Xeon E5 (Broadwell-EP) support (thx @crazyi)
- Switched to edk2-stable201911, which is now the minimum supportd EDK II version

#### v0.5.2
- Fixed `MinKernel` and `MaxKernel` logic (thx @dhinakg, @reitermarkus)
- Fixed ASSERT when booting non-Apple OSes without arguments from the DEBUG version
- Added `MmioWhitelist` configuration option
- Added `PowerTimeoutKernelPanic` kernel quirk
- Fixed erratic cursor appearing in release builds
- Moved `ReconnectOnResChange` to a user-configurable quirk to avoid freezes
- Added OpenCore version to picker ui, configured by `ExposeSensitiveData`
- Added hypervisor CPUID support to work with virtualization (thx @Leoyzen)

#### v0.5.1
- Added support of kernel resource kext injection
- Added support for 0.25% clock slowdown on Xeon Scalable CPUs (thx @mrmiller)
- Replaced `MatchKernel` with `MinKernel` and `MaxKernel`
- Added `Arguments` to `Tools` and `Entries` sections
- Fixed broken timer for 300 series Intel chipsets
- Added `Input` section for mouse and keyboard aggregation

#### v0.5.0
- Added builtin firmware versions for new models 2019
- Fixed LogoutHook leaving random directories in `$HOME`
- Fixed FSBFrequency calculation on Xeon Scalable CPUs (thx @mrmiller)
- Fixed ARTFrequency specifying on Intel server and atom models
- Increased log size to 256 KB by default
- Added `ReplaceTabWithSpace` quirk to improve Shell experience
- Added `ClearScreenOnModeSwitch` quirk to avoid visual glitches
- Added `MISC_PWR_MGMT` patch to `AppleXcpmExtraMsrs` quirk (thx @mrmiller)
- Added `DevirtualiseMmio` quirk to `Booter` section
- Added FileVault 2 user interface protocols formerly in AppleUiSupport
- Improved kernel patch logging to include configuration comments
- Added MSFT basic data and Linux root fs recognition to `ScanPolicy`
- Fixed RT region protection restoration regression (thx Sniki)
- Added `OPT`, `CMD+R`, `CMD+OPT+P+R` boot action hotkey support
- Added `PollAppleHotKeys` to register boot.efi hotkeys in the picker
- Added `DisableSingleUser` quirk to prohibit single user mode
- Upgraded EDK II base package to edk2-stable201908
- Prohibited argument changing by BootNext

#### v0.0.4
- Fixed kext injection issues with dummy dependencies
- Fixed kext injection issues with reused vtables
- Fixed Custom SMBIOS table update patches
- Added timestamp to the log file and changed extension to txt
- Enhanced `LogoutHook` script used for emulated NVRAM saving
- Fixed multiple operating system support in APFS containers
- Added `AvoidHighAlloc` UEFI quirk to avoid high memory allocs
- Updated builtin firmware versions for 10.15 beta support
- Added `Booter` section for Apple bootloader preferences
- Dropped `AptioMemoryFix.efi` support for `Booter` and `FwRuntimeServices.efi`
- Fixed hibernation issues in Windows with `RequestBootVarRouting`
- Significantly improved boot stability on APTIO
- Added support for Windows & OpenCore on the same drive through `BlessOverride`
- Added advanced user-specified boot entries through `Misc` -> `Entries`
- Added `DisableVariableWrite` quirk to disable hardware NVRAM write in macOS

#### v0.0.3
- Added complete modern platform database (2012+)
- Added `DisableIoMapper` kernel quirk
- Fixed ACPI modification failures with nested multiboot
- Dropped `IgnoreForWindows` quirk legacy
- Added basic AMD Zen CPU support
- Added `Misc` -> `Tools` section to add third-party tools
- Added `Kernel` -> `Emulate` section for CPUID patches
- Added `CustomSMBIOSGuid` quirk for Custom SMBIOS update mode
- Added `PanicNoKextDump` quirk to avoid kext dump in panics
- Switched to EDK II stable and reduced image size
- Added `LapicKernelPanic` kernel quirk
- Added `AppleXcpmExtraMsrs` quirk and improved XCPM patches
- Added `(external)` suffix for external drives in boot menu
- Added `UsePicker` option, do enable for OC boot management
- Added nvram.plist loading for legacy and incompatible platforms
- Improved instructions for legacy and Windows installation
- Added Windows Boot Camp switching support
- Added basic hibernation detection & support
- Added `ResetHwSig` ACPI quirk to workaround hibernation
- Removed `Custom` subfolder requirement from `ACPI` tables
- Fixed kext injection in 10.7.x and 10.8.x
- Added ESP partition type detection to ScanPolicy
- Added support for third-party user interfaces

#### v0.0.2
- Documentation improvements (see Differences.pdf)
- Platform information database updates
- Fixed misbehaving `Debug` -> `Target` enable bit
- Added `ResetLogoStatus` ACPI quirk
- Added `SpoofVendor` PlatformInfo feature
- Replaced `ExposeBootPath` with `ExposeSensitiveData`
- Added builtin implementation of Data Hub protocol
- Dropped `UpdateSMBIOSMode` `Auto` mode in favour of `Create`
- Fixed SMBIOS CPU detection for Xeon and Core models
- Moved `ConsoleControl` configuration to `Protocols`
- Added `Security` -> `ScanPolicy` preference
- Fixed invalid `board-rev` exposure in Data Hub
- Fixed SMBIOS Type 133 table exposure
- Added support for SMBIOS Type 134 table exposure

#### v0.0.1
- Initial developer preview release
