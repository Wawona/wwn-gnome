# wwn-gnome

Wawona's port of the **GNOME Shell** (Mutter) Wayland session + GTK apps to run
under Wawona on the Apple ecosystem and Android, App Store compliant.

> **Status: SKELETON.** flake + `registryFragment` skeleton + port plan only.
> Build stubs fail intentionally; full port is downstream.

## Delivery model

Mutter is a full compositor → runs **nested** (Wawona client) or via **NixOS VM
/ waypipe** for the complete GNOME desktop (heavy). Individual GTK4/libadwaita
apps run as direct Wawona clients with `GDK_BACKEND=wayland`. See Wawona
`docs/2026-toolkit-de-compat.md`.

## Port plan

1. Toolchain via `wwn-toolchain`; GTK4/Mutter cross-built or via VM.
2. Compliance: no JIT (JS engine in gnome-shell), no unvetted extension loading,
   sandbox-safe dirs; prefer per-app GTK clients over full Shell on-device.
3. Fractional-scale + decoration semantics verified against Wawona.
4. Replace `dependencies/gnome/stub.nix` per platform; expose `gnome-*`; register.
5. Add `gnome` to the port plan / registryFragment as `status: planned`, then `approved`.

Convention: [wwn-* porting convention](https://github.com/Wawona/Wawona/blob/main/docs/2026-wwn-porting-convention.md).
