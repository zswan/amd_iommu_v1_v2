
1. Why need this patch?

When we enabled or write some device drivers, that need iommu support,
but device drivers has some buggy or other issues, we oftenly disable
iommu by setting iommu=off or iommu=pt, okay, it is ok, all things maybe
workable, but it has some risk.

Firstly, simply set iommu=off, it is not good working, if your system has
only dma 32bit capbility device, you will get them not working, so please
don't use iommu=off.

Sencondly, set iommu=pt, it is better to do workaround to bypass issues
related to iommu, but you have to make all devices working for passthrough
iommu, if you still can not fix your device driver bug, you have to keep
all device bypass iommu, it is not reasonable.

Thirdly, if somebody really want to set one single or group device to passthrough
iommu, what you can do? Okay, please use this patches.


2. Why this patch did not merged into opensource?

Talked with Joerg for this patch, in the long term, he give me advice, not use
this patch, since it will encourage somebody not to fix his bug, and just do 
workaroud by using this driver.

That is ok, I totally agree with him, we should try your best to fix driver bug
issue related to iommu, not just do workaround by using my patches.

So this patch, just for debug stage.

for example:

Since AMD eMMC has ADMA2 capability with 64bit addressable, so we can set eMMC DMA to passthrough
iommu, do it step by step:

1. lspci to check devid of eMMC
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
2. apoly my this patch.
3. set devid (0x14 << 3) to passthrough_deviceid

passthrough_deviceid = 160;

4. build, and you will make eMMC controller bypass IOMMU, and eliminate the iommu translation layer,
that technically optimize the eMMC performance.
