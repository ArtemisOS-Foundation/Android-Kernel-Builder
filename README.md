# Android Kernel Builder
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/ArtemisOS-Foundation/Android-Kernel-Builder/kernel-builder.yml?branch=main&style=flat-square&logo=github)](https://github.com/ArtemisOS-Foundation/Android-Kernel-Builder/actions)
[![License: GPL-3.0](https://img.shields.io/github/license/ArtemisOS-Foundation/Android-Kernel-Builder?style=flat-square)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/ArtemisOS-Foundation/Android-Kernel-Builder?style=flat-square)](https://github.com/ArtemisOS-Foundation/Android-Kernel-Builder/stargazers)

**Android Kernel Builder** is a powerful, automated CI/CD pipeline built with GitHub Actions. This project allows you to compile custom Android kernels directly in the cloud, eliminating the need for a high-end local development machine.

---

## 🚀 Key Features
- **Cloud-Native Compilation:** Build your kernel anywhere without taxing your PC.
- **AnyKernel3 Support:** Automatically packages your kernel into a flashable ZIP file.
- **KernelSU Integration:** Seamless support for the latest KernelSU patches.
- **Customizable Environment:** Easily configure your device codename, defconfig, and build parameters.
- **Automated Workflow:** Just push your settings and let GitHub Actions do the heavy lifting.

---

## 🛠 Setup & Usage

To start building your custom kernel, follow these simple steps:

### 1. Navigating to the Action
- Go to the **Actions** tab in this repository.
- Select **Kernel Builder** from the left sidebar.

### 2. Configuring the Build
- Click the **Run workflow** dropdown button.
- You will be presented with a configuration form. Refer to the images below for the required fields:

**Configuration Part 1:**
![Workflow Configuration](18131.png)

**Configuration Part 2:**
![Workflow Configuration](18132.png)

- **Kernel Source URL:** Link to your kernel source repository.
- **Kernel Source Branch:** Target branch (e.g., `main`, `lineage-20`).
- **Kernel Defconfig:** The specific defconfig file for your device.
- **KernelSU Next Patch:** Select `yes` if you want to include the patch.
- **Device Codename:** Your device codename (e.g., `surya`).
- **Kernel Name:** Custom name for your kernel output.
- **Use AnyKernel3:** Set to `yes` to enable auto-packaging.

### 3. Execution
- Once all fields are filled, click the green **Run workflow** button.
- Monitor your build progress in the **Actions** tab. Once completed, your artifact will be available to download!

---

## 📜 Credits
- **[GitHub Actions](https://github.com/features/actions)** for the CI/CD infrastructure.
- **[AnyKernel3](https://github.com/osm0sis/AnyKernel3)** by *osm0sis* for the deployment scripts.
- **[KernelSU](https://kernelsu.org/)** for the kernel-based root solution.

---

## 📄 License
This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**. See the [LICENSE](LICENSE) file for more details.

---
*Built with ❤️ by ArtemisOS-Foundation*
