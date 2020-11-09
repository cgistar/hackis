# 我的配置

| 名称       | 型号                          |
| ---------- | ----------------------------- |
| CPU        | i3 8100                       |
| 硬盘       | RC500                         |
| 内存       | 国产鸟、鱼牌混搭 16G          |
| 网卡       | DW1820A                       |
| DP 转 HDMI | 绿联 DP111，合金头 PS176 芯片 |

# M710Q opencore 配置

1. 包含了 DW1820A 无线网卡及蓝牙的配置；
2. 使用前，请计算三码，并填写在 PlatformInfo -> Generic -> MLB、 SystemSerialNumber、 SystemUUID；
3. 如果有连接 dp 转 hdmi 紫屏的，可以参考[使用 Hackintool 修复黑苹果 Intel 核显驱动外部显示器紫屏问题](https://blog.skk.moe/post/hackintosh-fix-magenta-screen/),修补 EDID，或制作缓冲帧补丁方式解决；
4. 尽量使用好一点的 DP 转 hdmi 线，要主动式的，升级到 10.15.5 后，避免黑屏问题；

# 使用说明

解锁 CFG 后可以变更 Config—–Kernel—–Quirks

1. AppleXcpmCfgLock true -> false
2. AppleCpuPmCfgLock true -> false
3. IgnoreInvalidFlexRatio：如果没有解鎖 CFG，必须勾选。
4. 不是使用的 DW1820A 网卡，可以关闭网卡 PCI 描述、蓝牙驱动

# RU.efi 解锁 CFG Lock

通过教程[解锁 MSR 0xE2、BIOS Lock 等隐藏选项新姿势，还黑果原生体验（附刷 AMI BIOS 教程）](http://bbs.pcbeta.com/viewthread-1834965-1-1.html)，查询到我的 BIOS，版本：M1AKT49A，需要修改 0x503

1. 通过 EFI 菜单进入 RU.efi
2. ALT+C
3. 选择 UEFI Variable
4. 按 PAGE UP 和 PAGE DOWN 进行翻页，找到 Setup 项，可能会看到两个 Setup 项，分别按回车进去看下，选择数据较多的一个 Setup。在数据视图中按 CTRL+PAGE UP 和 CTRL+PAGE DOWN 进行翻页；
5. 需修改 0x503 的值为 0，首先找到 0x500 再用左右方向键定位纵向 03 的数值，按回车键进入修改模式，直接输入数字 0，再按 CTRL+W 保存修改，你会看到"Updated OK: Setup"的信息，此时 BIOS Lock 的值就被写入了 BIOS 中。

感谢 @tanpengsccd 提供的简单方法:
- 进入菜单 按 space 显示所有选择项目
- 进入RU.efi
- 输入 setup_var 0x503 0x0
- 然后提示设置成功
- 再检查CFG Lock 已经解锁了
# BIOS 设置

1. 显卡缓存 256M
2. 关闭快速启动
3. 其它忘了。。。

# 更新日志

20.10.9

- Opencore 0.6.2;
- add H_EC to EC patch;
- add SSDT-PLUG GPRW 尝试修复睡眠秒醒问题;
- add SSDT-PMC nvram 方案;
- add Innie.kext 修复外置硬盘问题;
- remove USBPower.kext;

  20.6.9

- 更新 opencore 0.5.9

  20.5.29

- 增加节能 5 项 XCPM.aml SSDT-PM.aml，但还是睡眠即醒

  20.5.19

- 上传第一版

# 参考：

- [xjn' Blog 使用 OpenCore 引导黑苹果](https://blog.xjn819.com/?p=543)
- [紫氵朝 联想 ThinkCentre M710Q 微型主机黑苹果基本完善（2.15 修复前置音频输出）](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1826205)
- [daliansky Lenovo-M710Q-Hackintosh](https://github.com/daliansky/Lenovo-M710Q-Hackintosh)
