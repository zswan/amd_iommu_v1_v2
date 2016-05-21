Please read AMD IOMMU spec for detail information.

This register is used by system software to enable the optional IOMMU Performance Optimization
feature. This feature allows accesses from privileged (usually integrated) I/O devices such as GPUs to
bypass the IOMMU when directly accessing system memory. It is recommended to set this bit, unless
it is planned for the system software to use the the host I/O tables for GPA->SPA redirection

As I know, when GPU use HSA and GPUVM is using iommuv1 at the same time
we must enable this feature to optimize performance, it is risk for guest os.
