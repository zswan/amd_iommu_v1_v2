Basically iommu identify device by PCI BDF, but some none-pci device
you have to do sw workaroud for them when they do DMA transfer.

So those patches just to solve issues that non-pci device using iommu.
Note, since from kernel-4.7, those patches will be included in upstream.
