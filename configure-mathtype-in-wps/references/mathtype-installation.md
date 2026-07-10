# Licensed MathType Installation and WPS Integration

Use this reference for a clean MathType installation. It intentionally excludes cracking, key generation, license patching, antivirus disabling, and activation bypass instructions.

## Bundled Installer

```text
assets/MathType-win-zh.exe
```

- Size: 43193768 bytes
- SHA256: `B2CA56839F56636F93C958C61B0288CA65C0851105E0C523D5DB770EF15109FC`
- Authenticode status: Valid
- Signer: Design Science Inc.

## Install MathType

1. Verify the installer hash and Authenticode signature.
2. Confirm that the user has a valid MathType license or intends to use an authorized trial.
3. Obtain explicit approval before launching the installer.
4. Close WPS Writer and all Microsoft Office applications.
5. Run `MathType-win-zh.exe`.
6. Follow the standard installation wizard.
7. Keep the default installation directory unless another path is required.
8. Open MathType after installation and confirm that the editor starts.
9. Do not execute any crack, patch, key generator, or unsigned activation utility.

## Configure WPS

1. Confirm WPS architecture.
2. Install WPS VBA support if `Tools` does not show macro controls.
3. Copy the architecture-compatible `MathPage.wll` to the WPS `office6` directory.
4. Copy `MathPage.wll` and the installed MathType command `.dotm` template to `%APPDATA%\kingsoft\wps\startup`.
5. Restart WPS and open a `.docx` document.

## Restore a Missing MathType Tab

1. Open `Tools` > `Add-ins`.
2. Locate `mathpage.wll` and `mathtype commands 2016.dotm`.
3. Select each unchecked item, click `Enable`, and confirm the WPS warning.
4. Confirm that both entries are checked.
5. Click `OK`.
6. Verify that the `MathType` ribbon tab appears.
7. Open the tab and confirm its equation commands are visible.

## Security Boundary

- Do not copy or run `MathType7破解补丁.exe`.
- Do not bundle or follow a PDF that combines installation with cracking instructions.
- Do not disable security software to make an installer or patch run.
- If licensing fails, use the vendor's authorized activation, trial, purchase, or support channels.
