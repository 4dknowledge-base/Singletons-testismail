# 3. A silly test

If you look closely at the preceding test code, you&#8217;ll see that it&#8217;s completely idiotic. 
In fact, the code is supposed to clean up names so that they become folder names. However, in our test, we&#8217;re starting with already existing folder names&#8230; where, in essence, there&#8217;s nothing to clean up. Well done! We&#8217;ve just realized the idiocy of our test. 
If in our case the obvious is as obvious as the nose on your face, who among you had noticed this logic problem? Don&#8217;t smile, because experience shows that we have many such tests validating methods..

To make our test interesting, we have two options:

have a list of names containing problems,

introduce problems into our list of names.

We&#8217;ll choose the second solution, as it&#8217;s easy to obtain a starting list and all we have to do is introduce the problems. To do this, we&#8217;ll create a list of &#8220;gremlings&#8221; and introduce them at random:

```
$times:=New collection() $desktop:=Folder(fk applications folder) $folders:=$desktop.folders().extract("name") CONFIRM("add gremlins ?") If (ok=1) $chars:=":;?/*>