# Name and Contents of Each File in a File

![gnu_logo](gnu_logo.png)

 The post lists a self-contained bash script to output the name and contents of each file listed in a file.

**Script**

```
FILEA="File A line 1
File A line 2
File A line 3"

echo "$FILEA" > filea.txt

FILEB="File B line 1
File B line 2
File B line 3"

echo "$FILEB" > fileb.txt

FILEC="File C line 1
File C line 2
File C line 3"

echo "$FILEC" > filec.txt

FILELIST="filea.txt
fileb.txt
filec.txt"

echo "$FILELIST" > filelist.txt

while read FILENAME
do
        echo "$FILENAME"
        cat $FILENAME
        
done < filelist.txt
```

**Call With**

```
source script.sh
```

Reference 

- [Free Online HTML Escape / Unescape Tool - FreeFormatter.com](http://www.freeformatter.com/html-escape.html#ad-output)  
- GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project) 