# nvidia-t18x-can
NVIDIA SocketCAN drivers for 'Bosch Time Triggered M_CAN' and 'Tegra Hypervisor sec CAN'.

This repository contains two new CAN drivers shipped with Linux For Tegra R27.1.

https://developer.nvidia.com/embedded/linux-tegra

r27.1 - downloaded (2017-03-18) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-27-1

http://developer.download.nvidia.com/embedded/L4T/r27_Release_v1.0/BSP/r27.1.0_sources.tbz2

r28.1 - downloaded (2017-10-31) from

https://developer.nvidia.com/embedded/dlc/l4t-sources-28-1

The two Kconfig files tell about the new drivers:


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

This excerpt from the huge Linux 4.4 source tarball provided by NVIDIA is intended to study and preserve the new drivers. Especially to check the differences between the CAN FD capable M_CAN mainline driver and the provided 'Time Triggered M_CAN flavour' driver.