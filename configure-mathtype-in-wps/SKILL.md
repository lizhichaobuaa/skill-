---
name: configure-mathtype-in-wps
description: Install a licensed MathType 7.4 build and configure or troubleshoot MathType integration in WPS Office on Windows. Includes a signed MathType installer, a user-provided WPS VBA installer, MathPage.wll and MathType Commands .dotm deployment, manual WPS add-in activation, startup-directory checks, macro support, permissions, and 32-bit or 64-bit compatibility. Use when a user asks to install MathType, add MathType to WPS, install WPS VBA for MathType, restore a missing MathType tab, follow the Zhihu manual setup method, or diagnose WPS MathType loading failures.
---

# Install and Configure MathType in WPS

## Licensing and Safety

- Install MathType only with a valid license or an authorized trial.
- Never bundle, execute, recommend, or explain cracks, key generators, license patches, or activation bypasses.
- Never ask the user to disable antivirus, real-time protection, or Windows security to run an installer.
- Do not use tutorials that mix normal installation instructions with cracking steps. Use `references/mathtype-installation.md` instead.

## Preconditions

1. Determine whether MathType is already installed.
2. If MathType is missing, install it before configuring WPS integration.
3. Close all WPS, Word, Excel, and PowerPoint processes before installing MathType, installing VBA support, or copying add-in files.
4. Use the actual MathType and WPS installation directories instead of assuming tutorial example paths.
5. Obtain explicit confirmation immediately before running any bundled executable.

## Install MathType

The skill includes a signed MathType installer:

```text
assets/MathType-win-zh.exe
```

Recorded file details:

```text
Size: 43193768 bytes
SHA256: B2CA56839F56636F93C958C61B0288CA65C0851105E0C523D5DB770EF15109FC
Authenticode: Valid
Signer: Design Science Inc.
```

Use it only for a licensed installation:

1. Verify the bundled file exists.
2. Confirm its SHA256 hash and Authenticode signature before launch.
3. Explain that the executable is bundled from a user-provided local source and is signed by Design Science Inc.
4. Obtain explicit confirmation before launching it.
5. Close WPS and Microsoft Office applications.
6. Run the standard installer and retain the default installation path unless the user needs another location.
7. Do not run any crack or activation patch after installation.
8. Open MathType once and confirm it starts normally.
9. Continue with WPS integration only after MathType is installed.

Read `references/mathtype-installation.md` when performing the full installation workflow.

## Establish the Environment

Determine these details when they affect the procedure:

- WPS Office version and installation directory.
- Whether WPS is 32-bit or 64-bit.
- MathType version and installation directory.
- Whether WPS VBA or macro support is already installed.
- Whether the user can write to the WPS installation directory.

If the user requests a general procedure, use placeholders such as `<MATHTYPE_DIR>`, `<WPS_DIR>`, and `<USERNAME>`.

## Install WPS VBA Support

The skill includes the user-provided installer:

```text
assets/wps.vba.exe
```

Recorded file details:

```text
Size: 8767888 bytes
SHA256: 51FD8E8D84FAC2B192BECFF116170299FFEAE2C1887421841E6F90C7192E63CB
```

Use the installer only when WPS VBA or macro support is missing:

1. Verify the bundled file exists and confirm its SHA256 hash.
2. Explain that it is a user-provided executable and is not digitally signed.
3. Obtain explicit confirmation immediately before launching it.
4. Close WPS before launching it.
5. Run it with administrator privileges only if installation permissions require them.
6. Do not bypass Windows security warnings or antivirus blocks.
7. Reopen WPS and select `Tools`.
8. Confirm that `Run Macro`, `Macro Security`, `Add-ins`, and `Developer Tools` are available.

Do not download a replacement VBA installer from an untrusted source.

## Apply the Manual MathType Method

1. Locate `MathPage.wll` under:

   ```text
   <MATHTYPE_DIR>\MathPage\32\
   ```

   The referenced 2022 tutorial explicitly uses the `32` directory. Verify WPS architecture before choosing `32` or `64`.

2. Copy `MathPage.wll` to:

   ```text
   <WPS_DIR>\office6\
   ```

3. Copy another `MathPage.wll` to:

   ```text
   %APPDATA%\kingsoft\wps\startup\
   ```

4. Locate the MathType command template. The referenced tutorial uses:

   ```text
   <MATHTYPE_DIR>\Office Support\64\MathType Commands 2016.dotm
   ```

5. Prefer the command template supplied by the installed MathType version. Do not download replacement `.wll` or `.dotm` files from untrusted sites.
6. Copy `MathType Commands 2016.dotm`, or the matching installed template, to:

   ```text
   %APPDATA%\kingsoft\wps\startup\
   ```

7. Fully close and reopen WPS.

## Manually Enable Detected Add-ins

Treat this as a required check when the files are present but the `MathType` tab is missing.

1. Open a normal `.docx` file in WPS Writer.
2. Select `Tools` and verify the macro controls are available.
3. Select `Tools` > `Add-ins`.
4. Inspect `Global templates and add-ins`.
5. If `mathpage.wll` is listed but unchecked, select it, click `Enable`, and confirm the WPS loading warning.
6. If `mathtype commands 2016.dotm` is listed but unchecked, select it, click `Enable`, and confirm the warning.
7. Verify that both entries are checked, then click `OK`.
8. Confirm that the `MathType` tab appears in the ribbon.
9. Open the `MathType` tab and verify that equation insertion, conversion, export, and help controls are visible.

Important findings from WPS 12.1 with MathType 7.4:

- WPS can detect both startup files without loading them.
- Recopying the files does not solve this state; both entries must be enabled in `Tools` > `Add-ins`.
- Modern WPS exposes VBA controls under `Tools`; a separate visible `Developer` ribbon tab is not required.
- The `MathType` tab can appear immediately after both entries are enabled, without restarting WPS.

## Handle Version Differences

- Treat the tutorial's `MathPage\32` plus `Office Support\64` combination as a historical example for MathType 7 and WPS 2021, not a universal bitness rule.
- Match the `.wll` architecture to WPS, not merely to 64-bit Windows.
- Preserve existing destination files. Compare version, size, modification date, or hash before replacing them.
- Request administrator permission only when writing to the WPS installation directory requires it.

## Troubleshoot in Order

When the MathType tab does not appear, check:

1. MathType was installed successfully and starts normally.
2. WPS VBA support is active: `Tools` shows `Run Macro`, `Macro Security`, `Add-ins`, and `Developer Tools`.
3. `MathPage.wll` exists in both `<WPS_DIR>\office6\` and `%APPDATA%\kingsoft\wps\startup\`.
4. The MathType command `.dotm` file exists in `%APPDATA%\kingsoft\wps\startup\`.
5. WPS was fully closed and reopened after file copying.
6. In `Tools` > `Add-ins`, both MathType entries are checked. Enable them manually when they are detected but inactive.
7. WPS and the selected add-in files have compatible 32-bit or 64-bit architecture.
8. Windows has not marked the copied files as blocked.
9. Security software or WPS macro settings are not preventing startup templates from loading.

If WPS begins crashing, close WPS and remove only the newly copied files from the startup directory first, then retry with architecture-compatible files.

## Response Style

Provide:

- The precondition that MathType must be installed and licensed before WPS integration.
- Exact resolved paths when the user supplies installation details.
- A numbered install, copy, enable, restart, and verification checklist.
- A clear warning when instructions rely on the older MathType 7 and WPS 2021 tutorial.
- Focused troubleshooting based on the user's symptom.
- A clear refusal to run or bundle license-bypass tools.
