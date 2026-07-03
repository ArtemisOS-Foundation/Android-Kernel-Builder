<div align="center">

# 🚀 Android Kernel Builder

**Automated CI/CD pipeline for building custom Android kernels via GitHub Actions.**

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-green?logo=githubactions)](https://github.com/features/actions)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-orange)](https://github.com/tiann/KernelSU)
[![AnyKernel3](https://img.shields.io/badge/AnyKernel3-Integrated-purple)](https://github.com/osm0sis/AnyKernel3)

</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Setup Guide](#-setup-guide)
- [Usage Guide](#-usage-guide)
- [Configuration Parameters](#-configuration-parameters)
- [Build Outputs](#-build-outputs)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [Credits](#-credits)
- [License](#-license)

---

## 📋 Overview

**Android Kernel Builder** is a powerful, automated CI/CD pipeline built with GitHub Actions. This project enables you to compile custom Android kernels directly in the cloud, eliminating the need for a high-end local development machine. Whether you're a ROM developer, kernel maintainer, or Android enthusiast, this tool streamlines your workflow with zero local setup.

> 💡 **Why use this?** No need to install toolchains, configure cross-compilers, or manage dependencies on your local machine. Just fill in the form and let GitHub Actions handle the rest.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| ☁️ **Cloud-Native Compilation** | Build kernels entirely in GitHub's cloud infrastructure — no local resources required. |
| 📦 **AnyKernel3 Integration** | Automatically packages your compiled kernel into a flashable ZIP for seamless recovery flashing. |
| 🛡️ **KernelSU Support** | Optional integration with KernelSU Next patches for kernel-based root solutions. |
| ⚙️ **Fully Configurable** | Customize device codename, defconfig, kernel name, source URL, and branch. |
| 🔄 **Automated Workflow** | Trigger builds manually via `workflow_dispatch` with an intuitive web form. |
| 🌍 **Timezone Support** | Configurable timezone for build timestamps (defaults to `Asia/Jakarta`). |
| 🏷️ **Custom Build User** | Set your own `KBUILD_USER` identifier for personalized build metadata. |

---

## 🛠 Prerequisites

Before using this builder, ensure you have the following:

1. **A GitHub Account** — Required to fork/clone and run GitHub Actions.
2. **Kernel Source Repository** — Your Android kernel source must be publicly accessible (or use a Personal Access Token for private repos).
3. **Device Defconfig** — Know the exact defconfig file name for your target device (e.g., `surya_defconfig`, `ginkgo_defconfig`).
4. **Device Codename** — The official device codename (e.g., `surya`, `ginkgo`, `raphael`).

> ⚠️ **Note:** This workflow uses `workflow_dispatch` triggers, meaning builds must be initiated manually from the Actions tab.

---

## 🚀 Setup Guide

### Step 1: Fork or Clone the Repository

```bash
# Fork this repository to your own GitHub account, or clone it:
git clone https://github.com/ArtemisOS-Foundation/Android-Kernel-Builder.git
cd Android-Kernel-Builder
```

### Step 2: Verify Workflow File

Ensure the workflow file exists at the correct path:

```
.github/workflows/kernel-builder.yml
```

If you're setting this up for your own organization, review the workflow YAML to customize default values or add additional steps as needed.

### Step 3: Enable GitHub Actions

1. Navigate to your repository on GitHub.
2. Go to the **Settings** tab → **Actions** → **General**.
3. Ensure **Actions permissions** are set to **Allow all actions and reusable workflows**.

---

## 📲 Usage Guide

### 1. Navigate to Actions

- Open your repository on GitHub.
- Click the **Actions** tab at the top of the page.
- Select **Kernel Builder** from the left sidebar workflow list.

### 2. Trigger the Workflow

- Click the **Run workflow** button (dropdown) on the right side.
- A configuration form will appear with the following fields:

### 3. Fill in the Configuration Form

| Field | Icon | Description | Example |
|-------|------|-------------|---------|
| **Kernel Source URL** 🔗 | `🔗` | Direct HTTPS URL to your kernel source repository. | `https://github.com/YourName/android_kernel_xiaomi_surya` |
| **Kernel Source Branch** 🌿 | `🌿` | The branch you want to compile from. | `main`, `lineage-20`, `android13` |
| **Kernel Defconfig** ⚙️ | `⚙️` | The defconfig file name (without path). | `surya_defconfig` |
| **KernelSU Next Patch** 🛡️ | `🛡️` | Enable KernelSU Next patch integration. | `yes` / `no` |
| **KBuild User** 👤 | `👤` | Your identifier embedded in the kernel build info. | `ArtemisOS` |
| **Device Codename** 📱 | `📱` | Official device codename for AnyKernel3 packaging. | `surya` |
| **Kernel Name** 🏷️ | `🏷️` | Custom display name for your kernel output. | `ArtemisKernel-v1` |
| **Use AnyKernel3** 📦 | `📦` | Enable automatic flashable ZIP packaging. | `yes` / `no` |
| **AnyKernel Source URL** 📦 | `📦` | (Optional) Custom AnyKernel3 template URL if not using default. | `https://github.com/osm0sis/AnyKernel3` |
| **AnyKernel Branch** 🌿 | `🌿` | (Optional) Specific AnyKernel3 branch to use. | `master` |
| **Timezone** 🌍 | `🌍` | Timezone for build timestamps. | `Asia/Jakarta` |

> 📝 **Tip:** Fields marked with `*` are required. Optional fields will use sensible defaults if left empty.

### 4. Run the Build

- After filling in all required fields, click the green **Run workflow** button.
- The workflow will queue and begin execution within seconds.

### 5. Monitor & Download

- Click on the running workflow instance to view real-time logs.
- Once the build completes successfully, navigate to the **Artifacts** section at the bottom of the workflow summary page.
- Download your compiled kernel or AnyKernel3 ZIP package.

---

## 🔧 Configuration Parameters

### Required Fields

```
✅ Kernel Source URL      → https://github.com/user/kernel_repo
✅ Kernel Source Branch   → main
✅ Kernel Defconfig       → your_device_defconfig
✅ KBuild User            → YourName
✅ Device Codename        → your_device
✅ Kernel Name            → YourKernel-v1.0
✅ Use AnyKernel3         → yes / no
```

### Optional Fields

```
🔄 KernelSU Next Patch    → yes / no (default: no)
🔄 AnyKernel Source URL   → custom AnyKernel3 repo URL
🔄 AnyKernel Branch       → branch name (default: master)
🔄 Timezone               → Region/City (default: Asia/Jakarta)
```

### Example Configuration

| Parameter | Value |
|-----------|-------|
| Kernel Source URL | `https://github.com/ArtemisOS-Foundation/android_kernel_xiaomi_surya` |
| Kernel Source Branch | `lineage-21` |
| Kernel Defconfig | `surya_defconfig` |
| KernelSU Next Patch | `yes` |
| KBuild User | `ArtemisOS` |
| Device Codename | `surya` |
| Kernel Name | `ArtemisKernel-Surya` |
| Use AnyKernel3 | `yes` |
| AnyKernel Source URL | *(leave empty for default)* |
| AnyKernel Branch | *(leave empty for default)* |
| Timezone | `Asia/Jakarta` |

---

## 📦 Build Outputs

Upon successful completion, the following artifacts are generated:

| Artifact | Description |
|----------|-------------|
| `kernel-image` | Raw compiled kernel image (`Image`, `Image.gz`, or `Image.gz-dtb`). |
| `anykernel-zip` | Flashable AnyKernel3 ZIP package (if enabled). |
| `build-logs` | Full compilation logs for debugging purposes. |

> 📥 **Access:** Go to the completed workflow run → scroll to the **Artifacts** section → click to download.

---

## 🐛 Troubleshooting

### Build Fails at Compilation Stage

```
❌ Error: "defconfig not found"
✅ Fix: Verify your defconfig filename matches exactly (case-sensitive) in your kernel source's arch/arm64/configs/ directory.
```

### AnyKernel3 ZIP Not Generated

```
❌ Error: "AnyKernel3 packaging skipped"
✅ Fix: Ensure "Use AnyKernel3" is set to yes and the device codename is correct.
```

### KernelSU Patch Application Fails

```
❌ Error: "KernelSU patch conflict"
✅ Fix: Your kernel source may already have KernelSU integrated, or the branch is incompatible. Try setting "KernelSU Next Patch" to no.
```

### Workflow Not Visible

```
❌ Error: "No workflow runs found"
✅ Fix: Ensure the workflow file is in .github/workflows/ and Actions are enabled in repository settings.
```

---

## 🤝 Contributing

Contributions are welcome and greatly appreciated! Here's how you can help:

1. **Fork** the repository.
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** your changes: `git commit -m 'Add amazing feature'`
4. **Push** to the branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request.

Please ensure your code follows the existing style and includes appropriate documentation updates.

---

## 🙏 Credits

This project wouldn't be possible without the following amazing projects and individuals:

| Project / Person | Contribution |
|------------------|--------------|
| **[GitHub Actions](https://github.com/features/actions)** | CI/CD infrastructure and cloud build environment. |
| **[AnyKernel3](https://github.com/osm0sis/AnyKernel3)** by [_osm0sis_](https://github.com/osm0sis) | Flashable ZIP packaging framework for Android kernels. |
| **[KernelSU](https://github.com/tiann/KernelSU)** by [tiann](https://github.com/tiann) | Kernel-based root solution and Next-gen patches. |
| **[Android Open Source Project (AOSP)](https://source.android.com/)** | The foundation of Android kernel development. |
| **[LineageOS](https://lineageos.org/)** | Community-driven Android distribution and kernel references. |
| **ArtemisOS-Foundation Team** | Original workflow design, maintenance, and community support. |

Special thanks to all kernel developers, maintainers, and contributors in the Android custom ROM community for their continuous innovation and open-source spirit.

---

## 📄 License

```
Android Kernel Builder
Copyright (C) 2024 ArtemisOS-Foundation

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**. See the [LICENSE](LICENSE) file for the full license text.

> 🔗 **Read more:** [GNU GPL v3.0 Full Text](https://www.gnu.org/licenses/gpl-3.0.en.html)

---

<div align="center">

**Built with ❤️ by [ArtemisOS-Foundation](https://github.com/ArtemisOS-Foundation)**

⭐ *Star this repository if you find it helpful!*

</div>
