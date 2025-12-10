# MBR vs GPT

Before using a disk, it is essential to partition it.  
**MBR** (Master Boot Record) and **GPT** (GUID Partition Table) are two different ways to store partitioning information on a disk. This information determines, for example, where a partition begins and ends on the disk. This allows your system to know which sectors belong to which partitions and which partitions are bootable.  
**Therefore, it is necessary to choose between MBR and GPT before creating partitions on a disk.**

<details>
  <summary><strong>MBR (Master Boot Record)</strong></summary>

&nbsp;&nbsp;&nbsp;&nbsp;**1 — Historical standard (1983):**  
&nbsp;&nbsp;&nbsp;&nbsp;It was introduced with IBM PC DOS 2.0 in 1983. It is old but still used for compatibility.

&nbsp;&nbsp;&nbsp;&nbsp;**2 — Structure:**  
&nbsp;&nbsp;&nbsp;&nbsp;It's called **MBR** because it's a boot sector located at the beginning of a drive. This sector contains a boot loader for the installed operating system as well as information about the logical partitions.

&nbsp;&nbsp;&nbsp;&nbsp;**3 — BIOS Boot Process:**  
&nbsp;&nbsp;&nbsp;&nbsp;The **BIOS** loads the MBR. It consists of the first 512 bytes of the disk. From the information in the MBR, it determines the location of the boot loader.

&nbsp;&nbsp;&nbsp;&nbsp;**4 — Limitations:**  
&nbsp;&nbsp;&nbsp;&nbsp;- Supports disks only up to **2 TB** (because of 32-bit addressing).  
&nbsp;&nbsp;&nbsp;&nbsp;- Maximum of **4 primary partitions**. More partitions require an “extended partition” containing logical partitions.  
&nbsp;&nbsp;&nbsp;&nbsp;- No backup of partition table → corruption = possible data loss.

</details>

<details>
  <summary><strong>GPT (GUID Partition Table)</strong></summary>

&nbsp;&nbsp;&nbsp;&nbsp;**1 — New standard:**  
&nbsp;&nbsp;&nbsp;&nbsp;It's a new standard that is gradually replacing the aging MBR. It's associated with UEFI, which itself replaces the BIOS.

&nbsp;&nbsp;&nbsp;&nbsp;**2 — GUID:**  
&nbsp;&nbsp;&nbsp;&nbsp;Each partition on your hard drive has a unique identifier (**GUID = Globally Unique Identifier**).

&nbsp;&nbsp;&nbsp;&nbsp;**3 — Compatibility:**  
&nbsp;&nbsp;&nbsp;&nbsp;Includes a "protective MBR" so old software won’t think the disk is empty.

</details>

On an `MBR` disk, partitioning and boot data are stored in a single location. If this data is overwritten or damaged, it's a disaster.  
In contrast, `GPT` stores multiple copies of this data across the disk, making it much more robust and capable of data recovery if it becomes corrupted.  
`GPT` also stores the **CRC (Cyclic Redundancy Check)** to verify that the data is intact.  
Therefore, if the data is corrupted, `GPT` can report the problem and attempt to recover the damaged data from another location on the disk.  
With `MBR`, there was no way to know if data was corrupted. And by the time a problem was detected, it was too late, because the disk partition might have disappeared, for example.
