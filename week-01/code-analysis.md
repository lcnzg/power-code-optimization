# Hello, World! assembly analysis

## Compilation

```
sudo apt update
sudo apt install build-essential
```

```
gcc -O3 -S hello-world.c
```

## Analysis

```
$ cat hello-world.s
	.file	"hello-world.c"
	.abiversion 2
	.section	".text"
	.section	.text.startup,"ax",@progbits
	.align 2
	.p2align 4,,15
	.globl main
	.type	main, @function
main:
.LCF0:
0:	addis 2,12,.TOC.-.LCF0@ha	# Add Immediate Shifted RT,RA,SI
	addi 2,2,.TOC.-.LCF0@l		# Add Immediate RT,RA,SI
	.localentry	main,.-main
	mflr 0				# Copy the contents of the LR to register Rx
	addis 4,2,.LC0@toc@ha		# Add Immediate Shifted RT,RA,SI
	addi 4,4,.LC0@toc@l		# Add Immediate RT,RA,SI
	li 3,1				# Load Immediate Rx,value
	std 0,16(1)			# Store Doubleword RS,DS(RA)
	stdu 1,-96(1)			# Store Doubleword with Update RS,DS(RA)
	bl __printf_chk			# Call printf
	nop
	addi 1,1,96			# Add Immediate RT,RA,SI
	li 3,0				# Load Immediate Rx,value
	ld 0,16(1)			# Load Doubleword RT,DS(RA)
	mtlr 0				# Move to LR register Rx
	blr				# Branch to link register
	.long 0
	.byte 0,0,0,1,128,0,0,0
	.size	main,.-main
	.section	.rodata.str1.8,"aMS",@progbits,1
	.align 3
.LC0:
	.string	"Hello, World!"
	.ident	"GCC: (Ubuntu 7.4.0-1ubuntu1~18.04.1) 7.4.0"
	.section	.note.GNU-stack,"",@progbits
```
