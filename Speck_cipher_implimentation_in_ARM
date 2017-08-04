@-------D.M.S.Chathuranga(E/13/043)------------
@----------CO224 PROJECT-----------------------

.text
.global main
main: 
	
	sub sp,sp,#4
	str lr,[sp,#0]

	@print enter the keys 
	ldr r0,=format1
	bl printf

	sub sp,sp,#8
	@scanf for key1
	ldr	r0, =formats
	mov	r1, sp	
	bl	scanf	@scanf("%X",sp)
	ldr r4,[sp,#4]
	ldr r5,[sp,#0]

	@scanf for key2
	ldr	r0, =formats
	mov	r1, sp	
	bl	scanf	@scanf("%X",sp)
	ldr r6,[sp,#4]
	ldr r7,[sp,#0]

	@print enter the texts 
	ldr r0,=format2
	bl printf

	@scanf for text1
	ldr	r0, =formats
	mov	r1, sp	
	bl	scanf	@scanf("%X",sp)
	ldr r8,[sp,#4]
	ldr r9,[sp,#0]

	@scanf for text2
	ldr	r0, =formats
	mov	r1, sp	
	bl	scanf	@scanf("%X",sp)
	ldr r10,[sp,#4]
	ldr r11,[sp,#0]
	add sp,sp,#8
	
	@store all data in stack
	sub sp,sp,#32
	str r4,[sp,#0]
	str r5,[sp,#4]
	str r6,[sp,#8]
	str r7,[sp,#12]
	str r8,[sp,#16]
	str r9,[sp,#20]
	str r10,[sp,#24]
	str r11,[sp,#28]

@--------first round--------
	ldr r0,[sp,#16]
	ldr r1,[sp,#20]
	bl ROR8
	
	ldr r2,[sp,#24]
	ldr r3,[sp,#28]
	bl ADD

	ldr r2,[sp,#8]
	ldr r3,[sp,#12]
	bl XOR
	str r0,[sp,#16]
	str r1,[sp,#20]

	ldr r0,[sp,#24]
	ldr r1,[sp,#28]
	bl ROL3

	ldr r2,[sp,#16]
	ldr r3,[sp,#20]
	bl XOR
	str r0,[sp,#24]
	str r1,[sp,#28]
	
@------after first round-----
	mov r4,#0
LOOP:	
	cmp r4,#31
	BGE EXIT

	ldr r0,[sp,#0]
	ldr r1,[sp,#4]
	bl ROR8

	ldr r2,[sp,#8]
	ldr r3,[sp,#12]
	bl ADD
	str r0,[sp,#0]	

	eor r2,r1,r4
	str r2,[sp,#4]

	ldr r0,[sp,#8]
	ldr r1,[sp,#12]
	bl ROL3

	ldr r2,[sp,#0]
	ldr r3,[sp,#4]
	bl XOR
	str r0,[sp,#8]
	str r1,[sp,#12]

	ldr r0,[sp,#16]
	ldr r1,[sp,#20]
	bl ROR8

	ldr r2,[sp,#24]
	ldr r3,[sp,#28]
	bl ADD

	ldr r2,[sp,#8]
	ldr r3,[sp,#12]
	bl XOR
	str r0,[sp,#16]
	str r1,[sp,#20]

	ldr r0,[sp,#24]
	ldr r1,[sp,#28]
	bl ROL3

	ldr r2,[sp,#16]
	ldr r3,[sp,#20]
	bl XOR
	str r0,[sp,#24]
	str r1,[sp,#28]
	
	add r4,r4,#1
	b LOOP 

EXIT:	@Printing the ciper texts
	ldr r0,=format3
	bl printf

	ldr r0,=formato1
	ldr r1,[sp,#16]
	ldr r2,[sp,#20]
	bl printf

	ldr r0,=formato2
	ldr r1,[sp,#24]
	ldr r2,[sp,#28]
	bl printf
	add sp,sp,#32
	ldr lr,[sp,#0]
	add sp,sp,#4
	mov pc,lr

@-----Addtion function--------
@Inputs- r0,r2-first8bits
ADD: 	sub sp,sp,#4
	str lr,[sp,#0]

	adds r1,r1,r3
	adc r0,r0,r2

	ldr lr,[sp,#0]
	add sp,sp,#4
	mov pc,lr

@---------function for XOR-----------------
@Inputs- r0,r2-first8bits
XOR:	sub sp,sp,#4
	str lr,[sp,#0]
	
	eor r0,r0,r2
	eor r1,r1,r3

	ldr lr,[sp,#0]
	add sp,sp,#4
	mov pc,lr

@---------function for ROR8--------------
@ror8 R0-first8bit R1-second8bit
ROR8:	sub sp,sp,#4
	str lr,[sp,#0]

	lsr r2,r0,#8
	add r3,r2,r1,lsl #24  	
	lsr r2,r1,#8
	add r1,r2,r0,lsl #24
	mov r0,r3

	ldr lr,[sp,#0]
	add sp,sp,#4
	mov pc,lr

@---------function for ROL3---------------
@rol3 R0-first8bit R1-second8bit
ROL3:	sub sp,sp,#4
	str lr,[sp,#0]

	lsl r2,r0,#3
	add r3,r2,r1,lsr #29  	
	lsl r2,r1,#3
	add r1,r2,r0,lsr #29
	mov r0,r3

	ldr lr,[sp,#0]
	add sp,sp,#4
	mov pc,lr
@-----------------------------------------
.data
format1:.asciz "Enter the key:\n"
format2:.asciz "Enter the plain text:\n"
format3:.asciz "Cipher text is:\n"
formato1:.asciz "%x%08x "
formato2:.asciz "%x%08x\n"
formats:.asciz "%llx"
