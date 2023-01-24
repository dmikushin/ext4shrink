# ext4shrink

Tired of dealing with the command-line resizing tools, like `resize2fs`? Yes, they are not made to be easy.

This script will shrink the ext4 partition down to the minimum possible size in one shot. The minimum size is set equal to the disk volume used by data. Extra 10% of free space will be added to give some room for modifications.

The main purpose is to migrate the embedded system image on a smaller pen drive or SD card.

## Example

The following output demonstrates the script in the works for a sample 32 GB SD card:

```
$ sudo ./ext4shrink /dev/sdb
Partition info for /dev/sdb:
BYT;
/dev/sdb:31266439168B:scsi:512:512:msdos:Generic- SD/MMC:;
1:4194304B:1970139647B:1965945344B:ext4::;
ext4 partition found, partition number is 1
ext4 partition blockdev device constructed: /dev/sdb1
ext4 partition starts at offset 4194304B
Press enter to continue if you have valid data above...

This next step might complain about superblock or partition table corruption, answer N to the abort prompt if it comes up:
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 41772/116640 files (0.3% non-contiguous), 326391/470751 blocks
resize2fs 1.46.5 (30-Dec-2021)
Minimum size of ext4 partition determined to be 427956
Adding 10 percent to minimum size to leave a little breathing room, now is 470751.  Resizing filesystem after you press enter to continue...

resize2fs 1.46.5 (30-Dec-2021)
The filesystem is already 470751 (4k) blocks long.  Nothing to do!

e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 41772/116640 files (0.3% non-contiguous), 326391/470751 blocks
Resizing ext4 filesystem on /dev/sdb1 to 470751 complete!
Partition new size 1928196096
New partition end offset 1970139145... removing original ext4 partition table entry...
Creating new shrunken ext4 partition table entry...
Done!
```
