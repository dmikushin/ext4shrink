# ext4shrink

Tired of searching over partition resizing tools, like resize2fs? Yes, they are not made to be easy.

This script will shrink the ext4 filesystem down to the minimum possible size, plus 10%. The minimum size is set equal to the disk volume used by data.

The main purpose is to migrate the embedded system image on a smaller SD card.

