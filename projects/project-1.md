---
layout: project
type: project
image: images/Dig_Dug.png
title: Dig Dug in ARM Assembly
permalink: projects/dig-dug
# All dates must be YYYY-MM-DD format!
date: 2017-05-05
labels:
  - Assembly
  - game design
  - ARM
summary: For the final project in CSE 379 at the State University of New York at Buffalo, I recreated the classic arcade game Dig Dug using ARM assembly language and the LPC2138 Board.
---


One of the first Computer Science and Engineering classes I took was CSE379 - Introduction to Microprocessors at SUNY at Buffalo. The course was designed to allow us to recreate a classic arcade game from the ground up in assembly language, as many games were originally written at the time. Labs began with the basic building blocks of a program such as loading, storing and utilizing the available registers. Using these building blocks we would be able to build our game over time during the semester, with the final weeks of the class spent entirely on this endeavor. 

The project was meant to be done in a group of 2-3, however my partner resigned the class a month in, well before development on the game itself had even begun. This being my first real foray into any sort of programming, I was pushed to my limits just to finish. I logged as much extra lab time as physically possible. The resulting program was roughly 3,000 lines of original code, but it successfully recreated a rudimentary version of Dig Dug, visualized for the user through a string displayed in the console that was continually rewritten to track player and enemy movement. Various I/O devices on the board were used to display additional information to the user, such as their number of lives. 

To give an example, here is one subroutine:

```s
;+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
;This section is Direction_select:
;This subroutine uses the timer count value 
;to select a random direction (u, d, l, r) and associated symbol (<,>,^,V)
;and stores back the direction value in designated memory (passed in r4)
;

Direction_select
	STMFD SP!,{r0-r3, r5-r12,lr}

	LDR r5, =0xE0004008
	LDR r0, [r5]
	LDR r1, =0xFFFFFFF0
	BIC r0, r0, r1
	CMP r0, #12
	BGE up2
	CMP r0, #8
	BGE down2
	CMP r0, #4
	BGE left2
	B right2

up2
	MOV r9, #1
	MOV r10, #0x5E
	B enddirection1
down2
	MOV r9, #2
	MOV r10, #0x56
	B enddirection1
left2
	MOV r9, #4
	MOV r10, #0x3C
	B enddirection1
right2
	MOV r9, #8
	MOV r10, #0x3E
	B enddirection1
enddirection1

	STRB r9, [r4]
	STRB r10, [r4, #1]
	
	LDMFD sp!, {r0-r3, r5-r12,lr}
	BX LR
```


The full code is available in my github repo, along with the final Lab report that accompanied the project.

[DigDug Project Repo](https://github.com/willkoch/DigDug)



