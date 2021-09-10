
# le9db patches

The patches provide sysctl knobs for protecting the specified amount of clean file pages (CFP) under memory pressure.

The kernel does not have a mechanism for selectively protecting clean file pages. A certain amount of the CFP is required by the userspace for normal operation. First of all, you need a cache of shared libraries and executable files. If the volume of the CFP cache falls below a certain level, thrashing and even livelock occurs.

Protection of CFP may be used to prevent thrashing and reducing I/O under memory pressure. Hard protection of CFP may be used to avoid high latency and prevent livelock in near-OOM conditions. The patch provides sysctl knobs for protecting the specified amount of clean file cache under memory pressure.

The `vm.clean_low_kbytes` sysctl knob provides *best-effort* protection of CFP. The CFP on the current node won't be reclaimed uder memory pressure when their amount is below `vm.clean_low_kbytes` *unless* we threaten to OOM or have no free swap space or vm.swappiness=0. Setting it to a high value may result in a early eviction of anonymous pages into the swap space by attempting to hold the protected amount of clean file pages in memory. The default value is defined by `CONFIG_CLEAN_LOW_KBYTES`.

The `vm.clean_min_kbytes` sysctl knob provides *hard* protection of CFP. The CFP on the current node won't be reclaimed under memory pressure when their amount is below `vm.clean_min_kbytes`. Setting it to a high value may result in a early out-of-memory condition due to the inability to reclaim the protected amount of CFP when other types of pages cannot be reclaimed. The default value is defined by `CONFIG_CLEAN_MIN_KBYTES`.

`le9db*-5.10` patches may be correctly applied to vanilla Linux 5.10—5.13.

The `le9db0`, `le9db1`, `le9db2` patches differ only in the default values.

`le9db0` just provides two sysctl knobs with 0 values and does not protect clean file pages by default.

`le9db1` provides only soft protection by default (`CONFIG_CLEAN_LOW_KBYTES=150000`, `CONFIG_CLEAN_MIN_KBYTES=0`). This patch may be safely used by default.

`le9db2` provides hard protection of clean file pages by default (`CONFIG_CLEAN_LOW_KBYTES=250000`, `CONFIG_CLEAN_MIN_KBYTES=200000`).

