# How to apply rt patch
1. Apply RT patches from linux (https://mirrors.edge.kernel.org/pub/linux/kernel/projects/rt/)
2. Apply TT patch `tt-5.15-r2.patch` (non-rt)
3. Apply this rt patch `rt.patch` ontop of the above two patches.

## Optional
4. You can also use `high-hz.patch` as well with `rt.patch`
