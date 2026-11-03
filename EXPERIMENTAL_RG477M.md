## Experimental Mali / Dimensity 8300 support (this fork)

This fork adds experimental detection for **Anbernic RG477M** (MediaTek Dimensity 8300 / Mali-G615 MC6).

- On matching devices the launcher uses the system Mali Vulkan driver via the wrapper (no Turnip).
- Default resolution is set to 1280×960 to match the device screen.
- **Status:** experimental. Mali Vulkan + DXVK support is still maturing; performance, stability and feature completeness are not guaranteed. Report issues with device model, Android version and logcat.

### What changed

In `WoWForeverScreen.kt`:
- `GpuProfile.detect` now checks for Dimensity 8300 / MT6897 / RG477M model strings.
- Mali path sets `useTurnip = false`, uses the `wrapper` graphics driver, omits `TU_DEBUG`, and sets `adrenotoolsTurnip=0`.
- Default screen size for Mali is `1280x960`.

This is a first-pass code change. Actual runtime success depends on the device's stock Mali Vulkan driver quality with DXVK. Further driver work (PanVK-kbase or similar) may be needed.
