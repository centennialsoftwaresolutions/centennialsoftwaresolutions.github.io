# Yocto 2.2.3 Based Linux Kernel Development Only 25% Efficient

![yocto_project_logo](yocto_project_logo.png)

This post lists the efficiency of Linux Kernel development using Yocto. It shows that developers who use Yocto to do kernel development spend at least **75%** of their recompile time waiting on the Yocto build system.

**Set Up**

This experiment was done in VirtualBox Version 5.1.30 r118389 (Qt5.6.2) running on this [computer and OS setup](http://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information).

It was run in Yocto 2.2.3 included with PetaLinux Tools 2017.4 which can be set up using [these](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools) instructions.

**Some Data**

Time to Execute BitBake

\-C, no recompile

real 1m22.290s 

user 0m43.175s 

sys 0m15.436s

\-f, no recompile

real 1m16.877s user 0m41.936s sys 0m14.508s

\-C, recompile

real 1m40.471s 

user 0m56.294s 

sys 0m18.285s

\-f, recompile

real 1m41.264s 

user 0m55.497s 

sys 0m19.174s

Some Observations

-   Its costs more than 1 min to use Yocto 2.2.3 in this set up.
    
-   There was a 82% Yocto 2.2.3 overhead to recompile a single Linux kernel file with -C
    
-   There was a 75% Yocto 2.2.3 overhead to recompile a single Linux kernel file with -f
    
-   These numbers imply that if your developers use Yocto to do kernel development, **Yocto** is costing you 75% to 82% of your development cost
    
-   The overhead suggests that using Yocto bitbake is not an efficient way to do Linux kernel development
    
-   Observing the experiment, the situation could be helped by speeding up "Initializing tasks"
    

**Experiment**

```
touch start.cC.compile
time bitbake -c compile -C compile virtual/kernel
touch end.cC.compile
find . -cnewer start.cC.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cC.compile.files.nochange
```

**bitbake -c compile -C compile virtual/kernel**

Output

```
Loading cache: 100% |##############################################################################################################################################| Time: 0:00:06
Loaded 3303 entries from dependency cache.
Parsing recipes: 100% |############################################################################################################################################| Time: 0:00:13
Parsing of 2512 .bb files complete (2474 cached, 38 parsed). 3307 targets, 227 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
NOTE: Tainting hash to force rebuild of task /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb, do_compile
WARNING: /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb.do_compile is tainted from a forced run0
Initialising tasks: 100% |#########################################################################################################################################| Time: 0:00:18
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 284 tasks of which 283 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.

real	1m22.290s
user	0m43.175s
sys	0m15.436s
```

Output Files Changed

```
cat bitbake.cC.compile.files.nochange
```

Sorted Files changed

```
./bitbake.lock
./tmp/log/cooker/plnx_aarch64
./tmp/log/cooker/plnx_aarch64/console-latest.log
./conf/sanity_info
./cache/bb_persist_data.sqlite3
./cache/bb_codeparser.dat
./tmp/sstate-control/index-x86_64
./tmp/sstate-control/index-x86_64_aarch64
./tmp/sstate-control/index-allarch
./tmp/sstate-control/index-aarch64
./tmp/sstate-control/index-plnx_aarch64
./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
./tmp/buildstats
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
./cache/local_file_checksum_cache.dat
./cache
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
./tmp/buildstats/20180526054125
./tmp/buildstats/20180526054125/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.12153
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/uapi/linux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.missing-syscalls.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/usr/.initramfs_data.cpio.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/kernel
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.12153
./tmp/buildstats/20180526054125/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
./sstate-cache/ae
./sstate-cache/ae/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:aed7583c589916385a150b62286f9ab8_compile.tgz.siginfo
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.aed7583c589916385a150b62286f9ab8
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.aed7583c589916385a150b62286f9ab8
./tmp/buildstats/20180526054125/build_stats
./tmp/log/cooker/plnx_aarch64/20180526054059.log
./end.cC.compile
./bitbake.cC.compile.files.nochange
```

**bitbake -c compile -f virtual/kernel**

```
touch start.cf.compile
time bitbake -c compile -f virtual/kernel
touch end.cf.compile
find . -cnewer start.cf.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cf.compile.files.nochange
```

Output

```
Loading cache: 100% |##############################################################################################################################################| Time: 0:00:05
Loaded 3303 entries from dependency cache.
Parsing recipes: 100% |############################################################################################################################################| Time: 0:00:13
Parsing of 2512 .bb files complete (2474 cached, 38 parsed). 3307 targets, 227 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
NOTE: Tainting hash to force rebuild of task /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb, do_compile
WARNING: /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb.do_compile is tainted from a forced run0
Initialising tasks: 100% |#########################################################################################################################################| Time: 0:00:17
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 284 tasks of which 283 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.

real	1m16.877s
user	0m41.936s
sys	0m14.508s
```

Output Files Changed

```
cat bitbake.cf.compile.files.nochange
```

Sorted Files Changed

```
./bitbake.lock
./tmp/log/cooker/plnx_aarch64
./tmp/log/cooker/plnx_aarch64/console-latest.log
./conf/sanity_info
./cache/bb_persist_data.sqlite3
./cache/bb_codeparser.dat
./tmp/sstate-control/index-x86_64
./tmp/sstate-control/index-allarch
./tmp/sstate-control/index-x86_64_aarch64
./tmp/sstate-control/index-aarch64
./tmp/sstate-control/index-plnx_aarch64
./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
./tmp/buildstats
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
./cache/local_file_checksum_cache.dat
./cache
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
./tmp/buildstats/20180526054247
./tmp/buildstats/20180526054247/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.17549
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/uapi/linux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.missing-syscalls.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/usr/.initramfs_data.cpio.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/kernel
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build
./tmp/buildstats/20180526054247/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.17549
./sstate-cache/b9
./sstate-cache/b9/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:b9c844bf37157f3ec11f97be4bcba37b_compile.tgz.siginfo
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.b9c844bf37157f3ec11f97be4bcba37b
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.b9c844bf37157f3ec11f97be4bcba37b
./tmp/buildstats/20180526054247/build_stats
./tmp/log/cooker/plnx_aarch64/20180526054222.log
./end.cf.compile
./bitbake.cf.compile.files.nochange
```

**diff**

```
diff -u bitbake.cC.compile.files.nochange bitbake.cf.compile.files.nochange > diff.cC.cf.nochange
```

diff.cC.cf.nochange

```
--- bitbake.cC.compile.files.nochange	2018-05-25 23:42:22.033551641 -0600
+++ bitbake.cf.compile.files.nochange	2018-05-25 23:43:40.361551641 -0600
@@ -5,8 +5,8 @@
 ./cache/bb_persist_data.sqlite3
 ./cache/bb_codeparser.dat
 ./tmp/sstate-control/index-x86_64
-./tmp/sstate-control/index-x86_64_aarch64
 ./tmp/sstate-control/index-allarch
+./tmp/sstate-control/index-x86_64_aarch64
 ./tmp/sstate-control/index-aarch64
 ./tmp/sstate-control/index-plnx_aarch64
 ./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
@@ -14,12 +14,12 @@
 ./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
 ./cache/local_file_checksum_cache.dat
 ./cache
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
-./tmp/buildstats/20180526054125
-./tmp/buildstats/20180526054125/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
+./tmp/buildstats/20180526054247
+./tmp/buildstats/20180526054247/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.12153
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.17549
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
@@ -29,15 +29,15 @@
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/usr/.initramfs_data.cpio.d
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/kernel
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build
+./tmp/buildstats/20180526054247/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.12153
-./tmp/buildstats/20180526054125/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
-./sstate-cache/ae
-./sstate-cache/ae/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:aed7583c589916385a150b62286f9ab8_compile.tgz.siginfo
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.17549
+./sstate-cache/b9
+./sstate-cache/b9/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:b9c844bf37157f3ec11f97be4bcba37b_compile.tgz.siginfo
 ./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
-./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.aed7583c589916385a150b62286f9ab8
-./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.aed7583c589916385a150b62286f9ab8
-./tmp/buildstats/20180526054125/build_stats
-./tmp/log/cooker/plnx_aarch64/20180526054059.log
-./end.cC.compile
-./bitbake.cC.compile.files.nochange
+./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.b9c844bf37157f3ec11f97be4bcba37b
+./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.b9c844bf37157f3ec11f97be4bcba37b
+./tmp/buildstats/20180526054247/build_stats
+./tmp/log/cooker/plnx_aarch64/20180526054222.log
+./end.cf.compile
+./bitbake.cf.compile.files.nochange
```

**touch /home/pfefferz/plprj4/mtd\_board/build/tmp/work-shared/plnx\_aarch64/kernel-source/init/main.c**

**bitbake -c compile -C compile virtual/kernel**

Output

```
Loading cache: 100% |##############################################################################################################################################| Time: 0:00:05
Loaded 3303 entries from dependency cache.
Parsing recipes: 100% |############################################################################################################################################| Time: 0:00:12
Parsing of 2512 .bb files complete (2474 cached, 38 parsed). 3307 targets, 227 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
NOTE: Tainting hash to force rebuild of task /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb, do_compile
WARNING: /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb.do_compile is tainted from a forced run0
Initialising tasks: 100% |#########################################################################################################################################| Time: 0:00:17
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 284 tasks of which 283 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.

real	1m40.471s
user	0m56.294s
sys	0m18.285s
```

Output Files Changed

```
cat bitbake.cC.compile.files.change
```

Sorted Files Changed

```
./bitbake.lock
./tmp/log/cooker/plnx_aarch64
./tmp/log/cooker/plnx_aarch64/console-latest.log
./conf/sanity_info
./cache/bb_persist_data.sqlite3
./cache/bb_codeparser.dat
./tmp/sstate-control/index-x86_64
./tmp/sstate-control/index-allarch
./tmp/sstate-control/index-x86_64_aarch64
./tmp/sstate-control/index-aarch64
./tmp/sstate-control/index-plnx_aarch64
./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
./tmp/buildstats
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
./cache/local_file_checksum_cache.dat
./cache
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
./tmp/buildstats/20180526054404
./tmp/buildstats/20180526054404/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.22930
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/uapi/linux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.missing-syscalls.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/main.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.main.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/usr/.initramfs_data.cpio.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/kernel
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/vmlinux.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.version
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/compile.h
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/version.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.version.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/built-in.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.built-in.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_vmlinux1
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms1.S
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms1.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_vmlinux2
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms2.S
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms2.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/vmlinux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/System.map
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_System.map
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.vmlinux.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/Image
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/.Image.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.22930
./tmp/buildstats/20180526054404/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
./sstate-cache/3f
./sstate-cache/3f/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:3facba0ad0a9c54ccc8bfe31781b7b73_compile.tgz.siginfo
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.3facba0ad0a9c54ccc8bfe31781b7b73
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.3facba0ad0a9c54ccc8bfe31781b7b73
./tmp/buildstats/20180526054404/build_stats
./tmp/log/cooker/plnx_aarch64/20180526054340.log
./bitbake.cC.compile.files.change
./end.cC.compile
```

**touch /home/pfefferz/plprj4/mtd\_board/build/tmp/work-shared/plnx\_aarch64/kernel-source/init/main.c**

**bitbake -c compile -f virtual/kernel**

Output

```
Loading cache: 100% |##############################################################################################################################################| Time: 0:00:06
Loaded 3303 entries from dependency cache.
Parsing recipes: 100% |############################################################################################################################################| Time: 0:00:12
Parsing of 2512 .bb files complete (2474 cached, 38 parsed). 3307 targets, 227 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
NOTE: Tainting hash to force rebuild of task /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb, do_compile
WARNING: /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/recipes-kernel/linux/linux-xlnx_4.9.bb.do_compile is tainted from a forced run9
Initialising tasks: 100% |#########################################################################################################################################| Time: 0:00:17
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 284 tasks of which 283 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.

real	1m41.264s
user	0m55.497s
sys	0m19.174s
```

Output Files Changed

```
cat bitbake.cf.compile.files.change
```

Sorted Files Changed

```
./bitbake.lock
./tmp/log/cooker/plnx_aarch64
./tmp/log/cooker/plnx_aarch64/console-latest.log
./conf/sanity_info
./cache/bb_persist_data.sqlite3
./cache/bb_codeparser.dat
./tmp/sstate-control/index-x86_64
./tmp/sstate-control/index-x86_64_aarch64
./tmp/sstate-control/index-allarch
./tmp/sstate-control/index-aarch64
./tmp/sstate-control/index-plnx_aarch64
./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
./tmp/buildstats
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
./cache/local_file_checksum_cache.dat
./cache
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
./tmp/buildstats/20180526054551
./tmp/buildstats/20180526054551/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.28326
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/uapi/linux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.missing-syscalls.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/main.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.main.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/usr/.initramfs_data.cpio.d
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/kernel
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/vmlinux.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.version
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated/compile.h
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/generated
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/version.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.version.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/built-in.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/init/.built-in.o.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_vmlinux1
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms1.S
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms1.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_vmlinux2
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms2.S
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_kallsyms2.o
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/vmlinux
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/System.map
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.tmp_System.map
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/.vmlinux.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/Image
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/.Image.cmd
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.28326
./tmp/buildstats/20180526054551/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
./sstate-cache/5c
./sstate-cache/5c/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:5c41e1a6bd27c7d5374eff653f032a6e_compile.tgz.siginfo
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.5c41e1a6bd27c7d5374eff653f032a6e
./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.5c41e1a6bd27c7d5374eff653f032a6e
./tmp/buildstats/20180526054551/build_stats
./tmp/log/cooker/plnx_aarch64/20180526054527.log
./end.cf.compile
./bitbake.cf.compile.files.change
```

**diff**

```
diff -u bitbake.cC.compile.files.change bitbake.cf.compile.files.change > diff.cC.cf.change
```

diff.cC.cf.change

```
--- bitbake.cC.compile.files.change	2018-05-25 23:45:26.485551641 -0600
+++ bitbake.cf.compile.files.change	2018-05-25 23:47:13.189551641 -0600
@@ -5,8 +5,8 @@
 ./cache/bb_persist_data.sqlite3
 ./cache/bb_codeparser.dat
 ./tmp/sstate-control/index-x86_64
-./tmp/sstate-control/index-allarch
 ./tmp/sstate-control/index-x86_64_aarch64
+./tmp/sstate-control/index-allarch
 ./tmp/sstate-control/index-aarch64
 ./tmp/sstate-control/index-plnx_aarch64
 ./tmp/cache/linaro-glibc/plnx_aarch64/x86_64/bb_cache.dat.f736674305bf79334de8d3ea5f52fc9d
@@ -14,12 +14,12 @@
 ./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.taint
 ./cache/local_file_checksum_cache.dat
 ./cache
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.task_order
-./tmp/buildstats/20180526054404
-./tmp/buildstats/20180526054404/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
+./tmp/buildstats/20180526054551
+./tmp/buildstats/20180526054551/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.22930
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/run.do_compile.28326
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/include/config
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/source
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/Makefile
@@ -53,14 +53,14 @@
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/Image
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/linux-plnx_aarch64-standard-build/arch/arm64/boot/.Image.cmd
 ./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp
-./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.22930
-./tmp/buildstats/20180526054404/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
-./sstate-cache/3f
-./sstate-cache/3f/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:3facba0ad0a9c54ccc8bfe31781b7b73_compile.tgz.siginfo
+./tmp/work/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/temp/log.do_compile.28326
+./tmp/buildstats/20180526054551/linux-xlnx-4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0/do_compile
+./sstate-cache/5c
+./sstate-cache/5c/sstate:linux-xlnx:plnx_aarch64-xilinx-linux:4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd:r0:plnx_aarch64:3:5c41e1a6bd27c7d5374eff653f032a6e_compile.tgz.siginfo
 ./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx
-./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.3facba0ad0a9c54ccc8bfe31781b7b73
-./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.3facba0ad0a9c54ccc8bfe31781b7b73
-./tmp/buildstats/20180526054404/build_stats
-./tmp/log/cooker/plnx_aarch64/20180526054340.log
-./bitbake.cC.compile.files.change
-./end.cC.compile
+./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.5c41e1a6bd27c7d5374eff653f032a6e
+./tmp/stamps/plnx_aarch64-xilinx-linux/linux-xlnx/4.9-xilinx-v2017.4+gitAUTOINC+b450e900fd-r0.do_compile.sigdata.5c41e1a6bd27c7d5374eff653f032a6e
+./tmp/buildstats/20180526054551/build_stats
+./tmp/log/cooker/plnx_aarch64/20180526054527.log
+./end.cf.compile
+./bitbake.cf.compile.files.change
```

**Script**

```
touch start.cC.compile
time bitbake -c compile -C compile virtual/kernel
touch end.cC.compile
find . -cnewer start.cC.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cC.compile.files.nochange

touch start.cf.compile
time bitbake -c compile -f virtual/kernel
touch end.cf.compile
find . -cnewer start.cf.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cf.compile.files.nochange

diff -u bitbake.cC.compile.files.nochange bitbake.cf.compile.files.nochange > diff.cC.cf.nochange


touch /home/pfefferz/plprj4/mtd_board/build/tmp/work-shared/plnx_aarch64/kernel-source/init/main.c

touch start.cC.compile
time bitbake -c compile -C compile virtual/kernel
touch end.cC.compile
find . -cnewer start.cC.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cC.compile.files.change

touch /home/pfefferz/plprj4/mtd_board/build/tmp/work-shared/plnx_aarch64/kernel-source/init/main.c

touch start.cf.compile
time bitbake -c compile -f virtual/kernel
touch end.cf.compile
find . -cnewer start.cf.compile -printf "%T+\t%p\n" | sort | cut -f2 > bitbake.cf.compile.files.change

diff -u bitbake.cC.compile.files.change bitbake.cf.compile.files.change > diff.cC.cf.change
```

**References**

-   [Free Online HTML Escape / Unescape Tool - FreeFormatter.com](http://www.freeformatter.com/html-escape.html)
    
-   Yocto logo from [link](http://www.yoctoproject.org/wp-content/uploads/2017/08/YoctoProject_StyleGuide.pdf)