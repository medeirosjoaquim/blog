---
title: Manipulate docker images with bash loop
date: 2017-10-09
---
# Manipulate docker images with bash loop
Bash is powerful and simple. Everything you can list in the screen can be
set in a variable and manipulated.

I've just started using Docker and I wanted to do stuff with images like
copy, move, delete or whatever.

To list the images We can do

```
sudo docker images -a
```

This command will return all the images in the system.
I had some garbage like
```
<none>                  <none>              efe763a68df2        04 days ago         892MB
<none>                  <none>              g83b695043d3        05 days ago         892MB
```

that I've wanted to get rid of.

So, how We can do it?

Well, first let's loop the results and read it **line** line by line


```
sudo docker images -a | while read line; do

    commands $line
 done
```

Now, every line of the results will have it's value passed through $line variable;

I want to delete the images <none>, so:

```
sudo docker images -a | while read line; do
   if [[ $line =~ none  ]]; then
   sudo docker rmi $line
  fi
done
```

$line contains the whole line and We want just the image ID's, listed in the
third columns.

We can use awk or sed or even grep to catch that.
I'll use awk:  __awk '{ print $3 }' filename__


```
sudo docker images -a | while read line; do
   if [[ $line =~ none  ]]; then
    rmv=$(echo $line | awk '{ print $3 }')
   # ALWAYS USE ECHO TO TEST ANY CRITICAL COMMAND; like
   #sudo echo $rmv  ; if it shows exactly what you want to delete;
   $ then proceed
   sudo docker rmi $rmv
  fi
done
```

You could use this kind of loop to build daily reports for example.

Hope you've enjoyed








