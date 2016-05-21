# amd_iommu_v1_v2

You maybe want to know:

(1)Currently AMD IOMMU hardware spec is here:

http://support.amd.com/TechDocs/48882_IOMMU.pdf

(2)Current AMD IOMMU driver maintianer is Joerg
who is also iommu subsystem maintainer, he ever
worked at AMD in Germany.

Wan Zongshun is me, and worked at iommu driver partly.
Sometimes I handled some issues reported from other team issues
maybe related to iommu.

Suravee is also handling iommu currently in USA, nice boy and powerful for iommu.

(3) I am in china, if you have some question for AMD iommu driver
I think I can help you. email:mcuos.com@gmail.com

About those patches:

patches-for-ACPIHID-devices -- base on kernel-4.6, merged into kernel-4.7

Those patches are to support ACPI HID device using iommu.
The current AMD has two device need those patches supporting, one is uart, the other is eMMC5.0.
But for eMMC-4.5.1, since it is basing on PCI bus, so no need this patch series.
