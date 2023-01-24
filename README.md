# Palindrom-Check-In-MIPS-Assembely-
MIPS Code to check whether Input string is palindrome or not 

.data 
  string : .asciiz "level"
  rev:     .space 20
  pal: .asciiz "Palindrom"
  not_pal: .asciiz "not"
  
.text
  la $s0, string
  la $s1, rev
  
 load:
 lb $t1, 0($s0)
 sb $t1, 0($s1)
 addi $s0, $s0,1
 addi $s1, $s1, 1
 bne $t1, $zero, load
 
 la $s0, string
 addi $s1, $s1, -2
 
 palindrom_check:
 
 lb $t0, 0($s0)
 lb $t1, 0($s1)
 bne $t0, $t1, notp
 add $s0, $s0,1
 add $s1,$s1, -1
 beq $t0, $zero, yes
 b palindrom_check
 
 
 notp:
 li $v0, 4
 la $a0, not_pal
 syscall
 
 b exit
 
 yes:
 li $v0, 4
 la $a0, pal
 syscall
 
 exit:
