# sshpiper on OpenWrt

[sshpiper](https://github.com/tg123/sshpiper), The missing reverse proxy for ssh scp.

## Build

### 1. Add sshpiper feed

Assuming `OPENWRT_TOP_SRCDIR` is the root of openwrt sources.

```
echo src-link sshpiper "$(pwd)/sshpiper" >> ${OPENWRT_TOP_SRCDIR}/feeds.conf
cd "${OPENWRT_TOP_SRCDIR}"
./scripts/feeds update sshpiper
./scripts/feeds install sshpiper
```



### 2. Enable sshpiper

sshpiper is not selected by default, so use menuconfig to select sshpiper.

```
make menuconfig
```



In the configure window, use the Up and Down keys to move the cursor and the Left and Right keys to choose an action.

1. Select *Network* to enter its submenu.
2. Enable *sshpiper* by moving the cursor to it and pressing **Y**.
3. Select *Exit* to exit.

### 3. Build sshpiper

```
make package/sshpiper/{clean,compile} V=s
```



### 4. Install

Copy the generated **ipk** file into OpenWrt, and install with **opkg**.

```
opkg install sshpiper_*.ipk
```



## Usage

TBD.



### Test

TBD.
