# M710Q opencore 配置
1. 包含了DW1820A无线网卡及蓝牙的配置；
2. 使用前，请计算三码，并填写在 PlatformInfo -> Generic -> MLB、 SystemSerialNumber、 SystemUUID；
3. 如果有连接dp转hdmi紫屏的，可以参考[使用 Hackintool 修复黑苹果 Intel 核显驱动外部显示器紫屏问题](https://blog.skk.moe/post/hackintosh-fix-magenta-screen/),修补 EDID，或制作缓冲帧补丁方式解决；
4. 尽量使用好一点的DP转hdmi线，要主动式的，升级到 10.15.5 后，避免黑屏问题；

# 使用说明
解锁CFG 后可以变更 Config—–Kernel—–Quirks
1. AppleXcpmCfgLock true -> false
2. AppleCpuPmCfgLock true -> false

不是使用的DW1820A网卡，可以关闭网卡PCI描述、蓝牙驱动

# 更新日志
20.6.9
- 更新 opencore 0.5.9

20.5.29
- 增加节能5项 XCPM.aml SSDT-PM.aml，但还是睡眠即醒

20.5.19
- 上传第一版

# 参考：
- [xjn' Blog 使用OpenCore引导黑苹果](https://blog.xjn819.com/?p=543)
- [紫氵朝 联想ThinkCentre M710Q微型主机黑苹果基本完善（2.15修复前置音频输出）](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1826205)
- [daliansky Lenovo-M710Q-Hackintosh](https://github.com/daliansky/Lenovo-M710Q-Hackintosh)