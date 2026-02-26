# 2. Setting up a unit test

In the remainder of our study, and therefore of this document, we will propose successive improvements and compare them. To facilitate these comparisons, we start by setting up a method for running tests and displaying results. Here&#8217;s the test method:

```
$times:=New collection() $desktop:=Folder(fk applications folder) $folders:=$desktop.folders().extract("name") $time:=Milliseconds For ($i;1;4) For each ($folder;$folders) $name:=clean_folderName ($folder) End for each End for $times.push(Milliseconds-$time) $time:=Milliseconds //For ($i;1;4) // For each ($folder;$folders) // $name:=clean_folderName1 ($folder) // End for each //End for //$times.push(Milliseconds-$time) ALERT($times.join("r"))
```

In this code, we see a comment section that anticipates the test on a modified method.

The method retrieves the names of sub-folders present in the machine&#8217;s application folder to form the `$folders` collection. On our test machine, the collection has 230 elements. 

We use a `$times` collection to store the calculation times of each test run. 

Today&#8217;s processors are very fast, and the number of 230 calculations is not large enough to measure times properly, as we don&#8217;t have a stopwatch below the millisecond. We therefore have to artificially increase calculation times by running the processes 4 times, which gives us a thousand tests.