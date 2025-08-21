# Grab Bag of TCP/IP Socket Create Code, Implicit Make Debug and Finding Include Paths

![gnu_logo_1](gnu_logo_1.png)

This post presents code to open and close a TCP/IP socket, a command to make it, method to find **include files**, commands to browse references, a command to see how the compiler was configured and a command to print implicit Make rules.

**Distro**

Ubuntu 16.04.3

**Open and Close a Socket**

/* File socket.c */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <sys/socket.h>  /* socket(),[ #define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) PF_INET,[ #define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) SOCK_STREAM */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <netinet/in.h>   /* IPPROTO_TCP */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <stdio.h>      /* fprintf (), stderr */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <string.h>      /* strerror() */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <errno.h>      /* errno */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <stdlib.h>      /* exit(),[ #define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) EXIT_FAILURE */

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <unistd.h>      /* close() */

int main(int argc, char *argv[])

{

​    int s;

​    s = socket(PF_INET, SOCK_STREAM, IPPROTO_TCP);

​    if (s == -1) {

​        fprintf(stderr, "error opening socket: %s\n", strerror(errno));

​        exit(EXIT_FAILURE);

​    }

​    close(s);

}

**Make With Implicit Rules**

make socket

**Enable cscope to Browse Code**

See steps at[ http://www.zachpfeffer.com/single-post/cscopevim](http://www.zachpfeffer.com/single-post/cscopevim).

**Run CC Verbose to See Configuration**

**Note**

This allows you to see what paths are searched with you type[ #include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <...> or[ #include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) "..."

**Command**

touch socket.c; CFLAGS=-v make socket

**Output:**

cc -v  socket.c  -o socket

Using built-in specs.

COLLECT_GCC=cc

COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper

Target: x86_64-linux-gnu

Configured with: ../src/configure -v --with-pkgversion='Ubuntu 5.4.0-6ubuntu1~16.04.10' --with-bugurl=file:///usr/share/doc/gcc-5/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-5 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-5-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-5-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-5-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu

Thread model: posix

gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.10)

COLLECT_GCC_OPTIONS='-v' '-o' 'socket' '-mtune=generic' '-march=x86-64'

/usr/lib/gcc/x86_64-linux-gnu/5/cc1 -quiet -v -imultiarch x86_64-linux-gnu socket.c -quiet -dumpbase socket.c -mtune=generic -march=x86-64 -auxbase socket -version -fstack-protector-strong -Wformat -Wformat-security -o /tmp/ccPtW1Pm.s

GNU C11 (Ubuntu 5.4.0-6ubuntu1~16.04.10) version 5.4.0 20160609 (x86_64-linux-gnu)

​	compiled by GNU C version 5.4.0 20160609, GMP version 6.1.0, MPFR version 3.1.4, MPC version 1.0.3

GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072

ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"

ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/5/../../../../x86_64-linux-gnu/include"

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) "..." search starts here:

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <...> search starts here:

**/usr/lib/gcc/x86_64-linux-gnu/5/include**

**/usr/local/include**

**/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed**

**/usr/include/x86_64-linux-gnu**

**/usr/include**

End of search list.

GNU C11 (Ubuntu 5.4.0-6ubuntu1~16.04.10) version 5.4.0 20160609 (x86_64-linux-gnu)

​	compiled by GNU C version 5.4.0 20160609, GMP version 6.1.0, MPFR version 3.1.4, MPC version 1.0.3

GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072

Compiler executable checksum: bab7da148afbe213714f0f38814b36b0

COLLECT_GCC_OPTIONS='-v' '-o' 'socket' '-mtune=generic' '-march=x86-64'

as -v --64 -o /tmp/ccV4JGKf.o /tmp/ccPtW1Pm.s

GNU assembler version 2.26.1 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.26.1

COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/5/:/usr/lib/gcc/x86_64-linux-gnu/5/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/5/:/usr/lib/gcc/x86_64-linux-gnu/

LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/5/:/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/5/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/5/../../../:/lib/:/usr/lib/

COLLECT_GCC_OPTIONS='-v' '-o' 'socket' '-mtune=generic' '-march=x86-64'

/usr/lib/gcc/x86_64-linux-gnu/5/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/5/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper -plugin-opt=-fresolution=/tmp/ccFWgdJ8.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --sysroot=/ --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro -o socket /usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/5/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/5 -L/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/5/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/5/../../.. /tmp/ccV4JGKf.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/5/crtend.o /usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crtn.o

**Generate cscope.files**

rm cscope.files

find /usr/lib/gcc/x86_64-linux-gnu/5/include >> cscope.files

find /usr/local/include >> cscope.files

find /usr/lib/gcc/x86_64-linux-gnu/5/include-fixed >> cscope.files

find /usr/include/x86_64-linux-gnu >> cscope.files

find /usr/include >> cscope.files

find ./ -name *.[chxsS] >> cscope.files

cscope -b

**Full Path to Each Header**

**Include Paths**

/usr/lib/gcc/x86_64-linux-gnu/5/include

/usr/local/include

/usr/lib/gcc/x86_64-linux-gnu/5/include-fixed

/usr/include/x86_64-linux-gnu

/usr/include

**Headers**

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <sys/socket.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <netinet/in.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <stdio.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <string.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <errno.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <stdlib.h>

[#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) <unistd.h>

**Find**

find /usr/lib/gcc/x86_64-linux-gnu/5/include /usr/local/include /usr/lib/gcc/x86_64-linux-gnu/5/include-fixed /usr/include/x86_64-linux-gnu /usr/include -path */sys/socket.h -or -path */netinet/in.h

**Output:**

/usr/include/x86_64-linux-gnu/sys/socket.h

/usr/include/netinet/in.h

**Find**

find /usr/lib/gcc/x86_64-linux-gnu/5/include /usr/local/include /usr/lib/gcc/x86_64-linux-gnu/5/include-fixed /usr/include/x86_64-linux-gnu /usr/include -maxdepth 1 -name stdio.h -or -name string.h -or -name errno.h -or -name stdlib.h -or -name unistd.h

**Output:**

/usr/include/stdio.h

/usr/include/errno.h

/usr/include/string.h

/usr/include/stdlib.h

**Make Verbose**

touch socket.c; make --debug=v socket

**Output:**

GNU Make 4.1

Built for x86_64-pc-linux-gnu

Copyright (C) 1988-2014 Free Software Foundation, Inc.

License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software: you are free to change and redistribute it.

There is NO WARRANTY, to the extent permitted by law.

Reading makefiles...

Updating goal targets....

Considering target file 'socket'.

 Considering target file 'socket.c'.

 Finished prerequisites of target file 'socket.c'.

 No need to remake target 'socket.c'.

Finished prerequisites of target file 'socket'.

Prerequisite 'socket.c' is newer than target 'socket'.

Must remake target 'socket'.

cc   socket.c  -o socket

Successfully remade target file 'socket'.

**Print Implicit Rules**

make -p -f /dev/null

-p, --print-data-base    Print make's internal database.

-f FILE, --file=FILE, --makefile=FILE

​               Read FILE as a makefile.

**Excerpts:**

\# default

COMPILE.cc = $(CXX) $(CXXFLAGS) $(CPPFLAGS) $(TARGET_ARCH) -c

\# default

COMPILE.C = $(COMPILE.cc)

\# default

OUTPUT_OPTION = -o $@

*$@ The file name of the target of the rule*

\# Not a target:

.c.o:

\# Builtin rule

\# Implicit rule search has not been done.

\# Modification time never checked.

\# File has not been updated.

\# recipe to execute (built-in):

​    $(COMPILE.c) $(OUTPUT_OPTION) $<

*$< The name of the first prerequisite*

**References**

- **Using Cscope on large projects (example: the Linux kernel)** at [[link](http://cscope.sourceforge.net/large_projects.html)]
- **GNU Make: A Program for Directed Recompilation: for GNU Make Version 3.79.1**, Richard Stallman - Roland McGrath - Paul D.Smith - GNU Press - 2004, ISBN 1-882114-81-7,[[Amazon](https://www.amazon.com/GNU-Make-Program-Directed-Compilation/dp/1882114825)]
- GNU image from [[link](https://en.wikipedia.org/wiki/GNU_Project)]