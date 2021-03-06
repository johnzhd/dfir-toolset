# dfir-toolset
I'm collecting, sorting, and making order out of the available tools.  I'm housing my experience with opensource tools with an emphasis on Linux as the DF host OS.  Much of this comes from Remnux and SIFT.  A few come from Kali.  Others are pulled straight from Github.  I am working to eliminate the noise caused by orphaned, redundant, or superceded all-in-one software.  
  
**Distributions for Security tools**
* Security Onion
* SIFT + Remnux
* DEFT (Windows)   
    
**Mounting dd or vm snapshot disk images**  
* xmount (rw w/ cache mount EWF,VMDK,etc)
* kpartx
* mount -o offset=X

**Volume Shadow Copy browsing**  
* libvshadow FUSE mounting  
  
**Checking file signed signatures**  
* Authenticode Tools (Didier Stevens)
* Process Manager (Windows SysInternals)
* chktrust (Mono) for Linux

**Linux-based Browser Artifact tools omitted since toolkits like FTK and Encase dwarf them**  
    
**Scan for IOC, hashing, and hash lookups**  
* Parse IOC's from reports: IOCextractor, ioc-parser
* Define signatures: YaraGenerator, Autorule, Rule Editor
* Offline-Scan: yara (IOC), clamAV
* Metadata: trID (determine filetype), exifTool, missidentify (find PE in files not named exe)
* Gen Hashes: ssdeep(fuzzy hashes) w pydeep for bindings, md5deep (recursive md5 checks) / hashdeep (audit across multiple sets), hash_id (guess hash algorithm used), 
* Hashes Query: nsrllookup (Whitelist of non-malicious hashes) requiring nsrlsvr, virustotal-search, vtTool.py, Automater (search by URL, IP, Hash)
  
**File Forensics**  
* Sleuthkit with Autopsy 
* scalpel (not foremost anymore)
* safecopy (file restore from damaged sources)
* analyze mft (parse the mft from an ntfs FS)
* hachoir (Read windows metadata)
* Rifiuti (recycle bin analysis)
* testdisk (restore lost partitions), kpartx
* extundelete (ext3/4 file rest), recoverjpeg, vinetto (thumbs.db examiner)
  
**Handle Network Interactions**  
* Sniffing: ngrep, tcpdump, tcpick(passive sniffer), tcptrack, driftnet, tshark (terminal wshark),
dsniff(captures user data over common protos), aircrack-ng (WEP and WPA-PSK keys cracking), 
yaraPcap.py (http streams)
* Analyze/Exec pcap: ssldump(decode ssl/tls records), tcpxtract, tcpreplay (can't estab session), tcptrace (stats on pcaps), tcpflow (deconstruct), tcpcopy (resend data), chaosreader.pl (dump http conversations), CapTipper (emulate web svr of what's in pcap), Xplico (extract data per protocol), networkminer, scapy (BYO packets), editcap (convert formats)
* Services: FakeDNS, Nginx, fakeMail, Honeyd, INetSim
* Reporting: etherape(graphical network monitor), Wireshark
* MITM: Burp Proxy (manipulate http between web and client), ettercap (content filtering on fly), sslsniff (MITM attacker), mitmproxy, sslcaudit (test ssl), sslstrip, sslsplit
* Honeypots: Thug (docker based honeypot), Dionaea (honeypot), Kippo (SSH), Modern Honeypot Network
* Miscellaneous network: prettyping, Netcat, stunnel, p0f(passive remote fingerprinting), netwox(swiss-army knife of routines), lft(smart traceroute), passivedns, tcpstat(stats on NIC), 
  
**Windows Event Logger analysis**  
* Event Log Explorer - eventlogxp.com
* logparser - MS
* Log Parser Lizard - gui for logparser
* Mandiant Highlighter
* PsLogList MS
  
**Linux Event Log analysis**  
* Lsevt, evtx_parser, python-evtx
  
**Extract and Decode Artifacts**  
* Deobfuscate: unXOR, XORStrings, ex_pe_xor, XORSearch, brxor.py, xortool, NoMoreXOR, XORBruteForcer, Balbuzard
* Extract strings: strdeobj, pestr, strings.exe (wine)

**Examine Document Files**  
* PDF: AnalyzePDF, Pdfobjflow, pdfid, pdf-parser, peepdf, Origami, PDF X-RAY, PDFtk, swf_mastah, qpdf, pdfresurrect
* MS Office: officeparser, pyOLEScanner.py, oletools, libolecf, oledump, emldump, MSGConvert, base64dump.py, olefile, offcat/offviz(Win)
    Shellcode: sctest, unicode2hex-escaped, unicode2raw, dism-this, shellcode2exe
    Flash: xxxswf, SWF Tools, RABCDAsm, extract_swf, Flare(decompiler of Flash), flasm(disassembles Flash)
* Java: Java Cache IDX Parser, JD-GUI Java Decompiler, JAD Java Decompiler, Javassist, CFR
* JavaScript: Extract/unpack: Extractscripts, extractjs.rb (Oragami), jsunpack-n (pdf.py)
              Debug/manip: Rhino Debugger, Firebug, Didier's SpiderMonkey, V8, js Beautifier, JSDetox, 
    
**Mail**  
* readpst
* Digital Forensic Framework by Arxsys
* mpack/munpack for mime

**Binary/Hex Editors**  
* Binary: wxHexEditor, VBinDiff
* Hex: bless, exhexeditor

**Examine Memory Snapshots**  
* Volatility frameworks/wrappers  
  * Evolve - Creates sqllite db output and web frontend  
  * vshot - becoming antiquated.  Hand edit to add modules  
  * Mantaray - becoming antiquated  
  * Bulk_extractor modules for grabbing types of data  with beviewer for viz
  * Volatility module add-ons of notability  
    * mimikatz detection - RealityNet/hotoloti  
    * Rat detection - FabienPerigaud  
    * At jobs - binglot/misc  
    * ShimcacheMemory  
    * IOC scan - openioc_scan  
* Rekall (Volatility fork relying on API's and not scanning to find evidence)  
* findaes, AESKeyFinder, RSAKeyFinder, VolDiff  
* pdgmail (gmail from mem)  

**Investigate Malware**  
* System: Unhide(detect hidden processes), sysdig (strace + tcpdump + htop + iftop + lsof)
* Find anomalies: signsrch, pescanner, exescan, pev suite, peframe, pedump, disitool (alter digsig)
* Trace: strace, ltrace
* Static Analysis: Radare, Pyew, Bokken(front-end to radare/pyew), m2elf
* Disassemblers: Vivisect, Udis86, objdump, jad (java decom), recstudio, mastiff, captone, EmilPRO, distorm, Decompyle++ (python disassembler)
* Debug: Evan s Debugger (EDB), GNU Project Debugger (GDB), pyelftools (ELF parsing), elfutils: Object Viewer, lida
* Packers: UPX, Bytehist, Density Scout, PackerID, Packer Attacker, Burneye (vs burncrack, burninhell, burndump)
* Investigate: RATDecoders, readpe.py, PyInstaller Extractor, DC3-MWCP
* Maltrieve (DL Malware samples), Viper (managing and exploring malware samples), 
* Behavioral analysis: Procdot for visual report, ThreatExpert (online), Cuckoo (offline)

**Password cracking**  
* hydra (brute force pw cracker)  
* samdump2 (dumps windows password hashes)  
* patator  

**Visual Reporting**  
* afterglow (graphs complex datasets)
* mantego
* Elastic Stack

**Memory Capture**  
* dumpit, PMem, fdpro, Mandiant Memoryze to dump on Windows
* pmemsave to dump qemu VM
* Snapshot to take dump of ESX VM
* LiME to extract on Linux
* Linux Memory Grabber - Hal Pomeranz
* PMDump - dump memory of a process

**Disk Capture**  
* dcfldd (enhanced dd)
* gddrescue/ddrescueview, ddrutility (complements ddrescue)
* rdd

**Timelining**  
* log2timeline w/ plaso
* Timesketch

**Registry Manipulation**  
* FRED
* regripper (wine friendly)
  
**Rootkit detection**  
* GMER (Windows)  
* Rootkit revealer (Windows)  
* Rootkit remover (mcafee win)  
* chkrootkit  
  
**Amcache parsing**  
* amcache.py
* AmcacheParser

**Prefetch analysis**  
* PECmd
  
**LNK parsing**  
* LECmd  
  
**Jumplist parsing**  
* JLECmd  
  
**TZWorks suite**  
* sbags (shell bags prser)  
* shims (shim cache parser)  
* usp (usb parser)  
* Yaru (undelete reg keys)  
* cafae (pull reg values uses VSC)  
* wisp (slack parser)  

**Scheduled Task (AT) job parser
* jobparser.py

** Windows Internals Suite**  

Tool | Image Name | Origin 
---- | ---------- | ------  
Startup Programs Viewer | AUTORUNS | Sysinternals
Access Check            | ACCESSCHK | Sysinternals
Dependency Walker       | DEPENDS | www.dependencywalker.com
Global Flags            | GFLAGS | Debugging tools
Handle Viewer           | HANDLE | Sysinternals
Object Viewer           | WINOBJ | Sysinternals
Performance Monitor     | PERFMON.MSC | Windows built-in tool
Pool Monitor            | POOLMON | Windows Driver Kit
Process Explorer        | PROCEXP | Sysinternals
Process Monitor         | PROCMON | Sysinternals
Task (Process) List     | TLIST | Debugging tools
Task Manager            | TASKMGR | Windows built-in tool
  
**Windows client evidence collection
  fastIR (collect artifacts)  
  usbdeview - see s/n of drives inserted  
  uvcview (pull sn off usb), usbdeviceforensics  
  dumpzilla
  DumpAutoComplete (firefox autocomplete dump)  
  Mandiant web historian  
  IEPassView on live system for protected to recover protected browser artifacts  
  Magnet's IEF $$$ (Scraping for chat/webmail logs)  
  
**Windows Miscellaneous  
  Forensic toolkit (view files without touching metadata, Mcafee)  
  shoWin (reveal passwords, Mcafee)  
  Vision (maps net ports to apps, Mcafee)  
  AccessData's registry viewer  
  MiTec Windows File Analyzer (view lnk metadata)  
  pstpassword  

**Sweet Python API Modules Found along the way  
requesocks (http calls for humans)  
fuzzywuzzy (fuzzy string comparison)  
pypdns (passive dns)  
pypssl (passive ssl)  

**Backend tools to use for string search**
* wce.exe (pw retrieval)
* mimikatz.exe (windows exploiter. pull hashes, forge kerberos tickets)
* depends.exe (walk DLL path)
* icacls.exe (check for perm to write to dir of system process)
