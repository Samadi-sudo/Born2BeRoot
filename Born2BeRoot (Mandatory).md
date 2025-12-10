### <span style = "color: #5c9df2; text-decoration: underline;"> MBR vs GPT</span>

Before using a disk, it is essential to partition it.  **MBR**  (Master Boot Record) and  **GPT**  (GUID Partition Table) are two different ways to store partitioning information on a disk. This information determines, for example, where a partition begins and ends on the disk. This allows your system to know which sectors belong to which partitions and which partitions are bootable.  **Therefore, it is necessary to choose between MBR and GPT before creating partitions on a disk** .

<details>
  <summary> <strong>MBR</strong> (Master Boot Record)</summary>
<p style= "text-indent: 2em;">
<strong>1 — Historical standard (1983):</strong> It was introduced with IBM PC DOS 2.0 in 1983. It is old but still used for compatibility.
</p>

  <p style= "text-indent: 2em;">
  <strong>2 — Structure:</strong> It's called <strong>MBR</strong> because it's a boot sector located at the beginning of a drive. This sector contains a boot loader for the installed operating system as well as information about the logical partitions
  </p>
  
  <p style = "text-indent: 2em;">
  <strong>3 — BIOS Boot Process:</strong>The <strong style="text-decoration: underline;">BIOS</strong> loads the MBR. It consists of the first 512 bytes of the disk. From the information in the MBR, it determines the location of the boot loader.
  </p>

<p style="text-indent: 2em;">
<strong>4 — Limitations:</strong><br> • Supports disks only up to <strong>2 TB</strong> (because of 32-bit addressing).<br> • Maximum of <strong>4 primary partitions</strong>. More partitions require an “extended partition” containing logical partitions.<br> • No backup of partition table → corruption = possible data loss. 
</p> 
</details>

<details>
<summary><strong >GPT</strong>(GUID Partition Table)</summary>
<p style = "text-indent: 2em;">
	<strong>1-</strong> It's a new standard that is gradually replacing the aging MBR. It's associated with UEFI, which itself replaces the BIOS.
</p>

<p style = "text-indent: 2em;">
	<strong>2-</strong> It's called that way because each partition on your hard drive has a unique  identifier<strong>( GUID = Globally Unique Identifier).</strong> 
</p>

<p style="text-indent: 2em;">
<strong>3 — Compatibility:</strong><br> Includes a "protective MBR" so old software won’t think the disk is empty.
</p>

</details>

On an #MBR disk, partitioning and boot data are stored in a single location. If this data is overwritten or damaged, it's a disaster. In contrast, #GPT stores multiple copies of this data across the disk, making it much more robust and capable of data recovery if it becomes corrupted.
#GPT also stores the ==CRC (Cyclic Redundancy Check)== to verify that the data is intact. Therefore, if the data is corrupted, #GPT can report the problem and attempt to recover the damaged data from another location on the disk. With #MBR, there was no way to know if data was corrupted. And by the time a problem was detected, it was too late, because the disk partition might have disappeared, for example.
