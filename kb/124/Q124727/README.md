---
layout: page
title: "Q124727: How to Program DMA for Linear Addresses under Windows"
permalink: /kb/124/Q124727/
---

## Q124727: How to Program DMA for Linear Addresses under Windows

{% raw %}

	Article: Q124727
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The process for programming DMA for linear addresses under Windows is similar to
	the process for programming physical addresses under MS-DOS. On byte (8-bit)
	channels (0-3), program the page register with bits A23-A16 and the base
	register with bits A15-A0 of the 24-bit address. On word (16-bit) channels
	(5-7), program the page register with bits A23-A16 and the base register with
	bits A16-A1, shifted right 1 bit (>> 1 in C, or SHR <reg>,1 in ASM).
	
	MORE INFORMATION
	================
	
	It looks like bit A16 is used twice on word channels. Typically, bits A23-A16
	would be compared with the value 0FEh (0xFE) using an OR operator; then the page
	register would be programmed with the result. It is not necessary to strip off
	bit A16 in the page register because as the least significant bit in the page
	register, it is ignored by the hardware.
	
	As noted above, the base register on word channel transfer is programmed with
	bits (A16-A1) >> 1. The hardware generates the address by concatenating
	the 7 most significant bits from the page register with the 16 bits from the
	base register. Because the base is shifted left by one, incrementing the
	programmed address actually increments the physical address by 2. Because the
	LSB is always zero, the transfers are always word aligned.
	
	Word channels are actually somewhat of a hardware hack for a DMA controller that
	really only supports byte transfers.
	
	Given a 24-bit physical address, the controller would be programmed as described
	above. If you have a 24-bit linear address, program it the same way. The virtual
	DMA device (VDMAD) will reconstitue the linear address from the page/base
	registers the same way the hardware would.
	
	There is one caveat to keep in mind when using linear addresses. If the linear
	address is not below one megabyte, it will probably be above two gigabytes (>
	24-bits). If it is, it cannot be virtually programmed into the base register. If
	the DMA buffer comes from GlobalAlloc() instead of GlobalDosAlloc(), you need to
	disable address translation using the Virtual DMA Specification (VDS) API
	through INT 4Bh. Then use VDS again to get the physical address and program the
	page/base with the physical address.
	
	Additional query words: 3.10 3.11 VDMAD no32bit
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310 kbWinSDK311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
