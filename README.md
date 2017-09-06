0、需要一个u盘格式化为MAC FAT 格式,在其u盘根目录创建 \EFI\Boot\,下载apple_set_os.efi文件改名为bootx64.efi，将bootx64.efi放入U盘\EFI\Boot\下

1、进入windows设备管理器，展开显示适配器，找到独显屏蔽它

2、下载2013 Visual C++ x86，下载gpu_switch并已管理员身份执行gpu_switch 的 integrated.bar
	
3、重启，插入之前格式化的usb，按住option选择efi boot 进入win，更新集显驱动，
		更新成功后会黑屏（强制重启，再用efi boot进入，之后屏蔽pcie x16）

4、屏蔽成功之后重启，按住option选择efi boot启动 ，windows转动时插入egpu，进入系统等待下载egpu驱动

5、下载成功后会提示重启，重启efi boot进入 ，旋转时插入egpu 就OK了

！！！！！！！！！！！！ 必须看的 ！！！！！！！！！！！！！！

必须注意：切回mac之前需要启动独显的 pcie x16 
	并且以管理员身份运行gpu-switch dedicated.bat
	之后重新启动并检查dgpu
	这些都设置好之后如果在切回win 就需要重新配置


资源URL : 
		apple_set_os.eft    : 	https://github.com/0xbb/apple_set_os.efi/releases
		2013 Visual C++ x86 : 	https://www.microsoft.com/en-us/download/details.aspx?id=40784
		gpu_switch          : 	https://github.com/0xbb/gpu-switch
