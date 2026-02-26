# 10. A little more effort

If we look closely at the method, it is possible to take advantage of certain particularities of the 4D language.
For example, in a`["case of](https://developer.4d.com/docs/Concepts/control-flow#case-ofelseend-case)`&#8221; conditional structure, conditions are evaluated one after the other, but the evaluation stops as soon as a condition is met. 
With this in mind, we can start by evaluating the fastest conditions.

In most cases, we increment `$i`, so we can globalize this line and avoid the &#8220;else&#8221; case in the structure. Just remember to decrement in a particular case. 

Here&#8217;s the improved code:

```
#DECLARE($source : Text)->$result : Text var $i; $c : Integer $result:=$source $i:=1 While ($i246) $c:=Character code($result[[$i]]) Case of : ($c=34) $result[[$i]]:="'" : ($c0) $result[[$i]]:="_" End case $i:=$i+1 End while
```

The call to the **Position** command is therefore rejected at the end of the condition, as it is probably slower than the simple comparison between two long integers.
Now that we&#8217;ve created the ***clean_folderName_position4*** method, all we need to do is test it:

![](http://local-learn.4d.com/wp-content/uploads/2025/11/image-19-779x1024.png)

We&#8217;ve seen an improvement in execution times. Even if these improvements are minimal at this stage, they should not be overlooked when this method is going to be used millions of times.