## example 1: `g = h + A[8];`
in MIPS:
assume 	g in $s1
		h in $s2
		base address of A in $s3
```
lw $t0, 32($s3)		# load word, $t0 = A[8]
					# a word is 4 bytes, index 8 requires offest of 8*4=32
add $s1, $s2, $t0
```
> offset must be a constant

## example 2: `g = h + A[i];`
assume 	g in $s1
		h in $s2
		base address of A in $s3
		i in $s4
不能直接用變數當offset`$s4($s3)`，因此有以下方法：
```
add $t0, $s4, $zero	# $t0 = $s4  
sll $t0, $t0, 2		# $t0 = ($t0 << 2) = $t0 * 4	
add $t0, $t0, $s3	# $t0 = A+i
lw $t0, 0($t0)		# $t0 = *(A+i)
add $s1, $s2, $t0
```


