Openwrt Mainline 25.12 Device Expand
============================
Extend support for these devices:
- Xiaomi CR880X M79 V1 (M79A)
- Redmi AX3000 / Xiaomi CR880X M81
- CMCC RAX3000Q
- CMCC A9 (cr660x's bootloader)
- Qihoo 360T6GS (cr660x's bootloader)
- Qihoo 360T7 (hanwckf's U-Boot)
- Newland NL-WR8103 / CMCC MR3000D-CIq v2
- TP-Link WMA301 v2.0 / v2.1

Known Issues
------------
- Most known issues are identical to those in upstream OpenWrt. Please refer to the official issue tracker for general bugs.
- CMCC A9: LAN1 and WAN ports are intentionally swapped. This is by design, not a bug.
- Please only open an issue in this repository if the problem is specific to one of the expanded devices listed above. For all other issues, please report upstream.

Note
------------
- There is currently no open-source NSS driver implementation for **ipq50xx** on newer Linux kernels. Therefore, this firmware does **not** support **NSS NAT** or **NSS Wi-Fi offload**. If you require maximum performance, this build is **not** recommended. For such use cases, please refer to [The QSDK branch of hzyitc's OpenWrt fork](https://github.com/hzyitc/openwrt-redmi-ax3000/tree/ipq50xx-qsdk-kernel-5.4-openwrt-21.02-qsdk-11.5.05.841.1029). At the moment, you must accept one of the following trade-offs: **either use an older kernel, or give up hardware acceleration.**

- For **ipq60xx** and **ipq807x** platforms, consider using
[qosmio's NSS Fork of OpenWrt](https://github.com/qosmio/openwrt-ipq) to unlock hardware acceleration.

- Default login address: http://192.168.1.1 or http://openwrt.lan, username: __root__, password: _none_.



How to build
============
### Requirements
```bash
sudo apt update -y
sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
  bzip2 ccache clang cmake cpio curl device-tree-compiler ecj fastjar flex gawk gettext gcc-multilib \
  g++-multilib git gnutls-dev gperf haveged help2man intltool lib32gcc-s1 libc6-dev-i386 libelf-dev \
  libglib2.0-dev libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses-dev libpython3-dev \
  libreadline-dev libssl-dev libtool libyaml-dev libz-dev lld llvm lrzsz mkisofs msmtp nano \
  ninja-build p7zip p7zip-full patch pkgconf python3 python3-pip python3-ply python3-docutils \
  python3-pyelftools qemu-utils re2c rsync scons squashfs-tools subversion swig texinfo uglifyjs \
  upx-ucl unzip vim wget xmlto xxd zlib1g-dev zstd
```

### Quickstart
```bash
# Clone this repository
git clone https://github.com/ByteArray0/openwrt-device-expand
cd openwrt-device-expand
git checkout openwrt-25.12

# Update and install feeds
./scripts/feeds update -a
./scripts/feeds install -a

# Configure for your device
make menuconfig

# Build
make
```

## Related Repositories
- [openwrt-redmi-ax3000](https://github.com/hzyitc/openwrt-redmi-ax3000)
- [Openwrt](https://github.com/openwrt/openwrt)
- [LuCI Web Interface](https://github.com/openwrt/luci): Modern and modular interface to control the device via a web browser.
- [Openwrt Packages](https://github.com/openwrt/packages): Community repository of ported packages.
- [OpenWrt Routing](https://github.com/openwrt/routing): Packages specifically focused on (mesh) routing.
- [OpenWrt Video](https://github.com/openwrt/video): Packages specifically focused on display servers and clients (Xorg and Wayland).
