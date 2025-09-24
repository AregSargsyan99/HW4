Areg Sargsyan
The author of the codes is me and only me.

I made these files as required and and then linked them into square_prog:

gcc -c main.c
gcc -c math_utils.c
gcc main.o math_utils.o -o square_prog

These are all my commands I used as mentioned in the assignment:

gcc -c main.c
gcc -c math_utils.c
gcc main.o math_utils.o -o square_prog
nm main.o
nm math_utils.o
nm square_prog
objdump -d main.o
objdump -d math_utils.o
objdump -d square_prog
readelf -h main.o
readelf -h math_utils.o
readelf -h square_prog
readelf -S main.o
readelf -S math_utils.o
readelf -S square_prog

Here are the outputs copied right from the terminal:


aregs@ubuntu-aua-os:~/HW4$ nm main.o
0000000000000000 T main
                 U printf
                 U square
aregs@ubuntu-aua-os:~/HW4$ nm math_utils.o
0000000000000000 T square
aregs@ubuntu-aua-os:~/HW4$ nm square_prog
0000000000003dc8 d _DYNAMIC
0000000000003fb8 d _GLOBAL_OFFSET_TABLE_
0000000000002000 R _IO_stdin_used
                 w _ITM_deregisterTMCloneTable
                 w _ITM_registerTMCloneTable
0000000000002110 r __FRAME_END__
0000000000002008 r __GNU_EH_FRAME_HDR
0000000000004010 D __TMC_END__
000000000000038c r __abi_tag
0000000000004010 B __bss_start
                 w __cxa_finalize@GLIBC_2.2.5
0000000000004000 D __data_start
0000000000001100 t __do_global_dtors_aux
0000000000003dc0 d __do_global_dtors_aux_fini_array_entry
0000000000004008 D __dso_handle
0000000000003db8 d __frame_dummy_init_array_entry
                 w __gmon_start__
                 U __libc_start_main@GLIBC_2.34
0000000000004010 D _edata
0000000000004018 B _end
0000000000001198 T _fini
0000000000001000 T _init
0000000000001060 T _start
0000000000004010 b completed.0
0000000000004000 W data_start
0000000000001090 t deregister_tm_clones
0000000000001140 t frame_dummy
0000000000001149 T main
                 U printf@GLIBC_2.2.5
00000000000010c0 t register_tm_clones
0000000000001183 T square
aregs@ubuntu-aua-os:~/HW4$ objdump -d main.o

main.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <main>:
   0:	f3 0f 1e fa          	endbr64
   4:	55                   	push   %rbp
   5:	48 89 e5             	mov    %rsp,%rbp
   8:	48 83 ec 10          	sub    $0x10,%rsp
   c:	c7 45 fc 63 00 00 00 	movl   $0x63,-0x4(%rbp)
  13:	8b 45 fc             	mov    -0x4(%rbp),%eax
  16:	89 c7                	mov    %eax,%edi
  18:	e8 00 00 00 00       	call   1d <main+0x1d>
  1d:	89 c6                	mov    %eax,%esi
  1f:	48 8d 05 00 00 00 00 	lea    0x0(%rip),%rax        # 26 <main+0x26>
  26:	48 89 c7             	mov    %rax,%rdi
  29:	b8 00 00 00 00       	mov    $0x0,%eax
  2e:	e8 00 00 00 00       	call   33 <main+0x33>
  33:	b8 00 00 00 00       	mov    $0x0,%eax
  38:	c9                   	leave
  39:	c3                   	ret
aregs@ubuntu-aua-os:~/HW4$ objdump -d math_utils.o

math_utils.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <square>:
   0:	f3 0f 1e fa          	endbr64
   4:	55                   	push   %rbp
   5:	48 89 e5             	mov    %rsp,%rbp
   8:	89 7d fc             	mov    %edi,-0x4(%rbp)
   b:	8b 45 fc             	mov    -0x4(%rbp),%eax
   e:	0f af c0             	imul   %eax,%eax
  11:	5d                   	pop    %rbp
  12:	c3                   	ret
aregs@ubuntu-aua-os:~/HW4$ objdump -d square_prog

square_prog:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 <_init>:
    1000:	f3 0f 1e fa          	endbr64
    1004:	48 83 ec 08          	sub    $0x8,%rsp
    1008:	48 8b 05 d9 2f 00 00 	mov    0x2fd9(%rip),%rax        # 3fe8 <__gmon_start__@Base>
    100f:	48 85 c0             	test   %rax,%rax
    1012:	74 02                	je     1016 <_init+0x16>
    1014:	ff d0                	call   *%rax
    1016:	48 83 c4 08          	add    $0x8,%rsp
    101a:	c3                   	ret

Disassembly of section .plt:

0000000000001020 <.plt>:
    1020:	ff 35 9a 2f 00 00    	push   0x2f9a(%rip)        # 3fc0 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026:	ff 25 9c 2f 00 00    	jmp    *0x2f9c(%rip)        # 3fc8 <_GLOBAL_OFFSET_TABLE_+0x10>
    102c:	0f 1f 40 00          	nopl   0x0(%rax)
    1030:	f3 0f 1e fa          	endbr64
    1034:	68 00 00 00 00       	push   $0x0
    1039:	e9 e2 ff ff ff       	jmp    1020 <_init+0x20>
    103e:	66 90                	xchg   %ax,%ax

Disassembly of section .plt.got:

0000000000001040 <__cxa_finalize@plt>:
    1040:	f3 0f 1e fa          	endbr64
    1044:	ff 25 ae 2f 00 00    	jmp    *0x2fae(%rip)        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    104a:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)

Disassembly of section .plt.sec:

0000000000001050 <printf@plt>:
    1050:	f3 0f 1e fa          	endbr64
    1054:	ff 25 76 2f 00 00    	jmp    *0x2f76(%rip)        # 3fd0 <printf@GLIBC_2.2.5>
    105a:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)

Disassembly of section .text:

0000000000001060 <_start>:
    1060:	f3 0f 1e fa          	endbr64
    1064:	31 ed                	xor    %ebp,%ebp
    1066:	49 89 d1             	mov    %rdx,%r9
    1069:	5e                   	pop    %rsi
    106a:	48 89 e2             	mov    %rsp,%rdx
    106d:	48 83 e4 f0          	and    $0xfffffffffffffff0,%rsp
    1071:	50                   	push   %rax
    1072:	54                   	push   %rsp
    1073:	45 31 c0             	xor    %r8d,%r8d
    1076:	31 c9                	xor    %ecx,%ecx
    1078:	48 8d 3d ca 00 00 00 	lea    0xca(%rip),%rdi        # 1149 <main>
    107f:	ff 15 53 2f 00 00    	call   *0x2f53(%rip)        # 3fd8 <__libc_start_main@GLIBC_2.34>
    1085:	f4                   	hlt
    1086:	66 2e 0f 1f 84 00 00 	cs nopw 0x0(%rax,%rax,1)
    108d:	00 00 00 

0000000000001090 <deregister_tm_clones>:
    1090:	48 8d 3d 79 2f 00 00 	lea    0x2f79(%rip),%rdi        # 4010 <__TMC_END__>
    1097:	48 8d 05 72 2f 00 00 	lea    0x2f72(%rip),%rax        # 4010 <__TMC_END__>
    109e:	48 39 f8             	cmp    %rdi,%rax
    10a1:	74 15                	je     10b8 <deregister_tm_clones+0x28>
    10a3:	48 8b 05 36 2f 00 00 	mov    0x2f36(%rip),%rax        # 3fe0 <_ITM_deregisterTMCloneTable@Base>
    10aa:	48 85 c0             	test   %rax,%rax
    10ad:	74 09                	je     10b8 <deregister_tm_clones+0x28>
    10af:	ff e0                	jmp    *%rax
    10b1:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)
    10b8:	c3                   	ret
    10b9:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

00000000000010c0 <register_tm_clones>:
    10c0:	48 8d 3d 49 2f 00 00 	lea    0x2f49(%rip),%rdi        # 4010 <__TMC_END__>
    10c7:	48 8d 35 42 2f 00 00 	lea    0x2f42(%rip),%rsi        # 4010 <__TMC_END__>
    10ce:	48 29 fe             	sub    %rdi,%rsi
    10d1:	48 89 f0             	mov    %rsi,%rax
    10d4:	48 c1 ee 3f          	shr    $0x3f,%rsi
    10d8:	48 c1 f8 03          	sar    $0x3,%rax
    10dc:	48 01 c6             	add    %rax,%rsi
    10df:	48 d1 fe             	sar    $1,%rsi
    10e2:	74 14                	je     10f8 <register_tm_clones+0x38>
    10e4:	48 8b 05 05 2f 00 00 	mov    0x2f05(%rip),%rax        # 3ff0 <_ITM_registerTMCloneTable@Base>
    10eb:	48 85 c0             	test   %rax,%rax
    10ee:	74 08                	je     10f8 <register_tm_clones+0x38>
    10f0:	ff e0                	jmp    *%rax
    10f2:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)
    10f8:	c3                   	ret
    10f9:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

0000000000001100 <__do_global_dtors_aux>:
    1100:	f3 0f 1e fa          	endbr64
    1104:	80 3d 05 2f 00 00 00 	cmpb   $0x0,0x2f05(%rip)        # 4010 <__TMC_END__>
    110b:	75 2b                	jne    1138 <__do_global_dtors_aux+0x38>
    110d:	55                   	push   %rbp
    110e:	48 83 3d e2 2e 00 00 	cmpq   $0x0,0x2ee2(%rip)        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1115:	00 
    1116:	48 89 e5             	mov    %rsp,%rbp
    1119:	74 0c                	je     1127 <__do_global_dtors_aux+0x27>
    111b:	48 8b 3d e6 2e 00 00 	mov    0x2ee6(%rip),%rdi        # 4008 <__dso_handle>
    1122:	e8 19 ff ff ff       	call   1040 <__cxa_finalize@plt>
    1127:	e8 64 ff ff ff       	call   1090 <deregister_tm_clones>
    112c:	c6 05 dd 2e 00 00 01 	movb   $0x1,0x2edd(%rip)        # 4010 <__TMC_END__>
    1133:	5d                   	pop    %rbp
    1134:	c3                   	ret
    1135:	0f 1f 00             	nopl   (%rax)
    1138:	c3                   	ret
    1139:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

0000000000001140 <frame_dummy>:
    1140:	f3 0f 1e fa          	endbr64
    1144:	e9 77 ff ff ff       	jmp    10c0 <register_tm_clones>

0000000000001149 <main>:
    1149:	f3 0f 1e fa          	endbr64
    114d:	55                   	push   %rbp
    114e:	48 89 e5             	mov    %rsp,%rbp
    1151:	48 83 ec 10          	sub    $0x10,%rsp
    1155:	c7 45 fc 63 00 00 00 	movl   $0x63,-0x4(%rbp)
    115c:	8b 45 fc             	mov    -0x4(%rbp),%eax
    115f:	89 c7                	mov    %eax,%edi
    1161:	e8 1d 00 00 00       	call   1183 <square>
    1166:	89 c6                	mov    %eax,%esi
    1168:	48 8d 05 95 0e 00 00 	lea    0xe95(%rip),%rax        # 2004 <_IO_stdin_used+0x4>
    116f:	48 89 c7             	mov    %rax,%rdi
    1172:	b8 00 00 00 00       	mov    $0x0,%eax
    1177:	e8 d4 fe ff ff       	call   1050 <printf@plt>
    117c:	b8 00 00 00 00       	mov    $0x0,%eax
    1181:	c9                   	leave
    1182:	c3                   	ret

0000000000001183 <square>:
    1183:	f3 0f 1e fa          	endbr64
    1187:	55                   	push   %rbp
    1188:	48 89 e5             	mov    %rsp,%rbp
    118b:	89 7d fc             	mov    %edi,-0x4(%rbp)
    118e:	8b 45 fc             	mov    -0x4(%rbp),%eax
    1191:	0f af c0             	imul   %eax,%eax
    1194:	5d                   	pop    %rbp
    1195:	c3                   	ret

Disassembly of section .fini:

0000000000001198 <_fini>:
    1198:	f3 0f 1e fa          	endbr64
    119c:	48 83 ec 08          	sub    $0x8,%rsp
    11a0:	48 83 c4 08          	add    $0x8,%rsp
    11a4:	c3                   	ret
aregs@ubuntu-aua-os:~/HW4$ readelf -h main.o
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              REL (Relocatable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x0
  Start of program headers:          0 (bytes into file)
  Start of section headers:          680 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           0 (bytes)
  Number of program headers:         0
  Size of section headers:           64 (bytes)
  Number of section headers:         14
  Section header string table index: 13
aregs@ubuntu-aua-os:~/HW4$ readelf -h math_utils.o
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              REL (Relocatable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x0
  Start of program headers:          0 (bytes into file)
  Start of section headers:          464 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           0 (bytes)
  Number of program headers:         0
  Size of section headers:           64 (bytes)
  Number of section headers:         12
  Section header string table index: 11
aregs@ubuntu-aua-os:~/HW4$ readelf -h square_prog
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Position-Independent Executable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x1060
  Start of program headers:          64 (bytes into file)
  Start of section headers:          14048 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         13
  Size of section headers:           64 (bytes)
  Number of section headers:         31
  Section header string table index: 30
aregs@ubuntu-aua-os:~/HW4$ readelf -S main.o
There are 14 section headers, starting at offset 0x2a8:

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .text             PROGBITS         0000000000000000  00000040
       000000000000003a  0000000000000000  AX       0     0     1
  [ 2] .rela.text        RELA             0000000000000000  000001d0
       0000000000000048  0000000000000018   I      11     1     8
  [ 3] .data             PROGBITS         0000000000000000  0000007a
       0000000000000000  0000000000000000  WA       0     0     1
  [ 4] .bss              NOBITS           0000000000000000  0000007a
       0000000000000000  0000000000000000  WA       0     0     1
  [ 5] .rodata           PROGBITS         0000000000000000  0000007a
       0000000000000004  0000000000000000   A       0     0     1
  [ 6] .comment          PROGBITS         0000000000000000  0000007e
       000000000000002c  0000000000000001  MS       0     0     1
  [ 7] .note.GNU-stack   PROGBITS         0000000000000000  000000aa
       0000000000000000  0000000000000000           0     0     1
  [ 8] .note.gnu.pr[...] NOTE             0000000000000000  000000b0
       0000000000000020  0000000000000000   A       0     0     8
  [ 9] .eh_frame         PROGBITS         0000000000000000  000000d0
       0000000000000038  0000000000000000   A       0     0     8
  [10] .rela.eh_frame    RELA             0000000000000000  00000218
       0000000000000018  0000000000000018   I      11     9     8
  [11] .symtab           SYMTAB           0000000000000000  00000108
       00000000000000a8  0000000000000018          12     4     8
  [12] .strtab           STRTAB           0000000000000000  000001b0
       000000000000001b  0000000000000000           0     0     1
  [13] .shstrtab         STRTAB           0000000000000000  00000230
       0000000000000074  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), l (large), p (processor specific)
aregs@ubuntu-aua-os:~/HW4$ readelf -S math_utils.o
There are 12 section headers, starting at offset 0x1d0:

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .text             PROGBITS         0000000000000000  00000040
       0000000000000013  0000000000000000  AX       0     0     1
  [ 2] .data             PROGBITS         0000000000000000  00000053
       0000000000000000  0000000000000000  WA       0     0     1
  [ 3] .bss              NOBITS           0000000000000000  00000053
       0000000000000000  0000000000000000  WA       0     0     1
  [ 4] .comment          PROGBITS         0000000000000000  00000053
       000000000000002c  0000000000000001  MS       0     0     1
  [ 5] .note.GNU-stack   PROGBITS         0000000000000000  0000007f
       0000000000000000  0000000000000000           0     0     1
  [ 6] .note.gnu.pr[...] NOTE             0000000000000000  00000080
       0000000000000020  0000000000000000   A       0     0     8
  [ 7] .eh_frame         PROGBITS         0000000000000000  000000a0
       0000000000000038  0000000000000000   A       0     0     8
  [ 8] .rela.eh_frame    RELA             0000000000000000  00000150
       0000000000000018  0000000000000018   I       9     7     8
  [ 9] .symtab           SYMTAB           0000000000000000  000000d8
       0000000000000060  0000000000000018          10     3     8
  [10] .strtab           STRTAB           0000000000000000  00000138
       0000000000000015  0000000000000000           0     0     1
  [11] .shstrtab         STRTAB           0000000000000000  00000168
       0000000000000067  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), l (large), p (processor specific)
aregs@ubuntu-aua-os:~/HW4$ readelf -S square_prog
There are 31 section headers, starting at offset 0x36e0:

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .interp           PROGBITS         0000000000000318  00000318
       000000000000001c  0000000000000000   A       0     0     1
  [ 2] .note.gnu.pr[...] NOTE             0000000000000338  00000338
       0000000000000030  0000000000000000   A       0     0     8
  [ 3] .note.gnu.bu[...] NOTE             0000000000000368  00000368
       0000000000000024  0000000000000000   A       0     0     4
  [ 4] .note.ABI-tag     NOTE             000000000000038c  0000038c
       0000000000000020  0000000000000000   A       0     0     4
  [ 5] .gnu.hash         GNU_HASH         00000000000003b0  000003b0
       0000000000000024  0000000000000000   A       6     0     8
  [ 6] .dynsym           DYNSYM           00000000000003d8  000003d8
       00000000000000a8  0000000000000018   A       7     1     8
  [ 7] .dynstr           STRTAB           0000000000000480  00000480
       000000000000008f  0000000000000000   A       0     0     1
  [ 8] .gnu.version      VERSYM           0000000000000510  00000510
       000000000000000e  0000000000000002   A       6     0     2
  [ 9] .gnu.version_r    VERNEED          0000000000000520  00000520
       0000000000000030  0000000000000000   A       7     1     8
  [10] .rela.dyn         RELA             0000000000000550  00000550
       00000000000000c0  0000000000000018   A       6     0     8
  [11] .rela.plt         RELA             0000000000000610  00000610
       0000000000000018  0000000000000018  AI       6    24     8
  [12] .init             PROGBITS         0000000000001000  00001000
       000000000000001b  0000000000000000  AX       0     0     4
  [13] .plt              PROGBITS         0000000000001020  00001020
       0000000000000020  0000000000000010  AX       0     0     16
  [14] .plt.got          PROGBITS         0000000000001040  00001040
       0000000000000010  0000000000000010  AX       0     0     16
  [15] .plt.sec          PROGBITS         0000000000001050  00001050
       0000000000000010  0000000000000010  AX       0     0     16
  [16] .text             PROGBITS         0000000000001060  00001060
       0000000000000136  0000000000000000  AX       0     0     16
  [17] .fini             PROGBITS         0000000000001198  00001198
       000000000000000d  0000000000000000  AX       0     0     4
  [18] .rodata           PROGBITS         0000000000002000  00002000
       0000000000000008  0000000000000000   A       0     0     4
  [19] .eh_frame_hdr     PROGBITS         0000000000002008  00002008
       000000000000003c  0000000000000000   A       0     0     4
  [20] .eh_frame         PROGBITS         0000000000002048  00002048
       00000000000000cc  0000000000000000   A       0     0     8
  [21] .init_array       INIT_ARRAY       0000000000003db8  00002db8
       0000000000000008  0000000000000008  WA       0     0     8
  [22] .fini_array       FINI_ARRAY       0000000000003dc0  00002dc0
       0000000000000008  0000000000000008  WA       0     0     8
  [23] .dynamic          DYNAMIC          0000000000003dc8  00002dc8
       00000000000001f0  0000000000000010  WA       7     0     8
  [24] .got              PROGBITS         0000000000003fb8  00002fb8
       0000000000000048  0000000000000008  WA       0     0     8
  [25] .data             PROGBITS         0000000000004000  00003000
       0000000000000010  0000000000000000  WA       0     0     8
  [26] .bss              NOBITS           0000000000004010  00003010
       0000000000000008  0000000000000000  WA       0     0     1
  [27] .comment          PROGBITS         0000000000000000  00003010
       000000000000002b  0000000000000001  MS       0     0     1
  [28] .symtab           SYMTAB           0000000000000000  00003040
       0000000000000390  0000000000000018          29    19     8
  [29] .strtab           STRTAB           0000000000000000  000033d0
       00000000000001f0  0000000000000000           0     0     1
  [30] .shstrtab         STRTAB           0000000000000000  000035c0
       000000000000011a  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), l (large), p (processor specific)


Analyze:

From nm: in main.o I see T main and U square, plus U printf. That means main is defined in this object, while square and printf are unresolved here and must be found later. In math_utils.o I see T square, so square is defined there. In the final binary square_prog both main and square show up as defined (T), while libc things are still dynamic (e.g., U printf@GLIBC_2.2.5, U __libc_start_main@GLIBC_2.34). This shows the linker matched the undefined square in main.o to the definition in math_utils.o, and left libc calls to be resolved at runtime.
From objdump -d: in main.o the call to square is not resolved yet and shows as a placeholder (e8 00 00 00 00 followed by a local target), which is normal for relocatable code. In math_utils.o the square function is just a few instructions (load the argument, imul, return). In the final executable square_prog the call is resolved to a real target (call 1183 <square>), and the printf call goes through the PLT (call 1050 <printf@plt>). The executable also contains code you never see in the objects, like _start, and sections for initialization and finalization; that’s part of the normal C runtime startup/teardown.
From readelf: both object files are Type: REL (Relocatable file) with no program headers. They have sections like .text, .data, .bss, .rodata, .symtab, .strtab, and, importantly, relocation sections such as .rela.text (main.o also shows .rela.eh_frame). These relocation sections are the “to-be-fixed” places the linker must patch. The final program square_prog is Type: DYN (Position-Independent Executable), with an entry point (0x1060 on my system) and multiple program headers. It also includes dynamic/loader sections that don’t exist in the objects, such as .interp, .gnu.hash, .dynsym, .dynstr, .gnu.version*, .rela.dyn, .rela.plt, .plt, .plt.got, .plt.sec, .got, .dynamic, plus .init, .fini, and the init/fini arrays. Its .text, .rodata, .data, and .bss are the merged, laid-out results of linking. My build also still has a .symtab/.strtab because the executable isn’t stripped, which is fine.

