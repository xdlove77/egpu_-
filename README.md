首先重启，开机的时候按住 command+R，进入恢复模式，在实用工具找到终端，里面输入 csrutil diable 关闭系统的 SIP。

0、需要一个u盘格式化为 FAT 格式或者在mac中新建一个很小的FAT分区,在其u盘或者新建立的分区的根目录创建 \EFI\Boot\,下载apple_set_os.efi文件改名为bootx64.efi，将bootx64.efi放入\EFI\Boot\下。

1、进入windows设备管理器，展开显示适配器，找到独显屏蔽它。

2、下载2013 Visual C++ x86和gpu_switch。

2.1、已管理员身份执行gpu_switch 的 integrated.bat文件。
	
3、重启，如果是efi文件在usb中就插入之前格式化的usb（如果是新建分区就往下走），按住option选择efi boot 进入win，更新集显驱动，
		更新成功后有可能会黑屏（如果黑屏就强制重启（没黑屏就重启），再用efi boot进入，之后进入设备管理器屏蔽独显对应PCIE桥）

4、屏蔽成功之后重启，按住option选择efi boot启动 ，windows进度转动时插入egpu（注意只能插入笔记本左上角的typec接口，我的其他接口不管用），进入系统等待下载egpu驱动

5、下载成功后会提示重启，重启efi boot进入 ，旋转时插入egpu 就OK了

！！！！！！！！！！！！ 必须看的 ！！！！！！！！！！！！！！

必须注意：切回mac之前需要启动独显的PCIE桥，并且以管理员身份运行gpu-switch dedicated.bat。
	之后重启windows（不需要使用efi boot）检查dgpu是否显示。
	这些都设置好之后如果在切回win 就需要从2.1步骤重新配置（中间跳过步骤3的下载egpu驱动和步骤4下载集显驱动（因为这俩个都已下载过了）也会跳过步骤5）


资源URL : 
		apple_set_os.eft    : 	https://github.com/0xbb/apple_set_os.efi/releases
		2013 Visual C++ x86 : 	https://www.microsoft.com/en-us/download/details.aspx?id=40784
		gpu_switch          : 	https://github.com/0xbb/gpu-switch
