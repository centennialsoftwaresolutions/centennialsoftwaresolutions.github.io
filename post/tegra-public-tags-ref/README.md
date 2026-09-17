# tegra-public-dts tag list as of 9:00 PM on 9/16/2026

At https://docs.nvidia.com/jetson/archives/r39.2.1/DeveloperGuide/SD/Kernel/KernelCustomization.html#building-the-jetson-linux-kernel is states:

> The correct release-tag is specified in the release notes. This tag name syncs the sources to the source revision from which the release binary was built.

However @ https://developer.nvidia.com/embedded/jetpack/downloads the tag jetson_39.2.1 isn't listed and its not listed in https://docs.nvidia.com/jetson/archives/r39.2.1/ReleaseNotes/Jetson_Linux_Release_Notes_r39.2.1.pdf

This matters because 
```
demo-user@demo:~/Downloads/Linux_for_Tegra/source$ ./source_sync.sh -k -t jetson_39.2.1_GA
```
Produces:
```
Detecting available git server...
Testing server: https://gitlab.com/nvidia/nv-tegra...
Using git server: https://gitlab.com/nvidia/nv-tegra
Using user provided tag jetson_39.2.1_GA for source sync
Tag is set to jetson_39.2.1_GA
Fetching tag jetson_39.2.1_GA for build/nvidia-public ...
Checking out tag jetson_39.2.1_GA for build/nvidia-public ...
Failed to checkout tag jetson_39.2.1_GA for build/nvidia-public
Fetching tag jetson_39.2.1_GA for dtc-src/1.4.5 ...
Checking out tag jetson_39.2.1_GA for dtc-src/1.4.5 ...
Failed to checkout tag jetson_39.2.1_GA for dtc-src/1.4.5
Fetching tag jetson_39.2.1_GA for hardware/nvidia/t23x/nv-public ...
Checking out tag jetson_39.2.1_GA for hardware/nvidia/t23x/nv-public ...
Failed to checkout tag jetson_39.2.1_GA for hardware/nvidia/t23x/nv-public
Fetching tag jetson_39.2.1_GA for hardware/nvidia/t264/nv-public ...
Checking out tag jetson_39.2.1_GA for hardware/nvidia/t264/nv-public ...
Failed to checkout tag jetson_39.2.1_GA for hardware/nvidia/t264/nv-public
Fetching tag jetson_39.2.1_GA for hardware/nvidia/tegra/nv-public ...
Checking out tag jetson_39.2.1_GA for hardware/nvidia/tegra/nv-public ...
Failed to checkout tag jetson_39.2.1_GA for hardware/nvidia/tegra/nv-public
Fetching tag jetson_39.2.1_GA for hwpm ...
Checking out tag jetson_39.2.1_GA for hwpm ...
Failed to checkout tag jetson_39.2.1_GA for hwpm
Fetching tag jetson_39.2.1_GA for kernel/kernel-noble ...
Checking out tag jetson_39.2.1_GA for kernel/kernel-noble ...
Failed to checkout tag jetson_39.2.1_GA for kernel/kernel-noble
Fetching tag jetson_39.2.1_GA for nvdisplay ...
Checking out tag jetson_39.2.1_GA for nvdisplay ...
Failed to checkout tag jetson_39.2.1_GA for nvdisplay
Fetching tag jetson_39.2.1_GA for nvethernetrm ...
Checking out tag jetson_39.2.1_GA for nvethernetrm ...
Failed to checkout tag jetson_39.2.1_GA for nvethernetrm
Fetching tag jetson_39.2.1_GA for nvgpu ...
Checking out tag jetson_39.2.1_GA for nvgpu ...
Failed to checkout tag jetson_39.2.1_GA for nvgpu
Fetching tag jetson_39.2.1_GA for nvidia-oot ...
Checking out tag jetson_39.2.1_GA for nvidia-oot ...
Failed to checkout tag jetson_39.2.1_GA for nvidia-oot
Fetching tag jetson_39.2.1_GA for unifiedgpudisp ...
Checking out tag jetson_39.2.1_GA for unifiedgpudisp ...
Failed to checkout tag jetson_39.2.1_GA for unifiedgpudisp

```
...but
```
demo-user@demo:~/Downloads/Linux_for_Tegra/source$ ./source_sync.sh -k -t jetson_39.2.1
```
...works.

## Get the tags:
```
git ls-remote --tags https://gitlab.com/nvidia/nv-tegra/device/hardware/nvidia/tegra-public-dts.git
```
## Tags:
```
demo-user@demo:~/Downloads/Linux_for_Tegra/source$ git ls-remote --tags https://gitlab.com/nvidia/nv-tegra/device/hardware/nvidia/tegra-public-dts.git
56c0aa66985867a87444a5cecfc47f509b648d64	refs/tags/IGX_OS-1.1
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/IGX_OS-1.1^{}
f38ededfc0b8567ee7952ca76bceb8bdade92467	refs/tags/IGX_OS-1.1.1
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/IGX_OS-1.1.1^{}
af9c3a0a45d911b0190035345291aa7d3a181fe1	refs/tags/jetson_36.2
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.2^{}
7969d0d0aac3cdc556dcbb18c5e5e818173f4918	refs/tags/jetson_36.3
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.3^{}
a1e009a0fdf19341a81271e08a87bb4cb22baa44	refs/tags/jetson_36.4
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.4^{}
b74f53a13e6c6494c77741b939b113ad989f99af	refs/tags/jetson_36.4.3
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.4.3^{}
0bbc9b54343c6e915764b2410fb3952b58e7d624	refs/tags/jetson_36.4.4
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.4.4^{}
55325ae07ef92fb7856ac1234bee28dd855efb25	refs/tags/jetson_36.4.7
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.4.7^{}
ff3fade0d1fedfaa814188c447466a2699c874ac	refs/tags/jetson_36.5
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.5^{}
9668d7b67fc70c8a2f129d1d52a27d9628944fc7	refs/tags/jetson_36.5.2
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/jetson_36.5.2^{}
002821355847fe512a5a2b542ad9deb30d4a65a9	refs/tags/jetson_38.2
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/jetson_38.2^{}
57437cccc845e5a7e5f9c97a341446f71a0e55f4	refs/tags/jetson_38.2.1
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/jetson_38.2.1^{}
715460ff552909ec985a25990a18b47baf3c388d	refs/tags/jetson_38.2.2
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/jetson_38.2.2^{}
69c59c73082f40711c2c540752b7946390e38e04	refs/tags/jetson_38.4
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/jetson_38.4^{}
62fe46d950f77279d12f9d7596e9d257f1715c68	refs/tags/jetson_39.2.0
d76c3a7751ea75592413b42c984eac7084a99592	refs/tags/jetson_39.2.0^{}
80b5ad44f9da92d320f98e940d4340fde73f5c77	refs/tags/jetson_39.2.1
d76c3a7751ea75592413b42c984eac7084a99592	refs/tags/jetson_39.2.1^{}
39730e9408e2891b086335e069d58c7f2ba77c11	refs/tags/jetson_39.2_GA
d76c3a7751ea75592413b42c984eac7084a99592	refs/tags/jetson_39.2_GA^{}
99f8143bb2daae3e04aa326f2296824ccaaf273a	refs/tags/l4t-l4t-r36.3.1_eng_2024-05-29
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.3.1_eng_2024-05-29^{}
123cf701b588e8e690c87472d99838f1bc4824ef	refs/tags/l4t-l4t-r36.3_eng_2024-04-24
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.3_eng_2024-04-24^{}
1670ca6228b759be3e43385bd93c157444e3075e	refs/tags/l4t-l4t-r36.4.1_eng_2025-01-08
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4.1_eng_2025-01-08^{}
dc68cb652139a692fcfa926e0fe18f41f9df1fe0	refs/tags/l4t-l4t-r36.4.1_eng_2025-09-19
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4.1_eng_2025-09-19^{}
3b26c66de0f47328d5ce3bfc43e4bf10134fc93c	refs/tags/l4t-l4t-r36.4.4_eng_2025-04-02
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4.4_eng_2025-04-02^{}
0dc7d531f80025bf876fb1c6b6af8a3b40c84deb	refs/tags/l4t-l4t-r36.4.4_eng_2025-06-03
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4.4_eng_2025-06-03^{}
d40bf13ba4e1fbb88a74e59b26a73d6f0dde89f0	refs/tags/l4t-l4t-r36.4.4_eng_2025-09-23
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4.4_eng_2025-09-23^{}
0d68f6a7a340ae37c424f22328d5dfdf0b7603b3	refs/tags/l4t-l4t-r36.4_eng_2024-09-12
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/l4t-l4t-r36.4_eng_2024-09-12^{}
72342202fc5aac3d13e5ceda279b9be11bc1c56e	refs/tags/rel-36_eng_2023-10-04
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2023-10-04^{}
01e0002b7ff442e2948996f24f2f620c060432ba	refs/tags/rel-36_eng_2023-11-07
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2023-11-07^{}
0624316d67ed09321dd37da50df0a8dfb1ef8a3e	refs/tags/rel-36_eng_2023-12-04
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2023-12-04^{}
71d046ea2bafeab5f96a90ff7390d6d4ee3a4ce2	refs/tags/rel-36_eng_2023-12-12
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2023-12-12^{}
1cabbcce468748ee1eb0f996d676893e1e0ad677	refs/tags/rel-36_eng_2024-01-03
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-01-03^{}
b60ddce0614e2f39c23318888bae219942a45ecb	refs/tags/rel-36_eng_2024-01-12
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-01-12^{}
fde21bee01329537d6b4d81e43bbb78458dd93c3	refs/tags/rel-36_eng_2024-01-24
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-01-24^{}
28b62f32076ac49143f3253880a2a938408a179c	refs/tags/rel-36_eng_2024-02-05
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-02-05^{}
2c7586244b14ac85b28e568a7f7ec03f655adbc5	refs/tags/rel-36_eng_2024-02-27
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-02-27^{}
6b0b23c7ccf3c1262a7866d8f2f09d3e1fde367f	refs/tags/rel-36_eng_2024-03-06
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-03-06^{}
bac8b5683cb72a67e552259cf0a43a60a1341fb5	refs/tags/rel-36_eng_2024-03-14
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-03-14^{}
411d25ad4224c319a90dc766e2469ce1fceb5b03	refs/tags/rel-36_eng_2024-04-04
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-04-04^{}
98d0564af09334490e12f7c2741814d2d71bcbeb	refs/tags/rel-36_eng_2024-06-13
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-06-13^{}
f066c050a57ba49dde751028832fa17de427bd32	refs/tags/rel-36_eng_2024-06-26
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-06-26^{}
ebf4c599a415482fea822ba2fd5f5787e2406cc5	refs/tags/rel-36_eng_2024-07-08
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-07-08^{}
fd9e409dae283ca1786806fbc287d109f76645bf	refs/tags/rel-36_eng_2024-07-23
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-07-23^{}
88b3674890b542b124a471b2f5c6f6f77556501e	refs/tags/rel-36_eng_2024-08-29
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-08-29^{}
bb475fcbe60aed366451f15c4173e716a2bfa02a	refs/tags/rel-36_eng_2024-10-24
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2024-10-24^{}
21842de6097219d1e3f4cc57f17c399ad073c06e	refs/tags/rel-36_eng_2025-02-28
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2025-02-28^{}
3f5419e8a4216491901c5e542f90603badf6e70f	refs/tags/rel-36_eng_2025-12-11
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2025-12-11^{}
ab947538319950056a029ced83fd26b5b58e61b9	refs/tags/rel-36_eng_2026-01-04
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_eng_2026-01-04^{}
37ee73b994c262094b0a3eaeb33ec906922c2083	refs/tags/rel-36_lws2_eng_2025-09-23
8ba5d53ef1e1753f9f2a5b1f7b7b5fc5039de68e	refs/tags/rel-36_lws2_eng_2025-09-23^{}
c7a4178fdb42f507105281b99c2244be182d7503	refs/tags/rel-38_2026-01-05
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_2026-01-05^{}
97fc1d1792bfc180d4faaca8b9fbd790cfc99673	refs/tags/rel-38_2026-02-03
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_2026-02-03^{}
a16dd6a6434d4f29d029d73bacea2d221a5decfa	refs/tags/rel-38_eng_2025-10-06
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_eng_2025-10-06^{}
50bbafb539775d881f73ec582dce52216924da4e	refs/tags/rel-38_eng_2025-11-12
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_eng_2025-11-12^{}
81e211e2cdb04f5261a543a4087e9622494b1d48	refs/tags/rel-38_eng_2025-11-25
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_eng_2025-11-25^{}
5b6f39d2b5b5353f95d2c0f969b10984d311c43a	refs/tags/rel-38_eng_2025-12-05
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_eng_2025-12-05^{}
3725ec2413efc0424c5a4ba1206bee7d920dd241	refs/tags/rel-38_eng_2025-12-16
2101ccc1b1ef8267e63286332aed34891943c7c7	refs/tags/rel-38_eng_2025-12-16^{}
```

A bug was filed @ https://developer.nvidia.com/bugs/6791794
