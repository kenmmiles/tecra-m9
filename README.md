# Goal

A kernel and userland tailored to work most effectively and efficiently
with the tecra m9, and particularly the limitations of low RAM and
spinning rust.

# TODO

Revist old dotfiles configurations and move it all here. The idea is
to build a new workflow around this old hardware.

#  System information

```bash
inxi -Fzxx -C -I -S -G -d -m -E
```

System:
  Kernel: 6.1.0-37-amd64 arch: x86_64 bits: 64 compiler: gcc v: 12.2.0
    Desktop: Xfce v: 4.18.1 tk: Gtk v: 3.24.36 wm: xfwm dm: startx Distro: Debian
    GNU/Linux 12 (bookworm)
Machine:
  Type: Laptop System: TOSHIBA product: TECRA M9 v: PTM91U-0X3058
    serial: <filter> Chassis: type: 10 v: Version 1.0 serial: <filter>
  Mobo: TOSHIBA model: Portable PC v: Version A0 serial: <filter>
    BIOS: TOSHIBA v: Version 1.90 date: 02/29/2008
Battery:
  ID-1: BAT1 charge: 6.1 Wh (100.0%) condition: 6.1/76.1 Wh (8.0%) volts: 11.2
    min: 10.8 model: G71C0006B210 serial: <filter> status: full
  Device-1: apple_mfi_fastcharge model: N/A serial: N/A charge: N/A
    status: N/A
Memory:
  RAM: total: 1.89 GiB used: 1.19 GiB (63.0%)
  Array-1: capacity: 4 GiB slots: 2 EC: None max-module-size: 2 GiB
  Device-1: DIMM 0 info: single-bank type: DDR2 size: 1024 MiB
    speed: 667 MT/s volts: N/A manufacturer: Infineon part-no: HYMP112S64CP6-Y5
  Device-2: DIMM 1 info: single-bank type: DDR2 size: 1024 MiB
    speed: 667 MT/s volts: N/A manufacturer: Infineon part-no: HYMP112S64CP6-Y5
CPU:
  Info: dual core model: Intel Core2 Duo T9300 bits: 64 type: MCP arch: Penryn
    rev: 6 cache: L1: 128 KiB L2: 6 MiB
  Speed (MHz): avg: 2501 min/max: 800/2501 boost: enabled cores: 1: 2501
    2: 2501 bogomips: 9974
  Flags: ht lm nx pae sse sse2 sse3 sse4_1 ssse3
Graphics:
  Device-1: NVIDIA G86M [Quadro NVS 130M] vendor: Toshiba driver: nvidia
    v: 340.108 arch: Tesla pcie: speed: 2.5 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:042a
  Display: server: X.Org v: 1.21.1.7 compositor: xfwm v: 4.18.0 driver: X:
    loaded: nvidia unloaded: fbdev,modesetting,vesa alternate: nouveau,nv
    gpu: nvidia display-ID: :0.0 screens: 1
  Screen-1: 0 s-res: 1440x900 s-dpi: 96
  Monitor-1: LVDS-0 res: 1440x900 dpi: 121 diag: 358mm (14.08")
  API: OpenGL v: 3.3.0 NVIDIA 340.108 renderer: Quadro NVS 130M/PCIe/SSE2
    direct-render: Yes
Audio:
  Device-1: Intel 82801H HD Audio vendor: Toshiba driver: snd_hda_intel
    v: kernel bus-ID: 00:1b.0 chip-ID: 8086:284b
  API: ALSA v: k6.1.0-37-amd64 status: kernel-api
  Server-1: PipeWire v: 0.3.65 status: n/a (root, process) with:
    1: pipewire-pulse status: active 2: wireplumber status: active
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)
Network:
  Device-1: Intel 82566MM Gigabit Network vendor: Toshiba driver: e1000e
    v: kernel port: bfe0 bus-ID: 00:19.0 chip-ID: 8086:1049
  IF: enp0s25 state: down mac: <filter>
  Device-2: Intel PRO/Wireless 4965 AG or AGN [Kedron] Network
    driver: iwl4965 v: in-tree: pcie: speed: 2.5 GT/s lanes: 1 bus-ID: 02:00.0
    chip-ID: 8086:4229
  IF: wlp2s0 state: up mac: <filter>
  IF-ID-1: enx82ed2c96e04c state: down mac: <filter>
Bluetooth:
  Device-1: Toshiba Integrated Bluetooth HCI type: USB driver: btusb v: 0.8
    bus-ID: 5-2:3 chip-ID: 0930:0508
  Report: hciconfig ID: hci0 rfk-id: 3 state: up address: <filter> bt-v: 1.2
    lmp-v: 2.0 sub-v: 77b
Drives:
  Local Storage: total: 149.05 GiB used: 95.21 GiB (63.9%)
  ID-1: /dev/sda vendor: Hitachi model: HTS722016K9SA00 size: 149.05 GiB
    speed: 1.5 Gb/s serial: <filter>
  Optical-1: /dev/sr0 vendor: MATSHITA model: DVD-RAM UJ-852S rev: 1.00
    dev-links: cdrom
  Features: speed: 24 multisession: yes audio: yes dvd: yes
    rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition:
  ID-1: / size: 144.71 GiB used: 95.21 GiB (65.8%) fs: ext4 dev: /dev/sda1
Swap:
  ID-1: swap-1 type: partition size: 976 MiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/sda5
  ID-2: swap-2 type: zram size: 1.89 GiB used: 353.2 MiB (18.3%)
    priority: 100 dev: /dev/zram0
Sensors:
  System Temperatures: cpu: 84.0 C mobo: N/A gpu: nvidia temp: 78 C
  Fan Speeds (RPM): cpu: 3295
Info:
  Processes: 190 Uptime: 11h 1m Init: systemd v: 252 target: graphical (5)
  default: graphical Compilers: gcc: 12.2.0 alt: 12 Packages: pm: dpkg
  pkgs: 2840 Shell: Sudo v: 1.9.13p3 running-in: tmux: inxi: 3.3.26

# Software and tweaks

Debian bookworm with XFCE
 - Installed legacy 340 nvidia drivers
  - https://gist.github.com/Anakiev2/b828ed2972c04359d52a44e9e5cf2c63
 - Using zram with 101%
 - Disable access time with `noatime` in `/etc/fstab`
 - Filesystem tweaks:
    - sudo tune2fs -O dir_index /dev/sda1
    - sudo tune2fs -o journal_data_writeback /dev/sda1
 - HDD tweaks:
    - sudo hdparm -W1 /dev/sda
    - sudo hdparm -B 254 /dev/sda
 - Set `vm.swappiness=10` in `/etc/sysctl.conf`
