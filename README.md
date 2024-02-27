# Kernel-PCI-Run-Levels-Doc
Resolving PCI Device Issues, Verifying Kernel Install, and Understanding Run Levels in RHEL

## Resolving PCI Device Issues, Verifying Kernel Install, and Understanding Run Levels in RHEL

### Resolving an Issue with a PCI Device
1. Identify the PCI device using the command 'lspci' to list all PCI devices.
2. Check for drivers: Use 'lspci -k' to see the kernel driver in use for each device.
3. Install missing drivers: If the correct driver is not loaded, you may need to install it. This could involve enabling additional repositories or using a package manager.
4. Check 'dmesg' for errors with 'dmesg | grep -i pci'.
5. Update your system using 'sudo yum update' to ensure all components are current.

### Verifying a Kernel Install
1. Check the current kernel version with 'uname -r'.
2. List all installed kernels with 'rpm -q kernel'.
3. Ensure the boot loader is updated. Check the GRUB configuration or use 'grubby --default-kernel' to check the default kernel.

### Differences in Run Levels between RHEL 7 and RHEL 8
RHEL 7 uses the traditional init system with run levels, whereas RHEL 8 transitions to using systemd, which uses 'targets' instead of run levels. However, for compatibility, it maps old run levels to targets:
- Runlevel 0: poweroff.target
- Runlevel 1: rescue.target
- Runlevel 3: multi-user.target
- Runlevel 5: graphical.target
- Runlevel 6: reboot.target
