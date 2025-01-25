# Nested Virtualization troubleshooting

**Step-by-Step Commands and Troubleshooting for Nested Virtualization in TrueNAS**

1.  **Checking Virtualization Capabilities:** First, ensure that your host system supports virtualization. You can check for Intel VT-x (or AMD-V for AMD processors) by running the following command on your host system:

    ```bash
    grep -E --color 'vmx|svm' /proc/cpuinfo
    ```

    * `vmx` is for Intel processors.
    * `svm` is for AMD processors.

    If these flags are present, your CPU supports virtualization.
2.  **Enabling Nested Virtualization in TrueNAS:** The next step involves ensuring that nested virtualization is enabled in TrueNAS. Nested virtualization is supported on TrueNAS, but you might need to modify the settings for your specific virtual machine to expose the host CPU features to the guest VM.

    In the TrueNAS Web UI, navigate to **VMs > (Your VM) > Configuration** and add or modify the following options under **Advanced Options**:

    *   **`host:cpu`**: This ensures that the virtual machine uses the host CPU’s capabilities, including hardware virtualization.

        ```bash
        args: "-cpu host"
        ```

    This command tells the hypervisor to pass through the CPU's features to the virtual machine.
3.  **Adding the VMX Flag for Intel VT-x:** Intel VT-x or AMD-V must be explicitly enabled for nested virtualization. For Intel CPUs, the `vmx` flag is required, and for AMD, the equivalent is `svm`.

    Modify the configuration to pass the `vmx` flag:

    ```bash
    args: "-cpu host,+vmx"
    ```

    * `-cpu host` allows the guest VM to use the host CPU features.
    * `+vmx` enables Intel VT-x support within the guest VM.
4.  **Confirming CPU Flag Exposure:** After modifying the VM configuration, check that the CPU features (like VMX) are visible to the guest VM. Log into the guest VM and run the following command to verify that Intel VT-x is being passed through:

    ```bash
    egrep --color 'vmx' /proc/cpuinfo
    ```

    If the `vmx` flag appears in the output, then nested virtualization is enabled successfully.
5.  **Troubleshooting Kernel Parameters (if needed):** If you still encounter issues, you may need to add specific kernel parameters to your system to ensure proper virtualization support. Modify the `grub` configuration by adding the following line and then reboot your system:

    ```bash
    GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on"
    ```

    Or for AMD processors:

    ```bash
    GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on"
    ```

    After editing `grub`, update and reboot your system:

    ```bash
    sudo update-grub
    sudo reboot
    ```
6.  **Verifying Virtual Machine Performance:** After applying the configuration changes, monitor the performance of your guest VM. Ensure that the nested VMs inside the guest are able to run as expected. If performance is still lacking, check the host system’s CPU and RAM usage to ensure that resources are being allocated properly.

    You can also check the CPU stats inside the guest VM:

    ```bash
    top - 1
    ```

    or use `htop` for a more user-friendly interface to view resource allocation.
7.  **Debugging Logs (if nested virtualization fails):** If you encounter further issues, check the logs for any error messages related to CPU or virtualization:

    ```bash
    dmesg | grep -i kvm
    ```

    You can also check the VM logs directly from TrueNAS to see if any errors are reported during VM startup.

***

#### **Summary of All the Commands Ran:**

1.  **Check CPU virtualization flags:**

    ```bash
    grep -E --color 'vmx|svm' /proc/cpuinfo
    ```
2.  **Modify VM configuration (TrueNAS Web UI) to add CPU flags:**

    ```bash
    args: "-cpu host,+vmx"
    ```
3.  **Verify CPU flags inside the guest VM:**

    ```bash
    egrep --color 'vmx' /proc/cpuinfo
    ```
4.  **Enable kernel parameters for Intel or AMD virtualization (if needed):**

    ```bash
    GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on"
    ```

    or for AMD:

    ```bash
    GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on"
    ```
5.  **Reboot after modifying grub:**

    ```bash
    sudo update-grub
    sudo reboot
    ```
6.  **Check guest VM performance using `top`:**

    ```bash
    top - 1
    ```

    Or use `htop` for a more interactive view.
7.  **Check logs for virtualization errors:**

    ```bash
    dmesg | grep -i kvm
    ```

Here are all the commands we ran in the course of this troubleshooting:

1.  **Checking if hardware virtualization is available on the system:**

    ```bash
    kvm-ok
    ```
2.  **Checking the dmesg log for virtualization support:**

    ```bash
    dmesg | grep -i kvm
    ```
3.  **Checking if the kvm-intel module is in use:**

    ```bash
    lsmod | grep kvm
    ```
4.  **Stopping all running VMs to free up the kvm-intel module:**

    ```bash
    qm list
    qm stop <VMID>
    ```
5.  **Stopping Proxmox services related to KVM:**

    ```bash
    systemctl stop pvedaemon
    systemctl stop qemu-server
    ```
6.  **Unloading the kvm-intel module:**

    ```bash
    modprobe -r kvm-intel
    ```
7.  **Reloading the kvm-intel module:**

    ```bash
    modprobe kvm-intel
    ```
8.  **Restarting Proxmox services:**

    ```bash
    systemctl start pvedaemon
    systemctl start qemu-server
    ```
9.  **Verifying the virtualization flags:** For Intel CPUs:

    ```bash
    cat /proc/cpuinfo | grep vmx
    ```

    For AMD CPUs:

    ```bash
    cat /proc/cpuinfo | grep svm
    ```
10. **Checking the VM configuration file for the CPU settings:**

    ```bash
    echo "options kvm-intel nested=1" > /etc/modprobe.d/kvm-intel.conf
    ```
11. **Checking the TrueNAS logs for virtualization errors:** Navigate to the TrueNAS Web UI at: `System > Advanced > View Logs`.
12. **Rebooting the VM:**

    ```bash
    qm reboot <VMID>
    ```
