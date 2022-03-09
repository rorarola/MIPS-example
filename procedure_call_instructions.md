### Caller 呼叫函式
```
/* code in C */
int ans = leaf_example(a, b, c, d)
```

step 1: 複製變數到arguments($a0, $a1...)</br>
step 2: 跳到procedure(function)</br>
step 3: 將結果($v0, $v1..))存到ans</br>

```
# step 1
add $a0, $s0, $0
add $a1, $s1, $0
add $a2, $s2, $0
add $a3, $s3, $0

# step 2
jal leaf_example

# step 3
add $s4, $v0, $0
```
### Callee 函式
```
/* code in C */
int leaf_example(int g, int h, int i, int j){ 
	int f;
	f = (g + h) - (i + j);
	return f;
}
```

$s0用來儲存區域變數，呼叫函式的地方(例如main)，還有function裡都會用到。
```
int add_five(int n) {		
	int b = n + 5;		<-- local variable
}
int main() {
	int a = 10;		<-- local variable
	a = add_five(a);
}
```
為了避免重複用同一個記憶體，有以下操作</br>
step 1: 將會用到的區域變數裡的值先丟到stack</br>
step 2: 安心使用區域變數</br>
step 3: function結束把stack裡的東西吐出來，還原到原先狀態
```
leaf_example:
	# step 1
	addi $sp, $sp, -12
	sw   $t1, 8($sp)
  	sw   $t0, 4($sp)
  	sw   $s0, 0($sp)

	# step 2
	add  $t0, $a0, $a1
	add  $t1, $a2, $a3
	sub  $s0, $t0, $t1
	add  $v0, $s0, $zero

	# step 3
	lw   $s0, 0($sp)
  	lw   $t0, 4($sp)
  	lw   $t1, 8($sp)
	addi $sp, $sp, 12

	# end of functoin, jump back to main
	jr   $ra			
```
> stack是往下長的
> $sp用來做stack


