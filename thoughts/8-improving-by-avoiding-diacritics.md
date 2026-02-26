# 8. Improving by avoiding diacritics

Let&#8217;s look at the following line:

```
(Position($source[[$i]];":;?/*>0)
```

The characters tested are all non-alphabetic, so there&#8217;s no upper or lower case version. 
We can therefore modify the line using the option to compare using character codes:

```
(Position($source[[$i]];":;?/*>0)
```

Theoretically, this code is faster because it&#8217;s quicker to do a code comparison than a diacritical one. It&#8217;s time to check whether this is the case by running a new series of tests with the ***clean_folderName_position2*** method:

![](http://local-learn.4d.com/wp-content/uploads/2025/11/image-17-965x1024.png)

The execution times of this code are indeed improved, which is starting to make a real difference ..
However, we must continue our efforts.