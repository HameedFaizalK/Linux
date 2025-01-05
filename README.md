**Essansial commands for LVM: (https://www.tecmint.com/create-lvm-storage-in-linux/)**
<h1>reveal the distinct components: PV, VG, LV</h1>
 -> lvs, pvs, vgs
#ist all the disks and their partitions
 -> fdisk -l
#view the detailed information about all the Volume Groups
 -> vgdisplay
# list the file system disk space information
 -> df -TH
----------------------------------------------------
      #Creating LVM
  NOTE : Before creating LVM we needs to create disk drive
 - > fdisk -c /dev/sdb
      - Choose 'n' to create new.
      - Choose 'p' to create a primary partition.
      - Choose which number of partitions we need to create.
      - Press enter twice to use the full space of the disk.
      - We need to change the type of newly created partition type t.
      - Which number of partition need to change, choose the number which we created its 1.
        Here we need to change the type, we need to create LVM so we going to use the type code of LVM as 8e, if we do not know the type code Press L to list all types of codes.
      - Print the partition that we created to just confirm.
      - Here we can see the ID as 8e LINUX LVM.
      - Write the changes and exit the fdisk.
  Then restart the machine to verify the partition table using the fdisk command.
# create Physical Volumes using all 3 disks
  - > pvcreate /dev/sdb1 /dev/sdc1 /dev/sdd1
  -> make ensure  : pvs
#Creating Volume Groups : Create a Volume Group named tecmint_add_vg using the available free PV and a PE size of 32
  -> vgcreate -s 32M tecmint_add_vg /dev/sdb1 /dev/sdc1 /dev/sdd1
    make ensure :vgs / more info -> vgs -v
#get more vg info newely created
  -> vgdisplay (vg name)
#Creating LVM Logical Volumes






