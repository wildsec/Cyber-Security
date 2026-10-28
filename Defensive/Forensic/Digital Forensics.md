1. **Collection:** The first phase of digital forensics is data collection. Identifying all the devices from which the data can be collected is essential. 
2. **Examination:** The collected data may overwhelm investigators due to its size. This data usually needs to be filtered, and the data of interest needs to be extracted.
3. **Analysis:** This is a critical phase. The investigators now have to analyze the data by correlating it with multiple pieces of evidence to draw conclusions.
4. **Reporting:** In the last phase of digital forensics, a detailed report is prepared. This report contains the investigation’s methodology and detailed findings from the collected evidence. It may also contain recommendations. This report is presented to law enforcement and executive management. 

## Types
- **Computer forensics**
- **Mobile forensics
- **Network forensics
- **Database forensics
- **Cloud forensics**
- **Email forensics

## Acquisition
* Proper Authorization
*  Chain of Custody
	* A chain of custody is a formal document containing all the details of the evidence. Some of the key details are listed below:
	- Description of the evidence (name, type).
	- Name of individuals who collected the evidence.
	- Date and time of evidence collection.
	- Storage location of each piece of evidence.
	- Access times and the individual record who accessed the evidence.
	- A sample chain of custody can be downloaded from **[here](https://www.nist.gov/document/sample-chain-custody-formdocx)**.
-  Use of Write Blockers

## Windows
- **Disk image:** The disk image contains all the data present on the storage device of the system (HDD, SSD, etc.). This data is non-volatile, meaning that the disk data would survive even after a restart of the operating system. For example, all the files like media, documents, internet browsing history, and more.

- **Memory image:** The memory image contains the data inside the operating system’s RAM. This memory is volatile, meaning the data will get lost after the system is powered off or restarted. For example, to capture open files, running processes, current network connections, etc., the memory image should be prioritized and taken first from the suspect’s operating system; otherwise, any restart or shutdown of the system would result in all the volatile data getting deleted. While carrying out digital forensics on a Windows operating system, disk and memory images are very important to collect.

### Tools

* **FTK Imager:** FTK Imager is a widely used tool for taking disk images of Windows operating systems. 
* **Autopsy:** [Autopsy](https://www.autopsy.com/) is a popular open-source digital forensics platform. An investigator can import an acquired disk image into this tool, and the tool will conduct an extensive analysis of the image.
* **DumpIt:** [DumpIt](https://www.toolwar.com/2014/01/dumpit-memory-dump-tools.html) offers the utility of taking a memory image from a Windows operating system.
* **Volatility:** [Volatility](https://volatilityfoundation.org/) is a powerful open-source tool for analyzing memory images.

## File Info Tools

[[PDFinfo]]
[[Exif-Tool]]