# 4. Compiled code

When it comes to optimization, the first thing to think about is [compilation](https://developer.4d.com/docs/Project/compiler). Indeed, why try to go fast while remaining in interpreted mode, where each line is analyzed before being executed?
As the code is faster in compiled mode, we&#8217;re going to increase the number of test loops from 4 to 20.
Here&#8217;s the improved test code:

```
$times:=New collection() $desktop:=Folder(fk applications folder) $folders:=$desktop.folders().extract("name") If (Is compiled mode) $nbLoops:=20 Else $nbLoops:=4 End if CONFIRM("add gremlins ?") If (ok=1) $chars:=":;?/*>