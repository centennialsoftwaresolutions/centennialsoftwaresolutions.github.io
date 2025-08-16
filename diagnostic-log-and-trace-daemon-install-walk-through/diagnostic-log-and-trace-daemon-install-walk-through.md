# Diagnostic Log and Trace Daemon Install and Smoke Test Walk Through

![genivi_logo](genivi_logo.png)

This post walks through installing the dlt-daemon on Ubuntu 16.04.2 and smoke testing it.

**Install**

**1.** Install the dependencies

Open a terminal and type:

```
sudo apt-get update
sudo apt-get install cmake zlib1g-dev libdbus-glib-1-dev
```

Type 'Y' when prompted.

**2.** Clone the source

```
git clone https://github.com/GENIVI/dlt-daemon.git
```

**3.** Build it

Run these commands:

```
cd dlt-daemon/
mkdir build
cd build
cmake ..
make
optional: sudo make install
optional: sudo ldconfig
```

Command output

Output from **cmake ..**

```
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Build type not defined. Using default build type 'RelWithDebInfo'.
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found ZLIB: /usr/lib/x86_64-linux-gnu/libz.so (found version "1.2.8") 
-- Found PkgConfig: /usr/bin/pkg-config (found version "0.29.1") 
-- Checking for module 'dbus-1'
--   Found dbus-1, version 1.10.6
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- Looking for include file arpa/inet.h
-- Looking for include file arpa/inet.h - found
-- Looking for include file fcntl.h
-- Looking for include file fcntl.h - found
-- Looking for include file float.h
-- Looking for include file float.h - found
-- Looking for include file limits.h
-- Looking for include file limits.h - found
-- Looking for include file netdb.h
-- Looking for include file netdb.h - found
-- Looking for include file netinet/in.h
-- Looking for include file netinet/in.h - found
-- Looking for include file stdlib.h
-- Looking for include file stdlib.h - found
-- Looking for include file string.h
-- Looking for include file string.h - found
-- Looking for include file strings.h
-- Looking for include file strings.h - found
-- Looking for include file sys/ioctl.h
-- Looking for include file sys/ioctl.h - found
-- Looking for include file sys/socket.h
-- Looking for include file sys/socket.h - found
-- Looking for include file sys/time.h
-- Looking for include file sys/time.h - found
-- Looking for include file unistd.h
-- Looking for include file unistd.h - found
-- Looking for include file sys/ipc.h
-- Looking for include file sys/ipc.h - found
-- Looking for include file ctype.h
-- Looking for include file ctype.h - found
-- Looking for include file signal.h
-- Looking for include file signal.h - found
-- Looking for include file syslog.h
-- Looking for include file syslog.h - found
-- Looking for include file sys/stat.h
-- Looking for include file sys/stat.h - found
-- Looking for include file linux/stat.h
-- Looking for include file linux/stat.h - found
-- Looking for include file sys/uio.h
-- Looking for include file sys/uio.h - found
-- Looking for include file termios.h
-- Looking for include file termios.h - found
-- Looking for bzero
-- Looking for bzero - found
-- Looking for clock_gettime
-- Looking for clock_gettime - found
-- Looking for floor
-- Looking for floor - not found
-- Looking for fork
-- Looking for fork - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for gettimeofday
-- Looking for gettimeofday - found
-- Looking for inet_ntoa
-- Looking for inet_ntoa - found
-- Looking for malloc
-- Looking for malloc - found
-- Looking for memmove
-- Looking for memmove - found
-- Looking for memset
-- Looking for memset - found
-- Looking for mkfifo
-- Looking for mkfifo - found
-- Looking for select
-- Looking for select - found
-- Looking for socket
-- Looking for socket - found
-- Looking for strchr
-- Looking for strchr - found
-- Looking for strerror
-- Looking for strerror - found
-- Looking for strstr
-- Looking for strstr - found
-- Looking for strtol
-- Looking for strtol - found
-- 
-- -------------------------------------------------------------------------------
-- Build for Version 2.17.0 build v2.17.0_6_g90c8b5b version state STABLE
-- WITH_SYSTEMD = OFF
-- WITH_SYSTEMD_WATCHDOG = OFF
-- WITH_SYSTEMD_JOURNAL = OFF
-- WITH_DOC = OFF
-- WITH_MAN = ON
-- WITH_DLT_ADAPTOR = ON
-- WITH_DLT_CONSOLE = ON
-- WITH_DLT_EXAMPLES = ON
-- WITH_DLT_SYSTEM = ON
-- WITH_DLT_DBUS = ON
-- WITH_DLT_TESTS = ON
-- WITH_DLT_UNIT_TESTS = OFF
-- WITH_DLT_SHM_ENABLE = OFF
-- WITH_DLTTEST = OFF
-- WITH_DLT_CXX11_EXT = OFF
-- WITH_DLT_COREDUMPHANDLER = OFF
-- WITH_DLT_KPI = ON
-- WITH_CHECK_CONFIG_FILE = OFF
-- WITH_TESTSCRIPTS = OFF
-- WITH_GPROF = OFF
-- WITH_DLT_USE_IPv6 = ON
-- DLT_USER = genivi
-- BUILD_SHARED_LIBS = ON
-- TARGET_CPU_NAME = 
-- CMAKE_INSTALL_PREFIX = /usr/local
-- CMAKE_BUILD_TYPE = RelWithDebInfo
-- CMAKE_HOST_SYSTEM_PROCESSOR = x86_64
-- CMAKE_SYSTEM_PROCESSOR = x86_64
-- WITH_DLT_LOGSTORAGE_CTRL_UDEV = OFF
-- WITH_DLT_LOGSTORAGE_CTRL_PROP = OFF
-- Change a value with: cmake -D<Variable>=<Value>
-- -------------------------------------------------------------------------------
-- 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/pfefferz/dlt-daemon/build
```

Output from **make**

```
Scanning dependencies of target compress_man
[  0%] Built target compress_man
Scanning dependencies of target dlt
[  1%] Building C object src/lib/CMakeFiles/dlt.dir/dlt_user.c.o
[  2%] Building C object src/lib/CMakeFiles/dlt.dir/dlt_client.c.o
[  3%] Building C object src/lib/CMakeFiles/dlt.dir/dlt_filetransfer.c.o
[  4%] Building C object src/lib/CMakeFiles/dlt.dir/dlt_env_ll.c.o
[  5%] Building C object src/lib/CMakeFiles/dlt.dir/__/shared/dlt_common.c.o
[  6%] Building C object src/lib/CMakeFiles/dlt.dir/__/shared/dlt_user_shared.c.o
[  7%] Building C object src/lib/CMakeFiles/dlt.dir/__/shared/dlt_shm.c.o
[  8%] Linking C shared library libdlt.so
[  8%] Built target dlt
Scanning dependencies of target dlt-daemon
[  9%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt-daemon.c.o
[ 10%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_common.c.o
[ 11%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_connection.c.o
[ 12%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_event_handler.c.o
[ 13%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/gateway/dlt_gateway.c.o
[ 14%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_socket.c.o
[ 15%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_unix_socket.c.o
[ 16%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_serial.c.o
[ 17%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_client.c.o
[ 18%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/dlt_daemon_offline_logstorage.c.o
[ 19%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/shared/dlt_user_shared.c.o
[ 20%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/shared/dlt_common.c.o
[ 21%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/shared/dlt_shm.c.o
[ 22%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/shared/dlt_offline_trace.c.o
[ 23%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/offlinelogstorage/dlt_offline_logstorage.c.o
[ 25%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/lib/dlt_client.c.o
[ 26%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/shared/dlt_config_file_parser.c.o
[ 27%] Building C object src/daemon/CMakeFiles/dlt-daemon.dir/__/offlinelogstorage/dlt_offline_logstorage_behavior.c.o
[ 28%] Linking C executable dlt-daemon
[ 28%] Built target dlt-daemon
Scanning dependencies of target dlt-convert
[ 29%] Building C object src/console/CMakeFiles/dlt-convert.dir/dlt-convert.c.o
[ 30%] Linking C executable dlt-convert
[ 30%] Built target dlt-convert
Scanning dependencies of target dlt-control
[ 31%] Building C object src/console/CMakeFiles/dlt-control.dir/dlt-control.c.o
[ 32%] Building C object src/console/CMakeFiles/dlt-control.dir/dlt-control-common.c.o
[ 33%] Linking C executable dlt-control
[ 33%] Built target dlt-control
Scanning dependencies of target dlt-receive
[ 34%] Building C object src/console/CMakeFiles/dlt-receive.dir/dlt-receive.c.o
[ 35%] Linking C executable dlt-receive
[ 35%] Built target dlt-receive
Scanning dependencies of target dlt-passive-node-ctrl
[ 36%] Building C object src/console/CMakeFiles/dlt-passive-node-ctrl.dir/dlt-passive-node-ctrl.c.o
[ 37%] Building C object src/console/CMakeFiles/dlt-passive-node-ctrl.dir/dlt-control-common.c.o
[ 38%] Linking C executable dlt-passive-node-ctrl
[ 38%] Built target dlt-passive-node-ctrl
Scanning dependencies of target dlt-logstorage-ctrl
[ 39%] Building C object src/console/logstorage/CMakeFiles/dlt-logstorage-ctrl.dir/dlt-logstorage-ctrl.c.o
[ 40%] Building C object src/console/logstorage/CMakeFiles/dlt-logstorage-ctrl.dir/dlt-logstorage-common.c.o
[ 41%] Building C object src/console/logstorage/CMakeFiles/dlt-logstorage-ctrl.dir/dlt-logstorage-list.c.o
[ 42%] Building C object src/console/logstorage/CMakeFiles/dlt-logstorage-ctrl.dir/__/dlt-control-common.c.o
[ 43%] Building C object src/console/logstorage/CMakeFiles/dlt-logstorage-ctrl.dir/__/__/__/systemd/3rdparty/sd-daemon.c.o
[ 44%] Linking C executable dlt-logstorage-ctrl
[ 44%] Built target dlt-logstorage-ctrl
Scanning dependencies of target dlt-example-user
[ 45%] Building C object src/examples/CMakeFiles/dlt-example-user.dir/dlt-example-user.c.o
[ 46%] Linking C executable dlt-example-user
[ 46%] Built target dlt-example-user
Scanning dependencies of target dlt-example-filetransfer
[ 47%] Building C object src/examples/CMakeFiles/dlt-example-filetransfer.dir/dlt-example-filetransfer.c.o
[ 48%] Linking C executable dlt-example-filetransfer
[ 48%] Built target dlt-example-filetransfer
Scanning dependencies of target dlt-example-user-common-api
[ 50%] Building C object src/examples/CMakeFiles/dlt-example-user-common-api.dir/dlt-example-user-common-api.c.o
[ 51%] Linking C executable dlt-example-user-common-api
[ 51%] Built target dlt-example-user-common-api
Scanning dependencies of target dlt-example-user-func
[ 52%] Building C object src/examples/CMakeFiles/dlt-example-user-func.dir/dlt-example-user-func.c.o
[ 53%] Linking C executable dlt-example-user-func
[ 53%] Built target dlt-example-user-func
Scanning dependencies of target dlt-adaptor-stdin
[ 54%] Building C object src/adaptor/CMakeFiles/dlt-adaptor-stdin.dir/dlt-adaptor-stdin.c.o
[ 55%] Linking C executable dlt-adaptor-stdin
[ 55%] Built target dlt-adaptor-stdin
Scanning dependencies of target dlt-adaptor-udp
[ 56%] Building C object src/adaptor/CMakeFiles/dlt-adaptor-udp.dir/dlt-adaptor-udp.c.o
[ 57%] Linking C executable dlt-adaptor-udp
[ 57%] Built target dlt-adaptor-udp
Scanning dependencies of target dlt-test-user
[ 58%] Building C object src/tests/CMakeFiles/dlt-test-user.dir/dlt-test-user.c.o
[ 59%] Linking C executable dlt-test-user
[ 59%] Built target dlt-test-user
Scanning dependencies of target dlt-test-init-free
[ 60%] Building C object src/tests/CMakeFiles/dlt-test-init-free.dir/dlt-test-init-free.c.o
[ 61%] Linking C executable dlt-test-init-free
[ 61%] Built target dlt-test-init-free
Scanning dependencies of target dlt-test-multi-process
[ 62%] Building C object src/tests/CMakeFiles/dlt-test-multi-process.dir/dlt-test-multi-process.c.o
[ 63%] Linking C executable dlt-test-multi-process
[ 63%] Built target dlt-test-multi-process
Scanning dependencies of target dlt-test-stress-user
[ 64%] Building C object src/tests/CMakeFiles/dlt-test-stress-user.dir/dlt-test-stress-user.c.o
[ 65%] Linking C executable dlt-test-stress-user
[ 65%] Built target dlt-test-stress-user
Scanning dependencies of target dlt-test-client
[ 66%] Building C object src/tests/CMakeFiles/dlt-test-client.dir/dlt-test-client.c.o
[ 67%] Linking C executable dlt-test-client
[ 67%] Built target dlt-test-client
Scanning dependencies of target dlt-test-stress-client
[ 68%] Building C object src/tests/CMakeFiles/dlt-test-stress-client.dir/dlt-test-stress-client.c.o
[ 69%] Linking C executable dlt-test-stress-client
[ 69%] Built target dlt-test-stress-client
Scanning dependencies of target dlt-test-multi-process-client
[ 70%] Building C object src/tests/CMakeFiles/dlt-test-multi-process-client.dir/dlt-test-multi-process-client.c.o
[ 71%] Linking C executable dlt-test-multi-process-client
[ 71%] Built target dlt-test-multi-process-client
Scanning dependencies of target dlt-test-stress
[ 72%] Building C object src/tests/CMakeFiles/dlt-test-stress.dir/dlt-test-stress.c.o
[ 73%] Linking C executable dlt-test-stress
[ 73%] Built target dlt-test-stress
Scanning dependencies of target dlt-test-filetransfer
[ 75%] Building C object src/tests/CMakeFiles/dlt-test-filetransfer.dir/dlt-test-filetransfer.c.o
[ 76%] Linking C executable dlt-test-filetransfer
[ 76%] Built target dlt-test-filetransfer
Scanning dependencies of target dlt-test-fork-handler
[ 77%] Building C object src/tests/CMakeFiles/dlt-test-fork-handler.dir/dlt-test-fork-handler.c.o
[ 78%] Linking C executable dlt-test-fork-handler
[ 78%] Built target dlt-test-fork-handler
Scanning dependencies of target dlt-system
[ 79%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system.c.o
[ 80%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-options.c.o
[ 81%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-process-handling.c.o
[ 82%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-filetransfer.c.o
[ 83%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-logfile.c.o
[ 84%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-processes.c.o
[ 85%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-shell.c.o
[ 86%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-syslog.c.o
[ 87%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-watchdog.c.o
[ 88%] Building C object src/system/CMakeFiles/dlt-system.dir/dlt-system-journal.c.o
[ 89%] Linking C executable dlt-system
[ 89%] Built target dlt-system
Scanning dependencies of target dlt-dbus
[ 90%] Building C object src/dbus/CMakeFiles/dlt-dbus.dir/dlt-dbus.c.o
[ 91%] Building C object src/dbus/CMakeFiles/dlt-dbus.dir/dlt-dbus-options.c.o
[ 92%] Linking C executable dlt-dbus
[ 92%] Built target dlt-dbus
Scanning dependencies of target dlt-kpi
[ 93%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi.c.o
[ 94%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi-options.c.o
[ 95%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi-process.c.o
[ 96%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi-process-list.c.o
[ 97%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi-common.c.o
[ 98%] Building C object src/kpi/CMakeFiles/dlt-kpi.dir/dlt-kpi-interrupt.c.o
[100%] Linking C executable dlt-kpi
[100%] Built target dlt-kpi
```

Output from **sudo make install**

```
[  0%] Built target compress_man
[  8%] Built target dlt
[ 28%] Built target dlt-daemon
[ 30%] Built target dlt-convert
[ 33%] Built target dlt-control
[ 35%] Built target dlt-receive
[ 38%] Built target dlt-passive-node-ctrl
[ 44%] Built target dlt-logstorage-ctrl
[ 46%] Built target dlt-example-user
[ 48%] Built target dlt-example-filetransfer
[ 51%] Built target dlt-example-user-common-api
[ 53%] Built target dlt-example-user-func
[ 55%] Built target dlt-adaptor-stdin
[ 57%] Built target dlt-adaptor-udp
[ 59%] Built target dlt-test-user
[ 61%] Built target dlt-test-init-free
[ 63%] Built target dlt-test-multi-process
[ 65%] Built target dlt-test-stress-user
[ 67%] Built target dlt-test-client
[ 69%] Built target dlt-test-stress-client
[ 71%] Built target dlt-test-multi-process-client
[ 73%] Built target dlt-test-stress
[ 76%] Built target dlt-test-filetransfer
[ 78%] Built target dlt-test-fork-handler
[ 89%] Built target dlt-system
[ 92%] Built target dlt-dbus
[100%] Built target dlt-kpi
Install the project...
-- Install configuration: "RelWithDebInfo"
-- Installing: /usr/local/lib/pkgconfig/automotive-dlt.pc
-- Installing: /usr/local/share/man/man5/dlt.conf.5.gz
-- Installing: /usr/local/share/man/man5/dlt-system.conf.5.gz
-- Installing: /usr/local/share/man/man1/dlt-convert.1.gz
-- Installing: /usr/local/share/man/man1/dlt-daemon.1.gz
-- Installing: /usr/local/share/man/man1/dlt-receive.1.gz
-- Installing: /usr/local/share/man/man1/dlt-system.1.gz
-- Installing: /usr/local/share/man/man1/dlt-logstorage-ctrl.1.gz
-- Installing: /usr/local/share/man/man1/dlt-passive-node-ctrl.1.gz
-- Installing: /usr/local/lib/libdlt.so.2.17.0
-- Installing: /usr/local/lib/libdlt.so.2
-- Installing: /usr/local/lib/libdlt.so
-- Installing: /usr/local/bin/dlt-daemon
-- Installing: /usr/local/etc/dlt.conf
-- Installing: /usr/local/etc/dlt_gateway.conf
-- Installing: /usr/local/bin/dlt-convert
-- Set runtime path of "/usr/local/bin/dlt-convert" to ""
-- Installing: /usr/local/bin/dlt-receive
-- Set runtime path of "/usr/local/bin/dlt-receive" to ""
-- Installing: /usr/local/bin/dlt-control
-- Set runtime path of "/usr/local/bin/dlt-control" to ""
-- Installing: /usr/local/bin/dlt-passive-node-ctrl
-- Set runtime path of "/usr/local/bin/dlt-passive-node-ctrl" to ""
-- Installing: /usr/local/bin/dlt-logstorage-ctrl
-- Set runtime path of "/usr/local/bin/dlt-logstorage-ctrl" to ""
-- Installing: /usr/local/bin/dlt-example-user
-- Set runtime path of "/usr/local/bin/dlt-example-user" to ""
-- Installing: /usr/local/bin/dlt-example-user-func
-- Set runtime path of "/usr/local/bin/dlt-example-user-func" to ""
-- Installing: /usr/local/bin/dlt-example-user-common-api
-- Set runtime path of "/usr/local/bin/dlt-example-user-common-api" to ""
-- Installing: /usr/local/bin/dlt-example-filetransfer
-- Set runtime path of "/usr/local/bin/dlt-example-filetransfer" to ""
-- Installing: /usr/local/bin/dlt-adaptor-stdin
-- Set runtime path of "/usr/local/bin/dlt-adaptor-stdin" to ""
-- Installing: /usr/local/bin/dlt-adaptor-udp
-- Set runtime path of "/usr/local/bin/dlt-adaptor-udp" to ""
-- Installing: /usr/local/bin/dlt-test-multi-process
-- Set runtime path of "/usr/local/bin/dlt-test-multi-process" to ""
-- Installing: /usr/local/bin/dlt-test-multi-process-client
-- Set runtime path of "/usr/local/bin/dlt-test-multi-process-client" to ""
-- Installing: /usr/local/bin/dlt-test-user
-- Set runtime path of "/usr/local/bin/dlt-test-user" to ""
-- Installing: /usr/local/bin/dlt-test-client
-- Set runtime path of "/usr/local/bin/dlt-test-client" to ""
-- Installing: /usr/local/bin/dlt-test-stress-user
-- Set runtime path of "/usr/local/bin/dlt-test-stress-user" to ""
-- Installing: /usr/local/bin/dlt-test-stress-client
-- Set runtime path of "/usr/local/bin/dlt-test-stress-client" to ""
-- Installing: /usr/local/bin/dlt-test-stress
-- Set runtime path of "/usr/local/bin/dlt-test-stress" to ""
-- Installing: /usr/local/bin/dlt-test-filetransfer
-- Set runtime path of "/usr/local/bin/dlt-test-filetransfer" to ""
-- Installing: /usr/local/bin/dlt-test-fork-handler
-- Set runtime path of "/usr/local/bin/dlt-test-fork-handler" to ""
-- Installing: /usr/local/bin/dlt-test-init-free
-- Set runtime path of "/usr/local/bin/dlt-test-init-free" to ""
-- Installing: /usr/local/share/dlt-filetransfer/dlt-test-filetransfer-file
-- Installing: /usr/local/share/dlt-filetransfer/dlt-test-filetransfer-image.png
-- Installing: /usr/local/bin/dlt-system
-- Set runtime path of "/usr/local/bin/dlt-system" to ""
-- Installing: /usr/local/etc/dlt-system.conf
-- Installing: /usr/local/bin/dlt-dbus
-- Set runtime path of "/usr/local/bin/dlt-dbus" to ""
-- Installing: /usr/local/etc/dlt-dbus.conf
-- Installing: /usr/local/bin/dlt-kpi
-- Set runtime path of "/usr/local/bin/dlt-kpi" to ""
-- Installing: /usr/local/etc/dlt-kpi.conf
-- Installing: /usr/local/include/dlt/dlt.h
-- Installing: /usr/local/include/dlt/dlt_user.h
-- Installing: /usr/local/include/dlt/dlt_user_macros.h
-- Installing: /usr/local/include/dlt/dlt_client.h
-- Installing: /usr/local/include/dlt/dlt_protocol.h
-- Installing: /usr/local/include/dlt/dlt_common.h
-- Installing: /usr/local/include/dlt/dlt_types.h
-- Installing: /usr/local/include/dlt/dlt_version.h
-- Installing: /usr/local/include/dlt/dlt_shm.h
-- Installing: /usr/local/include/dlt/dlt_offline_trace.h
-- Installing: /usr/local/include/dlt/dlt_filetransfer.h
-- Installing: /usr/local/include/dlt/dlt_common_api.h
```

Output from **sudo ldconfig**

None

Output from **sudo ldconfig -v** (verbose option)

```
/sbin/ldconfig.real: Can't stat /lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Can't stat /usr/lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/usr/lib/x86_64-linux-gnu/libfakeroot:
	libfakeroot-0.so -> libfakeroot-tcp.so
/lib/i386-linux-gnu:
	libmemusage.so -> libmemusage.so
/sbin/ldconfig.real: /lib/i386-linux-gnu/ld-2.23.so is the dynamic linker, ignoring

	ld-linux.so.2 -> ld-2.23.so
	libnsl.so.1 -> libnsl-2.23.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libSegFault.so -> libSegFault.so
	libBrokenLocale.so.1 -> libBrokenLocale-2.23.so
	libm.so.6 -> libm-2.23.so
	librt.so.1 -> librt-2.23.so
	libnss_files.so.2 -> libnss_files-2.23.so
	libnss_compat.so.2 -> libnss_compat-2.23.so
	libcrypt.so.1 -> libcrypt-2.23.so
	libpcprofile.so -> libpcprofile.so
	libpthread.so.0 -> libpthread-2.23.so
	libnss_nis.so.2 -> libnss_nis-2.23.so
	libz.so.1 -> libz.so.1.2.8
	libutil.so.1 -> libutil-2.23.so
	libnss_hesiod.so.2 -> libnss_hesiod-2.23.so
	libanl.so.1 -> libanl-2.23.so
	libgcc_s.so.1 -> libgcc_s.so.1
	libnss_nisplus.so.2 -> libnss_nisplus-2.23.so
	libdl.so.2 -> libdl-2.23.so
	libc.so.6 -> libc-2.23.so
	libresolv.so.2 -> libresolv-2.23.so
	libcidn.so.1 -> libcidn-2.23.so
	libnss_dns.so.2 -> libnss_dns-2.23.so
/usr/lib/i386-linux-gnu:
/usr/local/lib:
	libdlt.so.2 -> libdlt.so.2.17.0
/lib/x86_64-linux-gnu:
	libnss_mdns.so.2 -> libnss_mdns.so.2
	libjson-c.so.2 -> libjson-c.so.2.0.0
	libmemusage.so -> libmemusage.so
	libkmod.so.2 -> libkmod.so.2.3.0
	libdevmapper.so.1.02.1 -> libdevmapper.so.1.02.1
	libbrlapi.so.0.6 -> libbrlapi.so.0.6.4
	libip6tc.so.0 -> libip6tc.so.0.1.0
	libpci.so.3 -> libpci.so.3.3.1
	libnsl.so.1 -> libnsl-2.23.so
	libe2p.so.2 -> libe2p.so.2.3
	libsepol.so.1 -> libsepol.so.1
/sbin/ldconfig.real: /lib/x86_64-linux-gnu/ld-2.23.so is the dynamic linker, ignoring

	ld-linux-x86-64.so.2 -> ld-2.23.so
	libpopt.so.0 -> libpopt.so.0.0.0
	libnss_mdns4.so.2 -> libnss_mdns4.so.2
	libcom_err.so.2 -> libcom_err.so.2.1
	libssl.so.1.0.0 -> libssl.so.1.0.0
	libnss_mdns6.so.2 -> libnss_mdns6.so.2
	libntfs-3g.so.861 -> libntfs-3g.so.861.0.0
	libisc-export.so.160 -> libisc-export.so.160.0.0
	libncurses.so.5 -> libncurses.so.5.9
	libnih.so.1 -> libnih.so.1.0.0
	libudev.so.1 -> libudev.so.1.6.4
	libthread_db.so.1 -> libthread_db-1.0.so
	libpam_misc.so.0 -> libpam_misc.so.0.82.0
	libulockmgr.so.1 -> libulockmgr.so.1.0.1
	libtinfo.so.5 -> libtinfo.so.5.9
	libaio.so.1 -> libaio.so.1.0.1
	libwrap.so.0 -> libwrap.so.0.7.6
	libglib-2.0.so.0 -> libglib-2.0.so.0.4800.2
	libSegFault.so -> libSegFault.so
	liblzma.so.5 -> liblzma.so.5.0.0
	libnss_mdns6_minimal.so.2 -> libnss_mdns6_minimal.so.2
	libBrokenLocale.so.1 -> libBrokenLocale-2.23.so
	libdns-export.so.162 -> libdns-export.so.162.1.3
	libply-splash-core.so.4 -> libply-splash-core.so.4.0.0
	libpamc.so.0 -> libpamc.so.0.82.1
	libm.so.6 -> libm-2.23.so
	libss.so.2 -> libss.so.2.0
	libnss_mdns4_minimal.so.2 -> libnss_mdns4_minimal.so.2
	librt.so.1 -> librt-2.23.so
	libnss_files.so.2 -> libnss_files-2.23.so
	libcgmanager.so.0 -> libcgmanager.so.0.0.0
	libnss_compat.so.2 -> libnss_compat-2.23.so
	libseccomp.so.2 -> libseccomp.so.2.2.3
	libcrypt.so.1 -> libcrypt-2.23.so
	libexpat.so.1 -> libexpat.so.1.6.0
	libdbus-1.so.3 -> libdbus-1.so.3.14.6
	libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
	libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
	libfdisk.so.1 -> libfdisk.so.1.1.0
	libply-boot-client.so.4 -> libply-boot-client.so.4.0.0
	libncursesw.so.5 -> libncursesw.so.5.9
	libparted-fs-resize.so.0 -> libparted-fs-resize.so.0.0.1
	libkeyutils.so.1 -> libkeyutils.so.1.5
	libslang.so.2 -> libslang.so.2.3.0
	libblkid.so.1 -> libblkid.so.1.1.0
	libpng12.so.0 -> libpng12.so.0.54.0
	libatm.so.1 -> libatm.so.1.0.0
	libext2fs.so.2 -> libext2fs.so.2.4
	libply.so.4 -> libply.so.4.0.0
	libpam.so.0 -> libpam.so.0.83.1
	libuuid.so.1 -> libuuid.so.1.3.0
	libxtables.so.11 -> libxtables.so.11.0.0
	libpcprofile.so -> libpcprofile.so
	libpcsclite.so.1 -> libpcsclite.so.1.0.0
	libusb-1.0.so.0 -> libusb-1.0.so.0.1.0
	libpthread.so.0 -> libpthread-2.23.so
	libnss_nis.so.2 -> libnss_nis-2.23.so
	libselinux.so.1 -> libselinux.so.1
	libip4tc.so.0 -> libip4tc.so.0.1.0
	libbsd.so.0 -> libbsd.so.0.8.2
	libiw.so.30 -> libiw.so.30
	libz.so.1 -> libz.so.1.2.8
	libnewt.so.0.52 -> libnewt.so.0.52.18
	libbz2.so.1.0 -> libbz2.so.1.0.4
	libutil.so.1 -> libutil-2.23.so
	libapparmor.so.1 -> libapparmor.so.1.4.0
	libprocps.so.4 -> libprocps.so.4.0.0
	libnss_hesiod.so.2 -> libnss_hesiod-2.23.so
	libanl.so.1 -> libanl-2.23.so
	libgcc_s.so.1 -> libgcc_s.so.1
	libreadline.so.6 -> libreadline.so.6.3
	libgpg-error.so.0 -> libgpg-error.so.0.17.0
	libnss_nisplus.so.2 -> libnss_nisplus-2.23.so
	libparted.so.2 -> libparted.so.2.0.1
	libatasmart.so.4 -> libatasmart.so.4.0.5
	libnl-genl-3.so.200 -> libnl-genl-3.so.200.22.0
	libcap.so.2 -> libcap.so.2.24
	libaudit.so.1 -> libaudit.so.1.0.0
	libacl.so.1 -> libacl.so.1.1.0
	libgcrypt.so.20 -> libgcrypt.so.20.0.5
	libmnl.so.0 -> libmnl.so.0.1.0
	libdl.so.2 -> libdl-2.23.so
	libx86.so.1 -> libx86.so.1
	libhistory.so.6 -> libhistory.so.6.3
	libc.so.6 -> libc-2.23.so
	libnss_mdns_minimal.so.2 -> libnss_mdns_minimal.so.2
	liblzo2.so.2 -> liblzo2.so.2.0.0
	libresolv.so.2 -> libresolv-2.23.so
	libnl-3.so.200 -> libnl-3.so.200.22.0
	libmount.so.1 -> libmount.so.1.1.0
	libfuse.so.2 -> libfuse.so.2.9.4
	libsmartcols.so.1 -> libsmartcols.so.1.1.0
	libply-splash-graphics.so.4 -> libply-splash-graphics.so.4.0.0
	libcryptsetup.so.4 -> libcryptsetup.so.4.6.0
	libpcre.so.3 -> libpcre.so.3.13.2
	libsystemd.so.0 -> libsystemd.so.0.14.0
	libiptc.so.0 -> libiptc.so.0.0.0
	libmvec.so.1 -> libmvec-2.23.so
	libcidn.so.1 -> libcidn-2.23.so
	libattr.so.1 -> libattr.so.1.1.0
	libnss_dns.so.2 -> libnss_dns-2.23.so
	libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
/usr/lib/x86_64-linux-gnu:
	libform.so.5 -> libform.so.5.9
	libnssutil3.so -> libnssutil3.so
	libnatpmp.so.1 -> libnatpmp.so.1
	libsane.so.1 -> libsane.so.1.0.25
	libglapi.so.0 -> libglapi.so.0.0.0
	libplds4.so -> libplds4.so
	libLLVM-3.8.so.1 -> libLLVM-3.8.so.1
	libopencv_contrib.so.2.4 -> libopencv_contrib.so.2.4.9
	libunity-action-qt.so.1 -> libunity-action-qt.so.1
	libunwind-ptrace.so.0 -> libunwind-ptrace.so.0.0.0
	libgtkmm-3.0.so.1 -> libgtkmm-3.0.so.1.1.0
	libopenjpeg_JPWL.so.5 -> libopenjpeg_JPWL.so.1.5.2
	libunity.so.9 -> libunity.so.9.0.2
	libcurl.so.4 -> libcurl.so.4.4.0
	libtic.so.5 -> libtic.so.5.9
	libmirclient.so.9 -> libmirclient.so.9
	libdvdread.so.4 -> libdvdread.so.4.2.0
	libspectre.so.1 -> libspectre.so.1.1.7
	libXxf86dga.so.1 -> libXxf86dga.so.1.0.0
	libIex-2_2.so.12 -> libIex-2_2.so.12.0.0
	libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.3800.1
	libfftw3f_omp.so.3 -> libfftw3f_omp.so.3.4.4
	libfl_pic.so.2 -> libfl_pic.so.2.0.0
	libfontembed.so.1 -> libfontembed.so.1.0.0
	libsemanage.so.1 -> libsemanage.so.1
	libdaemon.so.0 -> libdaemon.so.0.5.0
	libsnappy.so.1 -> libsnappy.so.1.3.0
	libgxps.so.2 -> libgxps.so.2.2.0
	libx264.so.148 -> libx264.so.148
	libcupsppdc.so.1 -> libcupsppdc.so.1
	libsignon-glib.so.1 -> libsignon-glib.so.1.0.0
	libogg.so.0 -> libogg.so.0.8.2
	libgensec.so.0 -> libgensec.so.0.0.1
	libgstnet-1.0.so.0 -> libgstnet-1.0.so.0.803.0
	libunity-core-6.0.so.9 -> libunity-core-6.0.so.9.0.0
	libx265.so.79 -> libx265.so.79
	libapt-private.so.0.0 -> libapt-private.so.0.0.0
	libgrilo-0.2.so.1 -> libgrilo-0.2.so.1.10.0
	libfftw3f_threads.so.3 -> libfftw3f_threads.so.3.4.4
	librevenge-generators-0.0.so.0 -> librevenge-generators-0.0.so.0.0.4
	libgstbadbase-1.0.so.0 -> libgstbadbase-1.0.so.0.803.0
	libcanberra.so.0 -> libcanberra.so.0.2.5
	libtheoraenc.so.1 -> libtheoraenc.so.1.1.2
	libIntelXvMC.so.1 -> libIntelXvMC.so.1.0.0
	libwinpr-interlocked.so.0.1 -> libwinpr-interlocked.so.0.1.0
	libflite_cmu_grapheme_lang.so.1 -> libflite_cmu_grapheme_lang.so.2.0.0
	libXvMCW.so.1 -> libXvMCW.so.1.0.0
	libfcitx-gclient.so.0 -> libfcitx-gclient.so.0.1
	libmircommon.so.5 -> libmircommon.so.5
	libjavascriptcoregtk-4.0.so.18 -> libjavascriptcoregtk-4.0.so.18.6.15
	libboost_date_time.so.1.58.0 -> libboost_date_time.so.1.58.0
	libgdkglext-x11-1.0.so.0 -> libgdkglext-x11-1.0.so.0.0.0
	libxml2.so.2 -> libxml2.so.2.9.3
	libaacs.so.0 -> libaacs.so.0.5.1
	libopenal.so.1 -> libopenal.so.1.16.0
	libpulse.so.0 -> libpulse.so.0.19.0
	libasprintf.so.0 -> libasprintf.so.0.0.0
	libass.so.5 -> libass.so.5.2.1
	libgeis.so.1 -> libgeis.so.1.3.0
	libQt5Xml.so.5 -> libQt5Xml.so.5.5.1
	libkrb5.so.26 -> libkrb5.so.26.0.0
	libnautilus-extension.so.1 -> libnautilus-extension.so.1.4.0
	libcogl.so.20 -> libcogl.so.20.4.1
	libbfd-2.26.1-system.so -> libbfd-2.26.1-system.so
	libgtkglext-x11-1.0.so.0 -> libgtkglext-x11-1.0.so.0.0.0
	libbdplus.so.0 -> libbdplus.so.0.1.0
	libavahi-core.so.7 -> libavahi-core.so.7.0.2
	libavahi-glib.so.1 -> libavahi-glib.so.1.0.2
	libndr-nbt.so.0 -> libndr-nbt.so.0.0.1
	libsync.so.2 -> libsync.so.2.0.0
	libgnutls-openssl.so.27 -> libgnutls-openssl.so.27.0.2
	libboost_system.so.1.58.0 -> libboost_system.so.1.58.0
	libnspr4.so -> libnspr4.so
	libsidplay.so.1 -> libsidplay.so.1.0.3
	libguile-2.0.so.22 -> libguile-2.0.so.22.7.2
	libicutest.so.55 -> libicutest.so.55.1
	libhpdiscovery.so.0 -> libhpdiscovery.so.0.0.1
	libpoppler.so.58 -> libpoppler.so.58.0.0
	libpagemaker-0.0.so.0 -> libpagemaker-0.0.so.0.0.3
	libedata-book-1.2.so.25 -> libedata-book-1.2.so.25.0.0
	libclutter-gtk-1.0.so.0 -> libclutter-gtk-1.0.so.0.600.6
	librasqal.so.3 -> librasqal.so.3.0.0
	liba11y-profile-manager-0.1.so.0 -> liba11y-profile-manager-0.1.so.0.1.0
	libflite_cmu_us_kal16.so.1 -> libflite_cmu_us_kal16.so.2.0.0
	libtotem-plparser.so.18 -> libtotem-plparser.so.18.1.0
	liblua5.2-c++.so.0 -> liblua5.2-c++.so.0.0.0
	libspandsp.so.2 -> libspandsp.so.2.0.0
	libharfbuzz-icu.so.0 -> libharfbuzz-icu.so.0.10000.1
	libcups.so.2 -> libcups.so.2
	libboost_random.so.1.58.0 -> libboost_random.so.1.58.0
	libgstpbutils-1.0.so.0 -> libgstpbutils-1.0.so.0.803.0
	libndr.so.0 -> libndr.so.0.0.5
	libtheoradec.so.1 -> libtheoradec.so.1.1.4
	libsndfile.so.1 -> libsndfile.so.1.0.25
	libflite_cmu_us_kal.so.1 -> libflite_cmu_us_kal.so.2.0.0
	libindicator3.so.7 -> libindicator3.so.7.0.0
	libXft.so.2 -> libXft.so.2.3.2
	libicuio.so.55 -> libicuio.so.55.1
	liblua5.3-lpeg.so.2 -> liblua5.3-lpeg.so.2.0.0
	libis.so.1 -> libis.so.1.0.0
	libnetapi.so.0 -> libnetapi.so.0
	libgeocode-glib.so.0 -> libgeocode-glib.so.0.0.0
	libmpc.so.3 -> libmpc.so.3.0.0
	libboost_iostreams.so.1.58.0 -> libboost_iostreams.so.1.58.0
	libandroid-properties.so.1 -> libandroid-properties.so.1.0.0
	libgpm.so.2 -> libgpm.so.2
	libwpd-0.10.so.10 -> libwpd-0.10.so.10.0.1
	libpng12.so.0 -> libpng.so
	libdc1394.so.22 -> libdc1394.so.22.1.11
	libcolorhug.so.2 -> libcolorhug.so.2.0.4
	libfontenc.so.1 -> libfontenc.so.1.0.0
	libpython3.5m.so.1.0 -> libpython3.5m.so.1.0
	libQt5Organizer.so.5 -> libQt5Organizer.so.5.0.0
	libdrm_amdgpu.so.1 -> libdrm_amdgpu.so.1.0.0
	libaccountsservice.so.0 -> libaccountsservice.so.0.0.0
	libmimic.so.0 -> libmimic.so.0.0.1
	libgdk-x11-2.0.so.0 -> libgdk-x11-2.0.so.0.2400.30
	libdrm_intel.so.1 -> libdrm_intel.so.1.0.0
	libaccounts-qt5.so.1 -> libaccounts-qt5.so.1.2.0
	libneon-gnutls.so.27 -> libneon-gnutls.so.27.3.1
	libindicator.so.7 -> libindicator.so.7.0.0
	libmwaw-0.3.so.3 -> libmwaw-0.3.so.3.0.7
	libgstwayland-1.0.so.0 -> libgstwayland-1.0.so.0.803.0
	libOxideQtQuick.so.0 -> libOxideQtQuick.so.0
	libffi.so.6 -> libffi.so.6.0.4
	libasyncns.so.0 -> libasyncns.so.0.3.1
	libgstallocators-1.0.so.0 -> libgstallocators-1.0.so.0.803.0
	libcolordprivate.so.2 -> libcolordprivate.so.2.0.4
	libvo-amrwbenc.so.0 -> libvo-amrwbenc.so.0.0.4
	libnfnetlink.so.0 -> libnfnetlink.so.0.2.0
	libgnome-keyring.so.0 -> libgnome-keyring.so.0.2.0
	libQtSql.so.4 -> libQtSql.so.4.8.7
	libxatracker.so.2 -> libxatracker.so.2.3.0
	libxcb-sync.so.1 -> libxcb-sync.so.1.0.0
	libwifi.so.1 -> libwifi.so.1.0.0
	libXpm.so.4 -> libXpm.so.4.11.0
	libvorbisfile.so.3 -> libvorbisfile.so.3.3.7
	libnux-graphics-4.0.so.0 -> libnux-graphics-4.0.so.0.8.0
	libbabeltrace-ctf-metadata.so.1 -> libbabeltrace-ctf-metadata.so.1.0.0
	libltdl.so.7 -> libltdl.so.7.3.1
	libical.so.1 -> libical.so.1.0.1
	libkrb5.so.3 -> libkrb5.so.3.3
	libpcre32.so.3 -> libpcre32.so.3.13.2
	libgdk_pixbuf-2.0.so.0 -> libgdk_pixbuf-2.0.so.0.3200.2
	libQt5Widgets.so.5 -> libQt5Widgets.so.5.5.1
	libquvi.so.7 -> libquvi.so.7.0.1
	libsodium.so.18 -> libsodium.so.18.0.1
	libtasn1.so.6 -> libtasn1.so.6.5.1
	libpulse-simple.so.0 -> libpulse-simple.so.0.1.0
	libQtDBus.so.4 -> libQtDBus.so.4.8.7
	libgnome-bluetooth.so.13 -> libgnome-bluetooth.so.13.0.1
	liblangtag.so.1 -> liblangtag.so.1.3.1
	libtotem.so.0 -> libtotem.so.0.0.0
	libva.so.1 -> libva.so.1.3900.0
	libjsoncpp.so.1 -> libjsoncpp.so.1.7.2
	libgstsdp-1.0.so.0 -> libgstsdp-1.0.so.0.803.0
	libwayland-egl.so.1 -> libwayland-egl.so.1.0.0
	libcacard.so.0 -> libcacard.so.0.0.0
	libwmf-0.2.so.7 -> libwmf-0.2.so.7.1.0
	libgtk-3.so.0 -> libgtk-3.so.0.1800.9
	libgstbadvideo-1.0.so.0 -> libgstbadvideo-1.0.so.0.803.0
	libmspub-0.1.so.1 -> libmspub-0.1.so.1.0.2
	libGLEWmx.so.1.13 -> libGLEWmx.so.1.13.0
	libcdio.so.13 -> libcdio.so.13.0.0
	libpangox-1.0.so.0 -> libpangox-1.0.so.0.0.0
	libmpxwrappers.so.0 -> libmpxwrappers.so.0.0.0
	libgom-1.0.so.0 -> libgom-1.0.so.0.1.0
	libibus-1.0.so.5 -> libibus-1.0.so.5.0.511
	libgstrtsp-1.0.so.0 -> libgstrtsp-1.0.so.0.803.0
	libtelepathy-glib.so.0 -> libtelepathy-glib.so.0.84.1
	libgettextlib-0.19.7.so -> libgettextlib.so
	libmircommon.so.7 -> libmircommon.so.7
	libclucene-contribs-lib.so.1 -> libclucene-contribs-lib.so.2.3.3.4
	libwinpr-pool.so.0.1 -> libwinpr-pool.so.0.1.0
	libXdmcp.so.6 -> libXdmcp.so.6.0.0
	libebook-contacts-1.2.so.2 -> libebook-contacts-1.2.so.2.0.0
	libbabeltrace-dummy.so.1 -> libbabeltrace-dummy.so.1.0.0
	libv4l2.so.0 -> libv4l2.so.0.0.0
	libswscale-ffmpeg.so.3 -> libswscale-ffmpeg.so.3.1.101
	libwinpr-environment.so.0.1 -> libwinpr-environment.so.0.1.0
	libIlmImfUtil-2_2.so.22 -> libIlmImfUtil-2_2.so.22.0.0
	libgc.so.1 -> libgc.so.1.0.3
	libvncclient.so.1 -> libvncclient.so.1.0.0
	libustr-1.0.so.1 -> libustr-1.0.so.1.0.4
	libwind.so.0 -> libwind.so.0.0.0
	libgrlpls-0.2.so.0 -> libgrlpls-0.2.so.0.0.5
	libwavpack.so.1 -> libwavpack.so.1.1.7
	libunwind-coredump.so.0 -> libunwind-coredump.so.0.0.0
	libxcb-render-util.so.0 -> libxcb-render-util.so.0.0.0
	libfluidsynth.so.1 -> libfluidsynth.so.1.5.2
	libQt5EglDeviceIntegration.so.5 -> libQt5EglDeviceIntegration.so.5.5.1
	liblouisutdml.so.6 -> liblouisutdml.so.6.0.8
	libdb-5.3.so -> libdb-5.3.so
	libgailutil-3.so.0 -> libgailutil-3.so.0.0.0
	libedataserver-1.2.so.21 -> libedataserver-1.2.so.21.0.0
	libpostproc-ffmpeg.so.53 -> libpostproc-ffmpeg.so.53.3.100
	libgtkmm-2.4.so.1 -> libgtkmm-2.4.so.1.1.0
	libevdocument3.so.4 -> libevdocument3.so.4.0.0
	libsuitesparseconfig.so.4.4.6 -> libsuitesparseconfig.so.4.4.6
	libQt5Gui.so.5 -> libQt5Gui.so.5.5.1
	libhybris-hwcomposerwindow.so.1 -> libhybris-hwcomposerwindow.so.1.0.0
	libnma.so.0 -> libnma.so.0.0.0
	libido3-0.1.so.0 -> libido3-0.1.so.0.0.0
	libgraphite2.so.3 -> libgraphite2.so.3.0.1
	libnss3.so -> libnss3.so
	libflite_cmu_time_awb.so.1 -> libflite_cmu_time_awb.so.2.0.0
	libgdbm_compat.so.3 -> libgdbm_compat.so.3.0.0
	liblua5.2-lpeg.so.2 -> liblua5.2-lpeg.so.2.0.0
	libiscsi.so.2 -> libiscsi.so.2.1.12
	libkj-async-0.5.3.so -> libkj-async-0.5.3.so
	libao.so.4 -> libao.so.4.0.0
	libgomp.so.1 -> libgomp.so.1.0.0
	libgdbm.so.3 -> libgdbm.so.3.0.0
	libinput.so.10 -> libinput.so.10.7.5
	libqqwing.so.2 -> libqqwing.so.2.1.0
	libgweather-3.so.6 -> libgweather-3.so.6.5.0
	liblcms2.so.2 -> liblcms2.so.2.0.6
	libminiupnpc.so.10 -> libminiupnpc.so.10
	liborcus-0.10.so.0 -> liborcus-0.10.so.0.0.0
	libpolkit-backend-1.so.0 -> libpolkit-backend-1.so.0.0.0
	libgcr-ui-3.so.1 -> libgcr-ui-3.so.1.0.0
	libformw.so.5 -> libformw.so.5.9
	libdv.so.4 -> libdv.so.4.0.3
	libsnapd-glib.so.1 -> libsnapd-glib.so.1.0.0
	libpixman-1.so.0 -> libpixman-1.so.0.33.6
	libefivar.so.0 -> libefivar.so.0.23
	libexempi.so.3 -> libexempi.so.3.2.4
	libgstaudio-1.0.so.0 -> libgstaudio-1.0.so.0.803.0
	libstartup-notification-1.so.0 -> libstartup-notification-1.so.0.0.0
	libe-book-0.1.so.1 -> libe-book-0.1.so.1.0.2
	libI810XvMC.so.1 -> libI810XvMC.so.1.0.0
	libgusb.so.2 -> libgusb.so.2.0.10
	libsensors.so.4 -> libsensors.so.4.4.0
	libijs-0.35.so -> libijs-0.35.so
	liburl-dispatcher.so.1 -> liburl-dispatcher.so.1.0.0
	libxslt.so.1 -> libxslt.so.1.1.28
	libicalss.so.1 -> libicalss.so.1.0.1
	libjacknet.so.0 -> libjacknet.so.0.1.0
	liblber-2.4.so.2 -> liblber-2.4.so.2.10.5
	libedata-cal-1.2.so.28 -> libedata-cal-1.2.so.28.0.0
	libexslt.so.0 -> libexslt.so.0.8.17
	libmpeg2.so.0 -> libmpeg2.so.0.1.0
	libGLEW.so.1.13 -> libGLEW.so.1.13.0
	libpanel.so.5 -> libpanel.so.5.9
	libgssapi.so.3 -> libgssapi.so.3.0.0
	librom1394.so.0 -> librom1394.so.0.3.0
	libssh-gcrypt.so.4 -> libssh-gcrypt.so.4.4.1
	libopcodes-2.26.1-system.so -> libopcodes-2.26.1-system.so
	libMagickWand-6.Q16.so.2 -> libMagickWand-6.Q16.so.2.0.0
	libatspi.so.0 -> libatspi.so.0.0.1
	liblwres.so.141 -> liblwres.so.141.0.3
	libpolkit-agent-1.so.0 -> libpolkit-agent-1.so.0.0.0
	libxcb-glx.so.0 -> libxcb-glx.so.0.0.0
	libatomic.so.1 -> libatomic.so.1.1.0
	libicuuc.so.55 -> libicuuc.so.55.1
	libwinpr-handle.so.0.1 -> libwinpr-handle.so.0.1.0
	libiculx.so.55 -> libiculx.so.55.1
	libfaad_drm.so.2 -> libfaad_drm.so.2.0.0
	libopencv_imgproc.so.2.4 -> libopencv_imgproc.so.2.4.9
	libzvbi.so.0 -> libzvbi.so.0.13.2
	libasn1.so.8 -> libasn1.so.8.0.0
	libwayland-server.so.0 -> libwayland-server.so.0.1.0
	libopus.so.0 -> libopus.so.0.5.2
	libavfilter-ffmpeg.so.5 -> libavfilter-ffmpeg.so.5.40.101
	libisc.so.160 -> libisc.so.160.0.0
	libunity-control-center.so.1 -> libunity-control-center.so.1.0.0
	libgstgl-1.0.so.0 -> libgstgl-1.0.so.0.803.0
	libgs.so.9 -> libgs.so.9.18
	libfcitx-utils.so.0 -> libfcitx-utils.so.0.1
	libxcb-shm.so.0 -> libxcb-shm.so.0.0.0
	libxcb-keysyms.so.1 -> libxcb-keysyms.so.1.0.0
	libgpod.so.4 -> libgpod.so.4.3.2
	libgdata.so.22 -> libgdata.so.22.1.2
	libfreerdp-client.so.1.1 -> libfreerdp-client.so.1.1.0
	libXdamage.so.1 -> libXdamage.so.1.1.0
	libnettle.so.6 -> libnettle.so.6.2
	libatk-bridge-2.0.so.0 -> libatk-bridge-2.0.so.0.0.0
	libp11-kit.so.0 -> libp11-kit.so.0.1.0
	libsmbclient-raw.so.0 -> libsmbclient-raw.so.0.0.1
	libmedia.so.1 -> libmedia.so.1.0.0
	libofa.so.0 -> libofa.so.0.0.0
	libsecret-1.so.0 -> libsecret-1.so.0.0.0
	libgeonames.so.0 -> libgeonames.so.0.0.0
	libsamba-policy.so.0 -> libsamba-policy.so.0.0.1
	libnpth.so.0 -> libnpth.so.0.0.5
	libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
	libgutenprint.so.2 -> libgutenprint.so.2.4.0
	libopencv_video.so.2.4 -> libopencv_video.so.2.4.9
	libimobiledevice.so.6 -> libimobiledevice.so.6.0.0
	libxenctrl-4.6.so -> libxenctrl-4.6.so
	libgeoclue.so.0 -> libgeoclue.so.0.0.0
	libmpdec.so.2 -> libmpdec.so.2.4.2
	libXaw.so.7 -> libXaw7.so.7.0.0
	libcmis-0.5.so.5 -> libcmis-0.5.so.5.0.0
	libvorbisenc.so.2 -> libvorbisenc.so.2.0.11
	libxlutil-4.6.so -> libxlutil-4.6.so
	libXcomposite.so.1 -> libXcomposite.so.1.0.0
	libboost_filesystem.so.1.58.0 -> libboost_filesystem.so.1.58.0
	librest-0.7.so.0 -> librest-0.7.so.0.0.0
	libmythes-1.2.so.0 -> libmythes-1.2.so.0.0.0
	libnotify.so.4 -> libnotify.so.4.0.0
	libmtdev.so.1 -> libmtdev.so.1.0.0
	libnux-4.0.so.0 -> libnux-4.0.so.0.8.0
	libQtCLucene.so.4 -> libQtCLucene.so.4.8.7
	libtevent-util.so.0 -> libtevent-util.so.0.0.1
	libSM.so.6 -> libSM.so.6.0.1
	libUbuntuGestures.so.5 -> libUbuntuGestures.so.5.5.0
	libpaper.so.1 -> libpaper.so.1.1.2
	libsamdb.so.0 -> libsamdb.so.0.0.1
	libgbm.so.1 -> libgbm.so.1.0.0
	libxcb-xkb.so.1 -> libxcb-xkb.so.1.0.0
	libbluray.so.1 -> libbluray.so.1.9.2
	libsf.so.1 -> libsf.so.1.0.0
	libgconf-2.so.4 -> libgconf-2.so.4.1.5
	librevenge-0.0.so.0 -> librevenge-0.0.so.0.0.4
	libv4l1.so.0 -> libv4l1.so.0.0.0
	libspeechd.so.2 -> libspeechd.so.2.6.0
	libpcrecpp.so.0 -> libpcrecpp.so.0.0.1
	libSoundTouch.so.1 -> libSoundTouch.so.1.0.0
	libmessaging-menu.so.0 -> libmessaging-menu.so.0.0.0
	libwinpr-dsparse.so.0.1 -> libwinpr-dsparse.so.0.1.0
	libssh_threads.so.4 -> libssh_threads.so.4.4.1
	libinproctrace.so -> libinproctrace.so
	libgdkmm-2.4.so.1 -> libgdkmm-2.4.so.1.1.0
	libsignon-extension.so.1 -> libsignon-extension.so.1.0.0
	libappstream.so.3 -> libappstream.so.0.9.4
	libgettextpo.so.0 -> libgettextpo.so.0.5.3
	libgrlnet-0.2.so.0 -> libgrlnet-0.2.so.0.1.10
	libcdio_cdda.so.1 -> libcdio_cdda.so.1.0.0
	libsignon-plugins.so.1 -> libsignon-plugins.so.1.0.0
	libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.2400.30
	libcamera.so.1 -> libcamera.so.1.0.0
	libwebp.so.5 -> libwebp.so.5.0.4
	libxenguest-4.6.so -> libxenguest-4.6.so
	libgstcheck-1.0.so.0 -> libgstcheck-1.0.so.0.803.0
	librsvg-2.so.2 -> librsvg-2.so.2.40.13
	libtbbmalloc_proxy.so.2 -> libtbbmalloc_proxy.so.2
	libQt5WebKit.so.5 -> libQt5WebKit.so.5.5.1
	libidn.so.11 -> libidn.so.11.6.15
	libopencv_highgui.so.2.4 -> libopencv_highgui.so.2.4.9
	libde265.so.0 -> libde265.so.0.0.10
	libmhash.so.2 -> libmhash.so.2.0.1
	libzeitgeist-2.0.so.0 -> libzeitgeist-2.0.so.0.0.0
	libsoxr.so.0 -> libsoxr.so.0.1.1
	libQt5Svg.so.5 -> libQt5Svg.so.5.5.1
	libpangomm-1.4.so.1 -> libpangomm-1.4.so.1.0.30
	libpython2.7.so.1.0 -> libpython2.7.so.1.0
	libcolumbus.so.1 -> libcolumbus.so.1.1.0
	libassuan.so.0 -> libassuan.so.0.7.2
	libapt-pkg.so.5.0 -> libapt-pkg.so.5.0.0
	libtimezonemap.so.1 -> libtimezonemap.so.1.0.0
	libopencv_calib3d.so.2.4 -> libopencv_calib3d.so.2.4.9
	librdf.so.0 -> librdf.so.0.0.0
	libgsettings-qt.so.1 -> libgsettings-qt.so.1.0.0
	libmpeg2encpp-2.1.so.0 -> libmpeg2encpp-2.1.so.0.0.0
	libcupsfilters.so.1 -> libcupsfilters.so.1.0.0
	libtwolame.so.0 -> libtwolame.so.0.0.0
	libcupscgi.so.1 -> libcupscgi.so.1
	libclucene-core.so.1 -> libclucene-core.so.2.3.3.4
	libwinpr-registry.so.0.1 -> libwinpr-registry.so.0.1.0
	libcrack.so.2 -> libcrack.so.2.9.0
	libprotobuf.so.9 -> libprotobuf.so.9.0.1
	libcompiz_core.so.ABI-20151010 -> libcompiz_core.so.0.9.12.2
	liblinear.so.3 -> liblinear.so.3.2.
	libGLU.so.1 -> libGLU.so.1.3.1
	libXrender.so.1 -> libXrender.so.1.3.0
	libQt5QuickTest.so.5 -> libQt5QuickTest.so.5.5.1
	libxkbfile.so.1 -> libxkbfile.so.1.0.2
	libopencv_objdetect.so.2.4 -> libopencv_objdetect.so.2.4.9
	libQt5Positioning.so.5 -> libQt5Positioning.so.5.5.1
	libtheora.so.0 -> libtheora.so.0.3.10
	libunistring.so.0 -> libunistring.so.0.1.2
	libwinpr-crt.so.0.1 -> libwinpr-crt.so.0.1.0
	libexif.so.12 -> libexif.so.12.3.3
	libpeas-1.0.so.0 -> libpeas-1.0.so.0.1600.0
	libgnome-bluetooth.so.0 -> libgnome-bluetooth.so.0.0.0
	libgucharmap_2_90.so.7 -> libgucharmap_2_90.so.7.0.0
	libefiboot.so.0 -> libefiboot.so.0.23
	libwacom.so.2 -> libwacom.so.2.4.5
	libXmuu.so.1 -> libXmuu.so.1.0.0
	libabw-0.1.so.1 -> libabw-0.1.so.1.0.1
	libmbim-glib.so.4 -> libmbim-glib.so.4.1.0
	libicutu.so.55 -> libicutu.so.55.1
	libdcerpc.so.0 -> libdcerpc.so.0.0.1
	libgsm.so.1 -> libgsm.so.1.0.12
	libXau.so.6 -> libXau.so.6.0.0
	libdcerpc-atsvc.so.0 -> libdcerpc-atsvc.so.0.0.1
	libwbclient.so.0 -> libwbclient.so.0.12
	libapt-inst.so.2.0 -> libapt-inst.so.2.0.0
	libndr-standard.so.0 -> libndr-standard.so.0.0.1
	libk5crypto.so.3 -> libk5crypto.so.3.1
	libtk8.6.so -> libtk8.6.so.0
	libwps-0.4.so.4 -> libwps-0.4.so.4.0.3
	libharfbuzz.so.0 -> libharfbuzz.so.0.10000.1
	libxcb-dri2.so.0 -> libxcb-dri2.so.0.0.0
	libpcre16.so.3 -> libpcre16.so.3.13.2
	libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.3800.1
	libswresample-ffmpeg.so.1 -> libswresample-ffmpeg.so.1.2.101
	libhpipp.so.0 -> libhpipp.so.0.0.1
	libgtop-2.0.so.10 -> libgtop-2.0.so.10.0.0
	libwinpr-sspi.so.0.1 -> libwinpr-sspi.so.0.1.0
	libnm-gtk.so.0 -> libnm-gtk.so.0.0.0
	libdbusmenu-gtk.so.4 -> libdbusmenu-gtk.so.4.0.12
	libflite_cmu_grapheme_lex.so.1 -> libflite_cmu_grapheme_lex.so.2.0.0
	libvibrator.so.1 -> libvibrator.so.1.0.0
	libnux-core-4.0.so.0 -> libnux-core-4.0.so.0.8.0
	librados.so.2 -> librados.so.2.0.0
	libxkbcommon-x11.so.0 -> libxkbcommon-x11.so.0.0.0
	libhpmud.so.0 -> libhpmud.so.0.0.6
	libndr-krb5pac.so.0 -> libndr-krb5pac.so.0.0.1
	libwhoopsie-preferences.so.0 -> libwhoopsie-preferences.so.0.0.0
	liblouis.so.9 -> liblouis.so.9.0.0
	libGeoIP.so.1 -> libGeoIP.so.1.6.9
	libgme.so.0 -> libgme.so.0.6.0
	libopencv_core.so.2.4 -> libopencv_core.so.2.4.9
	libLLVM-5.0.so.1 -> libLLVM-5.0.so.1
	libhunspell-1.3.so.0 -> libhunspell-1.3.so.0.0.0
	libmms.so.0 -> libmms.so.0.0.2
	libcupsimage.so.2 -> libcupsimage.so.2
	liborcus-mso-0.10.so.0 -> liborcus-mso-0.10.so.0.0.0
	libfreerdp-cache.so.1.1 -> libfreerdp-cache.so.1.1.0
	libX11.so.6 -> libX11.so.6.3.0
	libIlmThread-2_2.so.12 -> libIlmThread-2_2.so.12.0.0
	libflite_cmu_indic_lex.so.1 -> libflite_cmu_indic_lex.so.2.0.0
	libaa.so.1 -> libaa.so.1.0.4
	libwinpr-library.so.0.1 -> libwinpr-library.so.0.1.0
	libbabeltrace.so.1 -> libbabeltrace.so.1.0.0
	libavahi-common.so.3 -> libavahi-common.so.3.5.3
	libappindicator.so.1 -> libappindicator.so.1.0.0
	libwinpr-path.so.0.1 -> libwinpr-path.so.0.1.0
	libgstreamer-1.0.so.0 -> libgstreamer-1.0.so.0.803.0
	libXtst.so.6 -> libXtst.so.6.1.0
	libdconf.so.1 -> libdconf.so.1.0.0
	libQt5PrintSupport.so.5 -> libQt5PrintSupport.so.5.5.1
	libgck-1.so.0 -> libgck-1.so.0.0.0
	libQtXml.so.4 -> libQtXml.so.4.8.7
	libgdk-3.so.0 -> libgdk-3.so.0.1800.9
	libtxc_dxtn_s2tc.so.0 -> libtxc_dxtn_s2tc.so.0.0.0
	libcamel-1.2.so.54 -> libcamel-1.2.so.54.0.0
	libxcb.so.1 -> libxcb.so.1.1.0
	libperl.so.5.22 -> libperl.so.5.22.1
	libxcb-render.so.0 -> libxcb-render.so.0.0.0
	libssh-gcrypt_threads.so.4 -> libssh-gcrypt_threads.so.4.4.1
	libtbb.so.2 -> libtbb.so.2
	libxcb-util.so.1 -> libxcb-util.so.1.0.0
	libgssapi_krb5.so.2 -> libgssapi_krb5.so.2.2
	libtsan.so.0 -> libtsan.so.0.0.0
	libwinpr-synch.so.0.1 -> libwinpr-synch.so.0.1.0
	libgettextsrc-0.19.7.so -> libgettextsrc.so
	libthai.so.0 -> libthai.so.0.2.4
	libmircore.so.1 -> libmircore.so.1
	libssl3.so -> libssl3.so
	libgmime-2.6.so.0 -> libgmime-2.6.so.0.620.0
	libgpgme.so.11 -> libgpgme.so.11.14.0
	libHalf.so.12 -> libHalf.so.12.0.0
	libdvdnav.so.4 -> libdvdnav.so.4.2.0
	libcdda_interface.so.0 -> libcdda_interface.so.0.10.2
	libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.3800.1
	libisc-pkcs11.so.160 -> libisc-pkcs11.so.160.0.0
	libraw.so.15 -> libraw.so.15.0.0
	libgstvideo-1.0.so.0 -> libgstvideo-1.0.so.0.803.0
	libstdc++.so.6 -> libstdc++.so.6.0.21
	libopencv_legacy.so.2.4 -> libopencv_legacy.so.2.4.9
	libwinpr-utils.so.0.1 -> libwinpr-utils.so.0.1.0
	librhythmbox-core.so.9 -> librhythmbox-core.so.9.0.0
	libsmbldap.so.0 -> libsmbldap.so.0
	libgdkmm-3.0.so.1 -> libgdkmm-3.0.so.1.1.0
	libssh.so.4 -> libssh.so.4.4.1
	libdrm.so.2 -> libdrm.so.2.4.0
	libsignon-qt5.so.1 -> libsignon-qt5.so.1.0.0
	libgccpp.so.1 -> libgccpp.so.1.0.3
	libdjvulibre.so.21 -> libdjvulibre.so.21.6.0
	libXv.so.1 -> libXv.so.1.0.0
	libpackagekit-glib2.so.16 -> libpackagekit-glib2.so.16.3.0
	libcanberra-gtk.so.0 -> libcanberra-gtk.so.0.1.9
	libasound.so.2 -> libasound.so.2.0.0
	libnm.so.0 -> libnm.so.0.1.0
	libQt5Network.so.5 -> libQt5Network.so.5.5.1
	liborcus-parser-0.10.so.0 -> liborcus-parser-0.10.so.0.0.0
	libdecoration.so.0 -> libdecoration.so.0.0.0
	libXext.so.6 -> libXext.so.6.4.0
	libdbusmenu-gtk3.so.4 -> libdbusmenu-gtk3.so.4.0.12
	libprotobuf-lite.so.9 -> libprotobuf-lite.so.9.0.1
	libgstphotography-1.0.so.0 -> libgstphotography-1.0.so.0.803.0
	libmtp.so.9 -> libmtp.so.9.3.0
	libestr.so.0 -> libestr.so.0.0.0
	libxvidcore.so.4 -> libxvidcore.so.4.3
	libsqlite3.so.0 -> libsqlite3.so.0.8.6
	libjbig2dec.so.0 -> libjbig2dec.so.0.0.0
	libavahi-client.so.3 -> libavahi-client.so.3.2.9
	libFLAC.so.8 -> libFLAC.so.8.3.0
	libgstadaptivedemux-1.0.so.0 -> libgstadaptivedemux-1.0.so.0.803.0
	libgmp.so.10 -> libgmp.so.10.3.0
	libQt5Quick.so.5 -> libQt5Quick.so.5.5.1
	libhybris-eglplatformcommon.so.1 -> libhybris-eglplatformcommon.so.1.0.0
	libQtGui.so.4 -> libQtGui.so.4.8.7
	libgstriff-1.0.so.0 -> libgstriff-1.0.so.0.803.0
	libwnck-3.so.0 -> libwnck-3.so.0.2.2
	libQt5XcbQpa.so.5 -> libQt5XcbQpa.so.5.5.1
	libmad.so.0 -> libmad.so.0.2.1
	libgcr-base-3.so.1 -> libgcr-base-3.so.1.0.0
	libXi.so.6 -> libXi.so.6.1.0
	libnfc_nxp.so.1 -> libnfc_nxp.so.1.0.0
	libgpgme-pthread.so.11 -> libgpgme-pthread.so.11.14.0
	libglibmm-2.4.so.1 -> libglibmm-2.4.so.1.3.0
	libcompizconfig.so.0 -> libcompizconfig.so.0.0.0
	libgnutls.so.30 -> libgnutls.so.30.6.2
	libflite_cmu_indic_lang.so.1 -> libflite_cmu_indic_lang.so.2.0.0
	libavutil-ffmpeg.so.54 -> libavutil-ffmpeg.so.54.31.100
	libbind9.so.140 -> libbind9.so.140.0.10
	libWildMidi.so.1 -> libWildMidi.so.1.1.2
	libupower-glib.so.3 -> libupower-glib.so.3.0.1
	libportaudio.so.2 -> libportaudio.so.2.0.0
	libmjpegutils-2.1.so.0 -> libmjpegutils-2.1.so.0.0.0
	libbluetooth.so.3 -> libbluetooth.so.3.18.10
	libcapnp-0.5.3.so -> libcapnp-0.5.3.so
	libpwquality.so.1 -> libpwquality.so.1.0.2
	libcapnp-rpc-0.5.3.so -> libcapnp-rpc-0.5.3.so
	libpciaccess.so.0 -> libpciaccess.so.0.11.1
	libmirprotobuf.so.3 -> libmirprotobuf.so.3
	libXrandr.so.2 -> libXrandr.so.2.2.0
	libespeak.so.1 -> libespeak.so.1.1.48
	libgtksourceview-3.0.so.1 -> libgtksourceview-3.0.so.1.5.0
	libcaca.so.0 -> libcaca.so.0.99.19
	libopencore-amrwb.so.0 -> libopencore-amrwb.so.0.0.3
	liblightdm-gobject-1.so.0 -> liblightdm-gobject-1.so.0.0.0
	librevenge-stream-0.0.so.0 -> librevenge-stream-0.0.so.0.0.4
	libQt5Core.so.5 -> libQt5Core.so.5.5.1
	libflite_cmu_us_slt.so.1 -> libflite_cmu_us_slt.so.2.0.0
	libdcerpc-samr.so.0 -> libdcerpc-samr.so.0.0.1
	libwinpr-sysinfo.so.0.1 -> libwinpr-sysinfo.so.0.1.0
	libcdda_paranoia.so.0 -> libcdda_paranoia.so.0.10.2
	libpoppler-glib.so.8 -> libpoppler-glib.so.8.7.0
	libunwind-x86_64.so.8 -> libunwind-x86_64.so.8.0.1
	libXcursor.so.1 -> libXcursor.so.1.0.2
	libwinpr-thread.so.0.1 -> libwinpr-thread.so.0.1.0
	libgphoto2.so.6 -> libgphoto2.so.6.0.0
	libtevent.so.0 -> libtevent.so.0.9.28
	liborc-0.4.so.0 -> liborc-0.4.so.0.25.0
	libschroedinger-1.0.so.0 -> libschroedinger-1.0.so.0.11.0
	libgnomekbdui.so.8 -> libgnomekbdui.so.8.0.0
	libquadmath.so.0 -> libquadmath.so.0.0.0
	libatk-1.0.so.0 -> libatk-1.0.so.0.21809.1
	libsamba-credentials.so.0 -> libsamba-credentials.so.0.0.1
	libXRes.so.1 -> libXRes.so.1.0.0
	libwmflite-0.2.so.7 -> libwmflite-0.2.so.7.0.1
	libnm-util.so.2 -> libnm-util.so.2.7.0
	libmenuw.so.5 -> libmenuw.so.5.9
	libecal-1.2.so.19 -> libecal-1.2.so.19.0.0
	libvo-aacenc.so.0 -> libvo-aacenc.so.0.0.4
	libxcb-xfixes.so.0 -> libxcb-xfixes.so.0.0.0
	libmodplug.so.1 -> libmodplug.so.1.0.0
	libSDL-1.2.so.0 -> libSDL.so
	libroken.so.18 -> libroken.so.18.1.0
	libtag.so.1 -> libtag.so.1.14.0
	libfaad.so.2 -> libfaad.so.2.0.0
	libclutter-gst-3.0.so.0 -> libclutter-gst-3.0.so.0.18.0
	libproxy.so.1 -> libproxy.so.1.0.0
	libfreerdp-primitives.so.1.1 -> libfreerdp-primitives.so.1.1.0
	libhcrypto.so.4 -> libhcrypto.so.4.1.0
	libunity-webapps-repository.so.0 -> libunity-webapps-repository.so.0.0.0
	libitm.so.1 -> libitm.so.1.0.0
	libpeas-gtk-1.0.so.0 -> libpeas-gtk-1.0.so.0.1600.0
	libaudio.so.2 -> libaudio.so.2.4
	libtracker-sparql-1.0.so.0 -> libtracker-sparql-1.0.so.0.602.0
	libmpx.so.0 -> libmpx.so.0.0.0
	libavahi-ui-gtk3.so.0 -> libavahi-ui-gtk3.so.0.1.4
	libcogl-path.so.20 -> libcogl-path.so.20.4.1
	libXinerama.so.1 -> libXinerama.so.1.0.0
	libgoa-1.0.so.0 -> libgoa-1.0.so.0.0.0
	libxcb-icccm.so.4 -> libxcb-icccm.so.4.0.0
	libgudev-1.0.so.0 -> libgudev-1.0.so.0.2.0
	libavcodec-ffmpeg.so.56 -> libavcodec-ffmpeg.so.56.60.100
	libwinpr-rpc.so.0.1 -> libwinpr-rpc.so.0.1.0
	libcdio_paranoia.so.1 -> libcdio_paranoia.so.1.0.0
	libflite_cmu_us_awb.so.1 -> libflite_cmu_us_awb.so.2.0.0
	libjasper.so.1 -> libjasper.so.1.0.0
	libflite.so.1 -> libflite.so.2.0.0
	libutempter.so.0 -> libutempter.so.1.1.6
	libfreerdp-common.so.1.1.0 -> libfreerdp-common.so.1.1.0-beta1
	libXt.so.6 -> libXt.so.6.0.0
	libraw1394.so.11 -> libraw1394.so.11.1.0
	libgnome-desktop-3.so.12 -> libgnome-desktop-3.so.12.0.0
	libopencv_ml.so.2.4 -> libopencv_ml.so.2.4.9
	libgd.so.3 -> libgd.so.3.0.0
	libmpfr.so.4 -> libmpfr.so.4.1.4
	libavc1394.so.0 -> libavc1394.so.0.3.0
	liblua5.2.so.0 -> liblua5.2.so.0.0.0
	libdatrie.so.1 -> libdatrie.so.1.3.3
	libevent-2.0.so.5 -> libevent-2.0.so.5.1.9
	libxcb-randr.so.0 -> libxcb-randr.so.0.1.0
	libyelp.so.0 -> libyelp.so.0.0.0
	libwebpmux.so.1 -> libwebpmux.so.1.0.2
	libenchant.so.1 -> libenchant.so.1.6.0
	libqmi-glib.so.1 -> libqmi-glib.so.1.3.0
	libnm-glib.so.4 -> libnm-glib.so.4.9.0
	libgstrtp-1.0.so.0 -> libgstrtp-1.0.so.0.803.0
	libImath-2_2.so.12 -> libImath-2_2.so.12.0.0
	libcanberra-gtk3.so.0 -> libcanberra-gtk3.so.0.1.9
	libudisks2.so.0 -> libudisks2.so.0.0.0
	libbabeltrace-ctf-text.so.1 -> libbabeltrace-ctf-text.so.1.0.0
	libXvMC.so.1 -> libXvMC.so.1.0.0
	libunity-extras.so.9 -> libunity-extras.so.9.0.2
	libspeex.so.1 -> libspeex.so.1.5.0
	libzmq.so.5 -> libzmq.so.5.0.0
	libspice-server.so.1 -> libspice-server.so.1.10.0
	libraptor2.so.0 -> libraptor2.so.0.0.0
	libvpx.so.3 -> libvpx.so.3.0.0
	libdfu.so.1 -> libdfu.so.1.0.1
	libmp3lame.so.0 -> libmp3lame.so.0.0.0
	libpcreposix.so.3 -> libpcreposix.so.3.13.2
	libgio-2.0.so.0 -> libgio-2.0.so.0.4800.2
	libsamplerate.so.0 -> libsamplerate.so.0.1.8
	libfreerdp-locale.so.1.1 -> libfreerdp-locale.so.1.1.0
	libndp.so.0 -> libndp.so.0.0.2
	libkrb5support.so.0 -> libkrb5support.so.0.1
	libopenjpeg.so.5 -> libopenjpeg.so.1.5.2
	libcairomm-1.0.so.1 -> libcairomm-1.0.so.1.4.0
	libvisual-0.4.so.0 -> libvisual-0.4.so.0.0.0
	libunity-gtk2-parser.so.0 -> libunity-gtk2-parser.so.0.0.0
	libjbig.so.0 -> libjbig.so.0
	libunity-webapps.so.0 -> libunity-webapps.so.0.0.0
	libdcerpc-server.so.0 -> libdcerpc-server.so.0.0.1
	libedataserverui-1.2.so.1 -> libedataserverui-1.2.so.1.0.0
	libcap-ng.so.0 -> libcap-ng.so.0.0.0
	libsigsegv.so.2 -> libsigsegv.so.2.0.3
	libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.21
	libsnmp.so.30 -> libsnmp.so.30.0.3
	libdotconf.so.0 -> libdotconf.so.0.0.1
	libgstbase-1.0.so.0 -> libgstbase-1.0.so.0.803.0
	libpcap.so.0.8 -> libpcap.so.1.7.4
	libusbredirparser.so.1 -> libusbredirparser.so.1.0.0
	libheimntlm.so.0 -> libheimntlm.so.0.1.0
	libgexiv2.so.2 -> libgexiv2.so.2.0.0
	libfdt.so.1 -> libfdt-1.4.0.so
	libyajl.so.2 -> libyajl.so.2.1.0
	libxcb-shape.so.0 -> libxcb-shape.so.0.0.0
	libsoup-gnome-2.4.so.1 -> libsoup-gnome-2.4.so.1.7.0
	libgstcodecparsers-1.0.so.0 -> libgstcodecparsers-1.0.so.0.803.0
	libarchive.so.13 -> libarchive.so.13.1.2
	libXmu.so.6 -> libXmu.so.6.2.0
	libjpeg.so.8 -> libjpeg.so.8.0.2
	libXss.so.1 -> libXss.so.1.0.0
	libhogweed.so.4 -> libhogweed.so.4.2
	libavresample-ffmpeg.so.2 -> libavresample-ffmpeg.so.2.1.0
	libcaca++.so.0 -> libcaca++.so.0.99.19
	libebook-1.2.so.16 -> libebook-1.2.so.16.3.1
	libplist.so.3 -> libplist.so.3.0.0
	libfribidi.so.0 -> libfribidi.so.0.3.6
	libgsturidownloader-1.0.so.0 -> libgsturidownloader-1.0.so.0.803.0
	libgirepository-1.0.so.1 -> libgirepository-1.0.so.1.0.0
	libopencore-amrnb.so.0 -> libopencore-amrnb.so.0.0.3
	libwayland-cursor.so.0 -> libwayland-cursor.so.0.0.0
	libfontconfig.so.1 -> libfontconfig.so.1.9.0
	libpipeline.so.1 -> libpipeline.so.1.4.1
	libQtNetwork.so.4 -> libQtNetwork.so.4.8.7
	libsasl2.so.2 -> libsasl2.so.2.0.25
	libodfgen-0.1.so.1 -> libodfgen-0.1.so.1.0.6
	libisccc.so.140 -> libisccc.so.140.0.4
	libxcb-present.so.0 -> libxcb-present.so.0.0.0
	libpolkit-gobject-1.so.0 -> libpolkit-gobject-1.so.0.0.0
	libfftw3.so.3 -> libfftw3.so.3.4.4
	libframe.so.6 -> libframe.so.6.0.0
	libicalvcal.so.1 -> libicalvcal.so.1.0.1
	libcolord.so.2 -> libcolord.so.2.0.4
	libappindicator3.so.1 -> libappindicator3.so.1.0.0
	libxklavier.so.16 -> libxklavier.so.16.4.0
	libbs2b.so.0 -> libbs2b.so.0.0.0
	libexpatw.so.1 -> libexpatw.so.1.6.0
	liblsan.so.0 -> liblsan.so.0.0.0
	libsmbclient.so.0 -> libsmbclient.so.0.2.3
	libzeitgeist-1.0.so.1 -> libzeitgeist-1.0.so.1.1.4
	libflite_cmu_us_rms.so.1 -> libflite_cmu_us_rms.so.2.0.0
	libIexMath-2_2.so.12 -> libIexMath-2_2.so.12.0.0
	libregistry.so.0 -> libregistry.so.0.0.1
	liblz4.so.1 -> liblz4.so.1.7.1
	libxenstore.so.3.0 -> libxenstore.so.3.0.3
	libnm-glib-vpn.so.1 -> libnm-glib-vpn.so.1.2.0
	libcdr-0.1.so.1 -> libcdr-0.1.so.1.0.2
	libQtCore.so.4 -> libQtCore.so.4.8.7
	libgstfft-1.0.so.0 -> libgstfft-1.0.so.0.803.0
	libgtkspell3-3.so.0 -> libgtkspell3-3.so.0.1.0
	libdns.so.162 -> libdns.so.162.1.3
	libv4lconvert.so.0 -> libv4lconvert.so.0.0.0
	libcrystalhd.so.3 -> libcrystalhd.so.3.6
	libfreetype.so.6 -> libfreetype.so.6.12.1
	libnetsnmphelpers.so.30 -> libnetsnmphelpers.so.30.0.3
	libfftw3_threads.so.3 -> libfftw3_threads.so.3.4.4
	libtdb.so.1 -> libtdb.so.1.3.8
	libgstbadaudio-1.0.so.0 -> libgstbadaudio-1.0.so.0.803.0
	libhpip.so.0 -> libhpip.so.0.0.1
	libgrail.so.6 -> libgrail.so.6.0.0
	libunity-settings-daemon.so.1 -> libunity-settings-daemon.so.1.0.0
	libdmapsharing-3.0.so.2 -> libdmapsharing-3.0.so.2.9.34
	libspeexdsp.so.1 -> libspeexdsp.so.1.5.0
	libmng.so.2 -> libmng.so.2.0.2
	libicui18n.so.55 -> libicui18n.so.55.1
	libUbuntuToolkit.so.5 -> libUbuntuToolkit.so.5.5.0
	libQt5Multimedia.so.5 -> libQt5Multimedia.so.5.5.1
	libmplex2-2.1.so.0 -> libmplex2-2.1.so.0.0.0
	libQt5Feedback.so.5 -> libQt5Feedback.so.5.0.0
	libQt5Test.so.5 -> libQt5Test.so.5.5.1
	libclucene-shared.so.1 -> libclucene-shared.so.2.3.3.4
	libelf.so.1 -> libelf-0.165.so
	libusbmuxd.so.4 -> libusbmuxd.so.4.0.0
	libopencv_features2d.so.2.4 -> libopencv_features2d.so.2.4.9
	libdbusmenu-qt.so.2 -> libdbusmenu-qt.so.2.6.0
	libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.10.5
	libjack.so.0 -> libjack.so.0.1.0
	libguilereadline-v-18.so.18 -> libguilereadline-v-18.so.18.0.0
	libXfont.so.1 -> libXfont.so.1.4.1
	libnetsnmptrapd.so.30 -> libnetsnmptrapd.so.30.0.3
	libgthread-2.0.so.0 -> libgthread-2.0.so.0.4800.2
	libiec61883.so.0 -> libiec61883.so.0.1.1
	libicule.so.55 -> libicule.so.55.1
	libxcb-dri3.so.0 -> libxcb-dri3.so.0.0.0
	libcapnpc-0.5.3.so -> libcapnpc-0.5.3.so
	libetonyek-0.1.so.1 -> libetonyek-0.1.so.1.0.6
	libplc4.so -> libplc4.so
	libgstinsertbin-1.0.so.0 -> libgstinsertbin-1.0.so.0.803.0
	libdouble-conversion.so.1 -> libdouble-conversion.so.1.0
	libdee-1.0.so.4 -> libdee-1.0.so.4.2.1
	libisl.so.15 -> libisl.so.15.1.1
	libwebkit2gtk-4.0.so.37 -> libwebkit2gtk-4.0.so.37.24.9
	libcurl-gnutls.so.4 -> libcurl-gnutls.so.4.4.0
	libfftw3f.so.3 -> libfftw3f.so.3.4.4
	libvisio-0.1.so.1 -> libvisio-0.1.so.1.0.5
	libgnomekbd.so.8 -> libgnomekbd.so.8.0.0
	libflite_cmulex.so.1 -> libflite_cmulex.so.2.0.0
	libui.so.1 -> libui.so.1.0.0
	libfftw3_omp.so.3 -> libfftw3_omp.so.3.4.4
	libcilkrts.so.5 -> libcilkrts.so.5.0.0
	libIlmImf-2_2.so.22 -> libIlmImf-2_2.so.22.0.0
	libgphoto2_port.so.12 -> libgphoto2_port.so.12.0.0
	liblirc_client.so.0 -> liblirc_client.so.0.2.1
	libQtXmlPatterns.so.4 -> libQtXmlPatterns.so.4.8.7
	libgiomm-2.4.so.1 -> libgiomm-2.4.so.1.3.0
	libcairo-gobject.so.2 -> libcairo-gobject.so.2.11400.6
	libtbbmalloc.so.2 -> libtbbmalloc.so.2
	libfwupd.so.1 -> libfwupd.so.1.0.1
	liba52-0.7.4.so -> liba52-0.7.4.so
	libOxideQtCore.so.0 -> libOxideQtCore.so.0
	libhardware.so.2 -> libhardware.so.2.0.0
	libtotem-plparser-mini.so.18 -> libtotem-plparser-mini.so.18.1.0
	libdns-pkcs11.so.162 -> libdns-pkcs11.so.162.1.3
	libtiff.so.5 -> libtiff.so.5.2.4
	libdca.so.0 -> libdca.so.0.0.0
	liblqr-1.so.0 -> liblqr-1.so.0.3.2
	libgobject-2.0.so.0 -> libgobject-2.0.so.0.4800.2
	libisccfg.so.140 -> libisccfg.so.140.3.0
	libcc1.so.0 -> libcc1.so.0.0.0
	libclutter-1.0.so.0 -> libclutter-1.0.so.0.2400.2
	libgcab-1.0.so.0 -> libgcab-1.0.so.0.0.0
	libbamf3.so.2 -> libbamf3.so.2.0.0
	libboost_thread.so.1.58.0 -> libboost_thread.so.1.58.0
	libmagic.so.1 -> libmagic.so.1.0.0
	libQt5DBus.so.5 -> libQt5DBus.so.5.5.1
	libshout.so.3 -> libshout.so.3.2.0
	libvorbis.so.0 -> libvorbis.so.0.4.8
	libcheese-gtk.so.25 -> libcheese-gtk.so.25.0.3
	libbabeltrace-lttng-live.so.1 -> libbabeltrace-lttng-live.so.1.0.0
	libexiv2.so.14 -> libexiv2.so.14.0.0
	libaccount-plugin-1.0.so.0 -> libaccount-plugin-1.0.so.0.1.0
	libnetfilter_conntrack.so.3 -> libnetfilter_conntrack.so.3.5.0
	libcupsmime.so.1 -> libcupsmime.so.1
	libicudata.so.55 -> libicudata.so.55.1
	libsignon-plugins-common.so.1 -> libsignon-plugins-common.so.1.0.0
	libfreerdp-utils.so.1.1 -> libfreerdp-utils.so.1.1.0
	libglibmm_generate_extra_defs-2.4.so.1 -> libglibmm_generate_extra_defs-2.4.so.1.3.0
	libpanelw.so.5 -> libpanelw.so.5.9
	libgstbasecamerabinsrc-1.0.so.0 -> libgstbasecamerabinsrc-1.0.so.0.803.0
	libcompizconfig_gsettings_backend.so -> libcompizconfig_gsettings_backend.so
	libXfixes.so.3 -> libXfixes.so.3.1.0
	libmm-glib.so.0 -> libmm-glib.so.0.2.0
	libcroco-0.6.so.3 -> libcroco-0.6.so.3.0.1
	libgstmpegts-1.0.so.0 -> libgstmpegts-1.0.so.0.803.0
	libxcb-image.so.0 -> libxcb-image.so.0.0.0
	libhx509.so.5 -> libhx509.so.5.0.0
	libunwind.so.8 -> libunwind.so.8.0.1
	libQt5Qml.so.5 -> libQt5Qml.so.5.5.1
	libnetsnmp.so.30 -> libnetsnmp.so.30.0.3
	libsbc.so.1 -> libsbc.so.1.2.1
	libsmime3.so -> libsmime3.so
	libebackend-1.2.so.10 -> libebackend-1.2.so.10.0.0
	libavformat-ffmpeg.so.56 -> libavformat-ffmpeg.so.56.40.101
	libQtScript.so.4 -> libQtScript.so.4.8.7
	libatkmm-1.6.so.1 -> libatkmm-1.6.so.1.1.0
	libevdev.so.2 -> libevdev.so.2.1.12
	libhyphen.so.0 -> libhyphen.so.0.3.0
	libcheese.so.8 -> libcheese.so.8.0.3
	libcmis-c-0.5.so.5 -> libcmis-c-0.5.so.5.0.0
	librtmp.so.1 -> librtmp.so.1
	libgstapp-1.0.so.0 -> libgstapp-1.0.so.0.803.0
	libyaml-0.so.2 -> libyaml-0.so.2.0.4
	libfreerdp-codec.so.1.1 -> libfreerdp-codec.so.1.1.0
	libraw_r.so.15 -> libraw_r.so.15.0.0
	libwhoopsie.so.0 -> libwhoopsie.so.0.0
	libdcerpc-binding.so.0 -> libdcerpc-binding.so.0.0.1
	libkpathsea.so.6 -> libkpathsea.so.6.2.1
	libmenu.so.5 -> libmenu.so.5.9
	libmetacity-private.so.3 -> libmetacity-private.so.3.0.0
	libxshmfence.so.1 -> libxshmfence.so.1.0.0
	libzbar.so.0 -> libzbar.so.0.2.0
	libsmbconf.so.0 -> libsmbconf.so.0
	libqpdf.so.17 -> libqpdf.so.17.0.0
	libfreehand-0.1.so.1 -> libfreehand-0.1.so.1.0.1
	libfwup.so.0 -> libfwup.so.0.5
	libksba.so.8 -> libksba.so.8.11.4
	libgee-0.8.so.2 -> libgee-0.8.so.2.5.1
	libsonic.so.0 -> libsonic.so.0.2.0
	libmpeg2convert.so.0 -> libmpeg2convert.so.0.0.0
	libhybris-common.so.1 -> libhybris_ics.so
	libdebconfclient.so.0 -> libdebconfclient.so.0.0.0
	libgstcontroller-1.0.so.0 -> libgstcontroller-1.0.so.0.803.0
	libpango-1.0.so.0 -> libpango-1.0.so.0.3800.1
	libdrm_nouveau.so.2 -> libdrm_nouveau.so.2.0.0
	libnetsnmpmibs.so.30 -> libnetsnmpmibs.so.30.0.3
	libwpg-0.3.so.3 -> libwpg-0.3.so.3.0.1
	libpulse-mainloop-glib.so.0 -> libpulse-mainloop-glib.so.0.0.5
	libzvbi-chains.so.0 -> libzvbi-chains.so.0.0.0
	libwayland-client.so.0 -> libwayland-client.so.0.3.0
	libcogl-pango.so.20 -> libcogl-pango.so.20.4.1
	libsamba-passdb.so.0 -> libsamba-passdb.so.0.24.1
	libfcitx-config.so.4 -> libfcitx-config.so.4.1
	libubsan.so.0 -> libubsan.so.0.0.0
	libnuma.so.1 -> libnuma.so.1.0.0
	libasan.so.2 -> libasan.so.2.0.0
	libjson-glib-1.0.so.0 -> libjson-glib-1.0.so.0.102.0
	libmpg123.so.0 -> libmpg123.so.0.41.2
	libgsttag-1.0.so.0 -> libgsttag-1.0.so.0.803.0
	libepoxy.so.0 -> libepoxy.so.0.0.0
	libbabeltrace-ctf.so.1 -> libbabeltrace-ctf.so.1.0.0
	libexttextcat-2.0.so.0 -> libexttextcat-2.0.so.0.0.0
	liboauth.so.0 -> liboauth.so.0.8.7
	libtcl8.6.so -> libtcl8.6.so.0
	libdbus-glib-1.so.2 -> libdbus-glib-1.so.2.3.3
	libwinpr-file.so.0.1 -> libwinpr-file.so.0.1.0
	libgailutil.so.18 -> libgailutil.so.18.0.1
	libunity-gtk3-parser.so.0 -> libunity-gtk3-parser.so.0.0.0
	libICE.so.6 -> libICE.so.6.3.0
	libQt5WebKitWidgets.so.5 -> libQt5WebKitWidgets.so.5.5.1
	libedit.so.2 -> libedit.so.2.0.53
	libshine.so.3 -> libshine.so.3.0.1
	libevview3.so.3 -> libevview3.so.3.0.0
	libldb.so.1 -> libldb.so.1.1.24
	libaccounts-glib.so.0 -> libaccounts-glib.so.0.1.3
	libieee1284.so.3 -> libieee1284.so.3.2.2
	libdbusmenu-qt5.so.2 -> libdbusmenu-qt5.so.2.6.0
	libgstplayer-1.0.so.0 -> libgstplayer-1.0.so.0.803.0
	libfreerdp-gdi.so.1.1 -> libfreerdp-gdi.so.1.1.0
	liblua5.1-lpeg.so.2 -> liblua5.1-lpeg.so.2.0.0
	libcolamd.so.2.9.1 -> libcolamd.so.2.9.1
	libunity-misc.so.4 -> libunity-misc.so.4.1.0
	libvte-2.91.so.0 -> libvte-2.91.so.0.4200.5
	libnetsnmpagent.so.30 -> libnetsnmpagent.so.30.0.3
	libkate.so.1 -> libkate.so.1.3.0
	libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.4800.2
	libsrtp.so.0 -> libsrtp.so.0.0
	libcairo.so.2 -> libcairo.so.2.11400.6
	libgdk_pixbuf_xlib-2.0.so.0 -> libgdk_pixbuf_xlib-2.0.so.0.3200.2
	libaspell.so.15 -> libaspell.so.15.2.0
	libQt5Sql.so.5 -> libQt5Sql.so.5.5.1
	libflite_usenglish.so.1 -> libflite_usenglish.so.2.0.0
	libsamba-util.so.0 -> libsamba-util.so.0.0.1
	libsgutils2.so.2 -> libsgutils2.so.2.0.0
	libxapian.so.22 -> libxapian.so.22.7.0
	libsoup-2.4.so.1 -> libsoup-2.4.so.1.7.0
	libappstream-glib.so.8 -> libappstream-glib.so.8.0.6
	libeot.so.0 -> libeot.so.0.0.0
	libxkbcommon.so.0 -> libxkbcommon.so.0.0.0
	libopencv_flann.so.2.4 -> libopencv_flann.so.2.4.9
	libX11-xcb.so.1 -> libX11-xcb.so.1.0.0
	librbd.so.1 -> librbd.so.1.0.0
	libQt5OpenGL.so.5 -> libQt5OpenGL.so.5.5.1
	libsigc-2.0.so.0 -> libsigc-2.0.so.0.0.0
	libheimbase.so.1 -> libheimbase.so.1.0.0
	libhud.so.2 -> libhud.so.2.0.0
	libwebrtc_audio_processing.so.0 -> libwebrtc_audio_processing.so.0.0.0
	libchromaprint.so.0 -> libchromaprint.so.0.2.3
	liborc-test-0.4.so.0 -> liborc-test-0.4.so.0.25.0
	libwinpr-heap.so.0.1 -> libwinpr-heap.so.0.1.0
	libtalloc.so.2 -> libtalloc.so.2.1.5
	libwinpr-input.so.0.1 -> libwinpr-input.so.0.1.0
	libdrm_radeon.so.1 -> libdrm_radeon.so.1.0.1
	libsamba-hostconfig.so.0 -> libsamba-hostconfig.so.0.0.1
	libfreerdp-core.so.1.1 -> libfreerdp-core.so.1.1.0
	libgnome-menu-3.so.0 -> libgnome-menu-3.so.0.0.1
	libMagickCore-6.Q16.so.2 -> libMagickCore-6.Q16.so.2.0.0
	libdbusmenu-glib.so.4 -> libdbusmenu-glib.so.4.0.12
	libkj-0.5.3.so -> libkj-0.5.3.so
	libxenlight-4.6.so -> libxenlight-4.6.so
	libpspell.so.15 -> libpspell.so.15.2.0
	libQtDeclarative.so.4 -> libQtDeclarative.so.4.8.7
	libmediaart-2.0.so.0 -> libmediaart-2.0.so.0.900.0
	libfreerdp-crypto.so.1.1 -> libfreerdp-crypto.so.1.1.0
	libpytalloc-util.so.2 -> libpytalloc-util.so.2.1.5
/usr/lib/x86_64-linux-gnu/mesa-egl:
	libEGL.so.1 -> libEGL.so.1.0.0
/usr/lib/x86_64-linux-gnu/mesa:
	libGL.so.1 -> libGL.so.1.2.0
/lib32:
	libmemusage.so -> libmemusage.so
/sbin/ldconfig.real: /lib32/ld-2.23.so is the dynamic linker, ignoring

	ld-linux.so.2 -> ld-2.23.so
	libnsl.so.1 -> libnsl-2.23.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libSegFault.so -> libSegFault.so
	libBrokenLocale.so.1 -> libBrokenLocale-2.23.so
	libm.so.6 -> libm-2.23.so
	librt.so.1 -> librt-2.23.so
	libnss_files.so.2 -> libnss_files-2.23.so
	libnss_compat.so.2 -> libnss_compat-2.23.so
	libcrypt.so.1 -> libcrypt-2.23.so
	libpcprofile.so -> libpcprofile.so
	libpthread.so.0 -> libpthread-2.23.so
	libnss_nis.so.2 -> libnss_nis-2.23.so
	libutil.so.1 -> libutil-2.23.so
	libnss_hesiod.so.2 -> libnss_hesiod-2.23.so
	libanl.so.1 -> libanl-2.23.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.23.so
	libdl.so.2 -> libdl-2.23.so
	libc.so.6 -> libc-2.23.so
	libresolv.so.2 -> libresolv-2.23.so
	libcidn.so.1 -> libcidn-2.23.so
	libnss_dns.so.2 -> libnss_dns-2.23.so
/usr/lib32:
	libmpxwrappers.so.0 -> libmpxwrappers.so.0.0.0
	libgomp.so.1 -> libgomp.so.1.0.0
	libatomic.so.1 -> libatomic.so.1.1.0
	libstdc++.so.6 -> libstdc++.so.6.0.21
	libquadmath.so.0 -> libquadmath.so.0.0.0
	libitm.so.1 -> libitm.so.1.0.0
	libmpx.so.0 -> libmpx.so.0.0.0
	libz.so.1 -> libz.so.1.2.8
	libgcc_s.so.1 -> libgcc_s.so.1
	libcilkrts.so.5 -> libcilkrts.so.5.0.0
	libubsan.so.0 -> libubsan.so.0.0.0
	libasan.so.2 -> libasan.so.2.0.0
/libx32:
	libmemusage.so -> libmemusage.so
/sbin/ldconfig.real: /libx32/ld-2.23.so is the dynamic linker, ignoring

	ld-linux-x32.so.2 -> ld-2.23.so
	libnsl.so.1 -> libnsl-2.23.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libSegFault.so -> libSegFault.so
	libBrokenLocale.so.1 -> libBrokenLocale-2.23.so
	libm.so.6 -> libm-2.23.so
	librt.so.1 -> librt-2.23.so
	libnss_files.so.2 -> libnss_files-2.23.so
	libnss_compat.so.2 -> libnss_compat-2.23.so
	libcrypt.so.1 -> libcrypt-2.23.so
	libpcprofile.so -> libpcprofile.so
	libpthread.so.0 -> libpthread-2.23.so
	libnss_nis.so.2 -> libnss_nis-2.23.so
	libutil.so.1 -> libutil-2.23.so
	libnss_hesiod.so.2 -> libnss_hesiod-2.23.so
	libanl.so.1 -> libanl-2.23.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.23.so
	libdl.so.2 -> libdl-2.23.so
	libc.so.6 -> libc-2.23.so
	libresolv.so.2 -> libresolv-2.23.so
	libmvec.so.1 -> libmvec-2.23.so
	libcidn.so.1 -> libcidn-2.23.so
	libnss_dns.so.2 -> libnss_dns-2.23.so
/usr/libx32:
	libgomp.so.1 -> libgomp.so.1.0.0
	libatomic.so.1 -> libatomic.so.1.1.0
	libstdc++.so.6 -> libstdc++.so.6.0.21
	libquadmath.so.0 -> libquadmath.so.0.0.0
	libitm.so.1 -> libitm.so.1.0.0
	libgcc_s.so.1 -> libgcc_s.so.1
	libcilkrts.so.5 -> libcilkrts.so.5.0.0
	libubsan.so.0 -> libubsan.so.0.0.0
	libasan.so.2 -> libasan.so.2.0.0
/lib:
/usr/lib:
	libMonoSupportW.so -> libMonoSupportW.so
	libMonoPosixHelper.so -> libMonoPosixHelper.so
	libnetpbm.so.10 -> libnetpbm.so.10.0
```

**4.** Create api documentation

First pull in Doxygen (this step is not listed in the instructions)

```
sudo apt-get install doxygen
```

Type 'Y' when prompted.

Then type:

```
mkdir build
cd build
cmake -DWITH_DOC=ON ..
make doc
```

I created the Doxygen output and hosted it [here](http://pfefferz.github.io/dlt-daemon-doxygen-built/).

**Test it**

**1.** Create dltdemo.c or clone [https://github.com/pfefferz/dltdemo](http://github.com/pfefferz/dltdemo)

dltdemo.c at [link](http://github.com/pfefferz/dltdemo/blob/master/dltdemo.c)

**2.** Make it with

```
gcc dltdemo.c -o dltdemo -ldlt
```

**3.** Test it with

```
touch /tmp/dlt
./dltdemo
xxd -c 34 /tmp/dlt
```

Note: when I ran ./dltdemo without touching /tmp/dlt I got an error.

**References**

-   The install instructions by Alexander Wenzel <Alexander.AW.Wenzel@bmw.de> are at [link](http://raw.githubusercontent.com/GENIVI/dlt-daemon/master/INSTALL)
    
-   The user manual also by Alexander is at [link](http://raw.githubusercontent.com/GENIVI/dlt-daemon/master/doc/dlt_user_manual.txt)
    
-   Used the free HTML Escape / Unescape tool at [link](http://www.freeformatter.com/html-escape.html) to put the post together
    

**Additional Info**

-   The dlt-daemon comes from GENIVI. From [link,](http://www.genivi.org/) GENIVI is a "nonprofit industry alliance committed to driving the broad adoption of open source, In-Vehicle Infotainment (IVI) software and providing open technology for the connected car." There members are listed [here](http://www.genivi.org/genivi-members).
    
-   The DLT Wiki can be found at this [link](http://at.projects.genivi.org/wiki/display/PROJ/Diagnostic+Log+and+Trace).