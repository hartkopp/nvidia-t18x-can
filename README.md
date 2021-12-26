# nvidia-t18x-can
NVIDIA SocketCAN drivers for 'Bosch Time Triggered M_CAN' and 'Tegra Hypervisor sec CAN'.

This repository contains two new CAN drivers shipped with Linux For Tegra R27.1.

https://developer.nvidia.com/embedded/linux-tegra

This excerpt from the huge Linux 4.4 (Linux 4.9 in r31.1.0) source tarball provided by NVIDIA is intended to study and preserve the new drivers. Especially to check the differences between the CAN FD capable M_CAN mainline driver and the provided 'Time Triggered M_CAN flavour' driver.

The two Kconfig files tell about the new drivers (from r28.1):


    config MTTCAN
        tristate "Bosch M_TTCAN Devices"
        depends on ARCH_TEGRA_18x_SOC && CAN
        select STAGING
        help
          Support for the Bosch M_TTCAN driver. The Bosch MTTCAN CAN
          controller is having two independent CAN interfaces. These
          intefaces supports CAN-FD and TT-CAN. This driver will require
          SocketCAN support enabled in kernel.

    config MTTCAN_IVC
        tristate "Bosch M_TTCAN IVC Devices"
        depends on ARCH_TEGRA_18x_SOC && CAN
        select STAGING
        help
          Support for the Bosch M_TTCAN driver over IVC. The driver
          is implemented in sensor processor running RTOS. CAN services
          are made available to Linux though IVC. The Bosch MTTCAN
          CAN controller has two independent CAN interfaces. These
          intefaces supports CAN-FD and TT-CAN. This driver requires
          SocketCAN support enabled in kernel.

    config TEGRA_HV_SECCAN
        tristate "Tegra Hypervisor sec CAN"
        depends on TEGRA_HV_MANAGER
        help
          Add support for emulating a socketCAN device on tegra hypervisor systems.
          To compile this driver as a module, choose M here: the
          module will be called nvhvseccan.

Revision history:

r27.1 - downloaded (2017-03-18) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-27-1

http://developer.download.nvidia.com/embedded/L4T/r27_Release_v1.0/BSP/r27.1.0_sources.tbz2

r28.1 - downloaded (2017-10-31) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-28-1

r28.2 - downloaded (2018-02-15) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-28-2

has identical CAN drivers as in release r28.1

r31.1.0 - downloaded (2018-12-03) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-31-1-0

In 31.1.0 the mttcan and nvsec drivers have been integrated into one tree in
kernel/nvidia/... inside kernel_src.tbz2 inside public_sources.tbz2 .
The base kernel in kernel/kernel-4.9/Makefile points to version 4.9.108 .

r32.1 - downloaded (2019-05-12) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-32-1-JAX-TX2

In 32.1 the mttcan and nvsec drivers have been integrated into one tree in
kernel/nvidia/... inside kernel_src.tbz2 inside public_sources.tbz2 .
The base kernel in kernel/kernel-4.9/Makefile points to version 4.9.140 .

r32.2 - downloaded (2019-08-29) from

https://developer.nvidia.com/embedded/dlc/public_sources_AGX

r32.2.1 - downloaded (2019-08-29) from

https://developer.nvidia.com/embedded/dlc/r32-2-1_Release_v1.0/TX2-AGX/sources/public_sources.tbz2

r32.6.1 - downloaded (2021-12-26) from

https://developer.nvidia.com/embedded/l4t/r32_release_v6.1/sources/t186/public_sources.tbz2
