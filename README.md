
# Linksys EA8100 V2 Backup and OpenWrt Update Guide

This repository provides detailed instructions on how to back up the final official firmware for the Linksys EA8100 V2 and how to safely update the router to OpenWrt. Additionally, it covers how to utilize the router's dual-partition system to switch between firmware versions.

## Table of Contents
- [Introduction](#introduction)
- [Backup Official Firmware](#backup-official-firmware)
- [Switching Between Firmware Versions (Dual-Partition)](#switching-between-firmware-versions-dual-partition)
- [Updating to OpenWrt](#updating-to-openwrt)
- [Reverting to Official Firmware](#reverting-to-official-firmware)
- [FAQ](#faq)

## Introduction
The Linksys EA8100 V2 router supports OpenWrt, an open-source firmware that enables advanced features such as VPN support, custom firewall rules, and more detailed network management. Before proceeding with the update, it’s essential to back up the official firmware (FIR00 V2) to ensure you can revert to it if necessary.

This guide also explains how to take advantage of the router’s dual-partition system, which allows for easy switching between firmware versions.

## Backup Official Firmware
To back up the official firmware for the Linksys EA8100 V2, you can download it directly from this repository:

1. **Download the official firmware**: The final official firmware is available in the [`firmware`](./firmware) folder of this repository. You can also obtain it from the [Linksys support page](https://support.linksys.com/kb/article/4828-hk/).
   
2. **Access the router interface**:
   - Open a web browser and log in to the router at its default IP (usually `http://192.168.1.1`).
   
3. **Navigate to the firmware section**:
   - Go to `Troubleshooting -> Diagnostics -> Router Firmware`.
   - Use the "Backup Current Firmware" feature to create a backup, or download the firmware file from this repository.

4. **Save the backup safely**: Ensure you store this backup in a secure location, as you may need it if something goes wrong during the upgrade process.

## Switching Between Firmware Versions (Dual-Partition)
The Linksys EA8100 V2 utilizes a dual-partition system, which stores two firmware versions in separate partitions (A and B). You can easily switch between them:

1. **Switching between partitions**: 
   - In the router interface, go to `Troubleshooting -> Diagnostics -> Router Firmware -> Revert to Previous Firmware Version`.
   - This will switch between the two partitions, allowing you to return to the previous firmware version.

2. **Official firmware upgrade behavior**:
   - When you perform an official firmware upgrade, the router does not directly upgrade the partition you're currently using. If you are on **Partition A** and click "Upgrade," the system will actually switch to **Partition B** and perform the upgrade there. This ensures that you have a fallback partition in case the upgrade fails.

## Updating to OpenWrt
Before proceeding, ensure you have backed up the official firmware and understand the dual-partition system.

1. **Download the OpenWrt firmware**: Visit the [OpenWrt firmware page for the Linksys EA8100 V2](https://openwrt.org/toh/linksys/ea8100_v2) and download the appropriate firmware image.

2. **Access the router interface**:
   - Log in to your router’s web interface.

3. **Flash the OpenWrt firmware**:
   - Go to `Firmware Update`.
   - Select the OpenWrt firmware image you downloaded and initiate the update process.
   - The router will switch to the other partition (if you are on A, it will switch to B) and install OpenWrt there.

4. **Post-update configuration**:
   - After the router reboots, OpenWrt will be accessible at its default address (`http://192.168.1.1`).
   - Complete the initial OpenWrt configuration according to your needs.

## Reverting to Official Firmware
If you wish to return to the official firmware after using OpenWrt:

1. **Access OpenWrt interface**: 
   - Log in to OpenWrt at `http://192.168.1.1`.

2. **Flash the official firmware**: 
   - Go to `System > Backup/Flash Firmware`.
   - Upload the backed-up official firmware from this repository or the [Linksys support page](https://support.linksys.com/kb/article/4828-hk/) and start the flashing process.

3. **Reboot**: 
   - Once the process completes, the router will reboot with the original firmware.

4. **Switch partitions if necessary**:
   - If the router boots into OpenWrt after flashing, you may need to use the `Revert to Previous Firmware Version` feature mentioned above to switch to the partition with the official firmware.

## FAQ
**Q: Can I switch back and forth between OpenWrt and official firmware easily?**  
A: Yes, thanks to the dual-partition system, you can switch between OpenWrt and the official firmware using the `Revert to Previous Firmware Version` feature.

**Q: What happens if the OpenWrt installation fails?**  
A: If the installation fails, the router should fall back to the other partition with the original firmware. You can also try to switch partitions manually via the router interface or recovery mode.

**Q: Can I use the official firmware after flashing OpenWrt?**  
A: Yes, as long as you have backed up the official firmware, you can re-flash it at any time.
