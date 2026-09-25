Docker build file to create an image that can be used to build
MiSTer cores on Apple Silicon Macs.

Key difference is the adm/qenv.sh script to remove the check for
SSE instruction support which is there when using Rosetta.

To use, call `quartus_sh --flow compile <core>.qpf`

quartus_sh is a shell script that uses Apple container to run
the Linux amd64 environment needed.

``` shell
container run -a amd64 -m 8G -c 4 --rm -it -v .:/build -w /build quartus \
    /opt/intelFPGA_lite/quartus/bin/quartus_sh $*
```
