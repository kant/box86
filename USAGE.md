Usage
----

There are many environnement variable to control Box86 behavour. 

##### BOX86_LOG
Controls the Verbose level of the log
 * 0
 * NONE : No message (exept some fatal error)
 * 1
 * INFO : Current default. Show some log
 * 2
 * DEBUG : Verbose a lot of stuffs (like relocations or function called)
 * 3
 * DUMP : All DEBUG plus DUMP of all ELF Info

#### BOX86_LD_LIBRARY_PATH
Controls the folder scanned to look for x86 libs. Default is current folder and `lib` in current folder.
Also `/usr/lib/i386-linux-gnu` and `/lib/i386-linux-gnu` are added if they exists

#### BOX86_PATH
Controls the folder scanned to look for x86 executable. Default is current folder and `bin` in current folder.

#### BOX86_DLSYM_ERROR
* 0 : default. Don't log `dlsym` error
* 1 : Log dlsym error

#### BOX86_TRACE_FILE
Send all log and trace to a file instead of `stdout`

#### BOX86_TRACE
Only on build with trace enabled. Trace allow the logging of all instruction execute, along with register dump
* 0 : No trace
* 1 : Trace enabled. The trace start after the init of all depending libs is done
* symbolname : Trace only `symbolname` (trace is disable if the symbol is not found)
* 0xXXXXXXX-0xYYYYYYY : trace only between the 2 addresses

#### BOX86_TRACE_INIT
Use BOX86_TRACE_INIT instead of BOX_TRACE to start trace before init of Libs and main program
* 0 : No trace
* 1 : Trace enabled. The trace start with the init of all depending libs is done

#### BOX86_TRACE_START
Only on build with trace enabled.
* NNNNNNN : Start trace anly after NNNNNNNN opcode execute (number is an `uint64_t`)

#### BOX86_TRACE_XMM
Only on build with trace enabled.
* 0 : Default, the XMM (i.e. SSE/SSE2) register will not be logged with the general and x87 registers
* 1 : Dump the XMM registers

#### BOX86_LOAD_ADDR
Try to load at 0xXXXXXX main binaray (if binary is a PIE)
* 0xXXXXXXXX the load address (only active on PIE programs)

#### BOX86_NOSIGSEGV
To disable handling of SigSEGV (to ease debugging mainly)
* 0 : default, let x86 program set sighandler for SEGV
* 1 : disable handling of SigSEGV

#### BOX86_X11COLOR16
PANDORA only: to try convert X11 color from 32 bits to 16 bits (to avoid light green on light cyan windows
* 0 : default, don't touch X11 colors
* 1 : Change colors arguments in XSetForeground, XSetBackground and XCreateGC
