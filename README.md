pppwn_mips to run in openwrt routers in combination with [PPPwn_WRT](https://github.com/MODDEDWARFARE/PPPwn_WRT). This is built with [PPPwn_cpp](https://github.com/xfangfang/PPPwn_cpp/).

### Router 

```bash
root@OpenWrt:~# uname -m
mips
root@OpenWrt:~# cat /proc/cpuinfo
system type		: Qualcomm Atheros TP9343 rev 0
machine			: TP-Link TL-WR941HP v2
processor		: 0
cpu model		: MIPS 74Kc V5.0
BogoMIPS		: 373.55
wait instruction	: yes
microsecond timers	: yes
tlb_entries		: 32
extra interrupt vector	: yes
hardware watchpoint	: yes, count: 4, address/irw mask: [0x0ffc, 0x0ffc, 0x0ffb, 0x0ffb]
isa			: mips1 mips2 mips32r1 mips32r2
ASEs implemented	: mips16 dsp dsp2
Options implemented	: tlb 4kex 4k_cache prefetch mcheck ejtag llsc dc_aliases perf_cntr_intr_bit cdmm contextconfig perf mm_full
shadow register sets	: 1
kscratch registers	: 0
package			: 0
core			: 0
VCED exceptions		: not available
VCEI exceptions		: not available

root@OpenWrt:~#
```

### Build it yourself
- Clone https://github.com/xfangfang/PPPwn_cpp

### commands
```bash
cmake -B build -DCMAKE_BUILD_TYPE=MinSizeRel -DZIG_TARGET=mips-linux-musl -DUSE_SYSTEM_PCAP=OFF -DZIG_COMPILE_OPTION='-msoft-float'
cmake --build build -t pppwn
strip build/pppwn
upx --lzma build/pppwn 
```

- Rename the `pppwn` file to `pppwn_mips` and transfer in your PPPwn_WRT installlation, and run `./run.sh`


