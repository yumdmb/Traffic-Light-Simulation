ORG   00H
  AJMP   MAIN
  
MAIN:   MOV   A,#00H
  MOV   P0,A ;Set Port 0 as output
  MOV   P1,A ;Set Port 1 as output
  MOV   P2,A ;Set Port 2 as output
  MOV   P3,A ;Set Port 3 as output
  MOV   DPTR,#SEG ;MOVE TABLE ADRESS TO DATA POINTER
  
START:   MOV   R7,#01BH ;Set Lane 1 as green and others red
  MOV   R6,#1EH
  MOV   A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   GREENCOUNT ;Call Counter subroutine 
  MOV   R7,#01BH ;Set Lane 1 as yellow and others red
  MOV   R6,#01DH
  MOV   A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   YELLOWCOUNT ;Call Yellow Counter subroutine
  MOV   R7,#01BH ;Set Lane 2 as green and others red
  MOV   R6,#0F3H
  MOV   A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   GREENCOUNT ;Call Counter subroutine
  
  MOV   R7,#01BH ;Set Lane 2 as yellow and others red
  MOV   R6,#2BH
  MOV   A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   YELLOWCOUNT ;Call Yellow Counter subroutine
  
  MOV   R7,#01EH ;Set Lane 3 as green and others red
  MOV   R6,#01BH
  MOV     A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   GREENCOUNT ;Call Counter subroutine
  
  MOV   R7,#01DH ;Set Lane 3 as yellow and others red
  MOV   R6,#01BH
  MOV   A,R7
  MOV   P0,A
  MOV   A,R6
  MOV   P2,A 
  ACALL   YELLOWCOUNT ;Call Yellow Counter subroutine
  MOV   R7,#0F3H ;Set Lane 4 as yellow and others red
  MOV   R6,#0DBH
  MOV A,R7
  MOV P0,A
  MOV A,R6
  MOV P2,A 
  ACALL GREENCOUNT ;Call Counter subroutine
  MOV R7,#0EBH ;Set Lane 4 as yellow and others red
  MOV R6,#0DBH
  MOV A,R7
  MOV P0,A
  MOV A,R6
  MOV P2,A 
  ACALL YELLOWCOUNT ;Call Yellow Counter subroutine
  AJMP START
  
GREENCOUNT:   MOV   B,#09H
    MOV  A,B
    MOVC   A,@A+DPTR
    MOV   P1,A
    ACALL   DELAY
  
DECREMENTGREEN:DEC   B
    MOV  A,B
    MOVC   A,@A+DPTR
    MOV   P1,A
    ACALL   DELAY
    CJNE   A,#3FH,DECREMENTGREEN
    MOV   P1,#00H
    RET 

YELLOWCOUNT:  MOV   B,#09H
      MOV   A,B
     MOVC   A,@A+DPTR 
     MOV   P3,A
     ACALL  DELAY
      AJMP   DECREMENTYELLOW

DECREMENTYELLOW:DEC   B
    MOV  A,B
    MOVC   A,@A+DPTR
    MOV   P3,A
    ACALL   DELAY
    CJNE   A,#3FH,DECREMENTYELLOW
    MOV	   P3,#00H	
    RET 
    
DELAY:  MOV   R1,#09H ; Delay-for counter
DELAY1:   DJNZ   R1,DELAY1
  RET
  
  ;LOOK IP TABLE FOR 7SEGMENT DISPLAY
  SEG: DB 3Fh,06h,5Bh,4Fh,66h,6Dh,7Dh,07h,7Fh,6Fh,77h,7Ch,39h,5Eh,79h,71h
  END
