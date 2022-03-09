| Instruction  | Example               | Meaning   | Comments                                                                  |
|--------------|-----------------------|-----------|---------------------------------------------------------------------------|
| + (variable) | add $1, $2, $3        | $1=$2+$3  |                                                                           |
| - (variable) | sub $1, $2, $3        | $1=$2-$3  |                                                                           |
| + (constant) | addi $1, $2, 100      | $1=$2+100 | add a constant                                                            |
| + (unsigned) | addu $1, $2, 100      | $1=$2+100 | Values are treated as unsigned integers,<br>not two's complement integers |
| * (variable) | mul $1,$2,$3          | $1=$2*$3  |                                                                           |
| / (variable) | div $2, $3<br>mflo $1 | $1=$2/$3  |                                                                           |
| % (variable) | div $2, $3<br>mflo $1 | $1=$2%$3  |                                                                           |

[source](https://www.dsi.unive.it/~gasparetto/materials/MIPS_Instruction_Set.pdf)
