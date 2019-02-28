``` TCL
# for loop execution
for { set i 1}  {$i < 200} {incr i} {
    Switch to 100G
    Switch to 50G
    for { set j 1}  {$j < 20} {incr j} {
        Run 50G Cases
    }
    Switch to 25G
    for { set j 1}  {$j < 20} {incr j} {
        Run 25G Cases
    }
}
```
