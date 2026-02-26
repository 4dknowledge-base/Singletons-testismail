# 7. Second approach: back to basics

Our grandmothers always tell us that the best soup comes from the oldest pot &#8230; but they forget that their talent and know-how count too.
Let&#8217;s see how we can apply this principle in our case. We&#8217;re going to use the **[Position](https://developer.4d.com/docs/commands/position)** command to check whether the character should be replaced. In other words, we&#8217;ll test before replacing. Here&#8217;s the proposed code ( ***clean_folderName_position*** method):

```
#DECLARE($source : Text)->$result : Text var $i; $c : Integer $result:="" For ($i; 1; Length($source)) $c:=Character code($source[[$i]]) Case of : (Position($source[[$i]]; ":;?/*>0) $result:=$result+"_" : ($c=34) $result:=$result+"'" : ($c