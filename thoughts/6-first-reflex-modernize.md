# 6. First reflex: modernize

Attempting to replace characters that don&#8217;t exist requires us to rethink our processing method.
But even if we have to rethink this method, we&#8217;re going to take advantage of the new features available in the 4D language.
We&#8217;ll use a [collection](https://developer.4d.com/docs/Concepts/collection) to define invalid characters and then reconstruct a string by replacing them where necessary. In this way, we&#8217;ll only make the necessary replacements. Here&#8217;s some modern code ( ***clean_folderName_coll*** method):

```
#DECLARE($source : Text)->$result : Text var $i : Integer var illegalChars : Collection If (illegalChars=Null) illegalChars:=New collection $chars:=":;?/*>0) $result:=$result+illegalChars[$index[0]].replace Else $result:=$result+$source[[$i]] End if End for $last:=Length($result) If ($last>0) If (($result[[$last]]=".") | ($result[[$last]]=" ")) $result:=Substring($result; 1; $last-1)+"_" End if If ($result[[1]]=".") $result:="_"+Substring($result; 2) End if End if $result:=Substring($result; 1; 245)
```

The construction phase of the `illegalChars` collection can be time-consuming, so we use a process variable to ensure that this phase only has to be carried out on the first pass through the method for each process.
Let&#8217;s run the tests under the same conditions as above, but only in compiled mode:

![](http://local-learn.4d.com/wp-content/uploads/2025/11/image-14.png)

Oooouuuuups! There&#8217;s a problem ..
Code modernity doesn&#8217;t necessarily mean speed. We&#8217;ve even had to change the abscissa scale of our graph in order to display the values. This is clearly not where optimization lies.
The principle of searching through a collection is an attractive idea, but it&#8217;s far from efficient. And if you think about it, it&#8217;s quite logical.
It&#8217;s not all doom and gloom, however, as this test clearly shows a higher speed when gremlins are absent. 

So the strategy of replacing only when necessary is not useless; but it will have to be implemented differently.