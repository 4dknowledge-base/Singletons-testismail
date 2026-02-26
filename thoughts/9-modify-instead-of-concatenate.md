# 9. Modify instead of concatenate

The principle of the last method is to reconstruct the response string character by character. But is this really necessary? 
We know from experience that it&#8217;s always faster to change characters in a string than to concatenate them.
So let&#8217;s try modifying the code to apply this idea:

```
#DECLARE($source : Text)->$result : Text var $i; $c : Integer $result:=$source $i:=1 While ($i246) $c:=Character code($result[[$i]]) Case of : (Position($result[[$i]]; ":;?/*>0) $result[[$i]]:="_" $i:=$i+1 : ($c=34) $result[[$i]]:="'" $i:=$i+1 : ($c