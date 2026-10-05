# SukiSU Ultra kernel for OnePlus Nord CE 2 Lite 5G (sm6375)

Builds a rooted (SukiSU Ultra) kernel from
`LineageOS/android_kernel_oneplus_sm6375` (`lineage-23.2`, Linux 5.4.302, non-GKI)
and packs an **AnyKernel3** flashable zip.

## Run it
Actions -> "Build SukiSU kernel" -> Run workflow.

Artifacts: `AnyKernel3_SukiSU_sm6375.zip` (flash this), raw `Image*`, `build.log`.

## What it does
1. Clones the LineageOS sm6375 kernel.
2. Injects SukiSU Ultra (`builtin` branch, the non-GKI one) into `drivers/kernelsu`.
3. Applies `patches/0001-ksu-manual-hook.patch` (manual hooks for execve/faccessat/stat/read/input/devpts).
4. Enables `CONFIG_KSU` and builds with proton-clang using `vendor/holi-qgki_defconfig`.

## Flash
Flash the AnyKernel3 zip in a custom recovery / kernel flasher. It replaces the
kernel in the `boot` partition. Back up your stock boot image first.

## SUSFS
The `susfs` input is reserved; the SUSFS layer (core patch + inline hooks) is a
separate, version-coupled step and is not yet wired into this workflow.
