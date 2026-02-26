# 5. Thinking phase

When we analyze the code of the ***clean_folderName*** method, we can count 42 calls to the **[Replace string](https://developer.4d.com/docs/commands/replace-string)** command. 
That&#8217;s 42 replacement attempts, whether the targeted characters are present or not. 
What&#8217;s more, folder names are generally shorter than 40 characters. We can therefore conclude that replacement attempts fail in all tests. 
This explains why execution times are similar whether gremlins have been introduced or not.