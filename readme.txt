$> dmg2img -l com.apple.recovery.boot/BaseSystem.dmg
		partition 0: Protective Master Boot Record (MBR : 0)
		partition 1: GPT Header (Primary GPT Header : 1)
		partition 2: GPT Partition Data (Primary GPT Table : 2)
		partition 3:  (Apple_Free : 3)
	->	partition 4: disk image (Apple_HFS : 4)
		partition 5:  (Apple_Free : 5)
		partition 6: GPT Partition Data (Backup GPT Table : 6)
		partition 7: GPT Header (Backup GPT Header : 7)

$> gdisk /dev/sdb
	/dev/sdb1 300M   efi   0700
   	/dev/sdb2 3G     apfs  af00

$> mkfs.vfat -F 32 -n "BOOT" /dev/sdb1

$> dmg2img -p 5 com.apple.recovery.boot/BaseSystem.dmg /dev/sda3 
