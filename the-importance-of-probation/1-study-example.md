# 1. Study example

To illustrate the points made in this document, we&#8217;ll take an example encountered in a real-life study carried out by our Professional Services teams. The method proposed below receives a string of characters and corrects it to make it compatible with OS requirements (Mac and Windows) to become a folder name. To do this, for example, you need to remove the &#8220;:&#8221; and &#8220;/&#8221; characters from the string, which are folder separators in Mac OS and Windows respectively. To ensure cross-platform naming, we treat strings globally, so that the &#8220;/&#8221; character, which is permitted on Mac OS, is modified. Characters modified in this way are mainly replaced by &#8220;_&#8221;, or deleted. Quotation marks are replaced by a simple apostrophe. 

Here&#8217;s the method named ***clean_folderName*** that caught our attention and that we&#8217;d like to improve: 

```
#DECLARE($source:text)->$result:text var $i;$last : integer $result:=Replace string($source;":";"_") $result:=Replace string($result;";";"_") $result:=Replace string($result;"?";"_") $result:=Replace string($result;"/";"_") $result:=Replace string($result;"/";"_") $result:=Replace string($result; "*";"_") $result:=Replace string($result;Char(34);"'") $result:=Replace string($result;">";"_") $result:=Replace string($result;"0) If (($result[[$last]]=".") | ($result[[$last]]=" ")) $result:=Substring($result;1;$last-1)+"_" End if If ($result[[1]]=".") $result:="_"+Substring($result;2) End if End if $result:=Substring($result;1;245)
```