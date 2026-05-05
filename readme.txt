来源于：https://github.com/CLAY-BIOS/Lenovo-ThinkPad-T450s-Hackintosh-OpenCore

1. 无线网卡
	https://github.com/OpenIntelWireless/itlwm

2. Linux 上安装 dmg2img, 使用恢复模式安装Mac
	$> dmg2img -l com.apple.recovery.boot/BaseSystem.dmg
			partition 0: Protective Master Boot Record (MBR : 0)
			partition 1: GPT Header (Primary GPT Header : 1)
			partition 2: GPT Partition Data (Primary GPT Table : 2)
			partition 3:  (Apple_Free : 3)
			partition 4: EFI System Partition (C12A7328-F81F-11D2-BA4B-00A0C93EC93B : 4)
		-->	partition 5: disk image (Apple_HFS : 5)
			partition 6:  (Apple_Free : 6)
			partition 7: GPT Partition Data (Backup GPT Table : 7)
			partition 8: GPT Header (Backup GPT Header : 8)

	$> gdisk /dev/sdb
		/dev/sdb1 300M   efi   0700
	   	/dev/sdb2 4G     apfs  af00

	$> sudo mkfs.vfat -F 32 -n "BOOT" /dev/sdb1

	$> sudo dmg2img -p 5 com.apple.recovery.boot/BaseSystem.dmg /dev/sdb2
