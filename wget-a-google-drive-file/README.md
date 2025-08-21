# wget a Google Drive file

![google_drive_logo](google_drive_logo.png)

Note: this isn't working, just listing it for reference at this point. It was purported to work.

This posts lists how to get a Google Drive file using wget (and sed and rm).

Copy and paste this into a bash line.

function gdrive_download () {
 CONFIRM=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate "https://docs.google.com/uc?export=download&id=$1" -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')
 wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$CONFIRM&id=$1" -O $2
 rm -rf /tmp/cookies.txt
}

gdrive_download 120aPYqveqPx6jtssMEnLoqY0kCgVdR2fgMpb8FhFNHo test.txt

These two commands will download the content you see above at link: [https://docs.google.com/document/d/120aPYqveqPx6jtssMEnLoqY0kCgVdR2fgMpb8FhFNHo/edit?usp=sharing](http://docs.google.com/document/d/120aPYqveqPx6jtssMEnLoqY0kCgVdR2fgMpb8FhFNHo/edit?usp=sharing)

For other files use the ID of the file and call grive\_download with the ID and what you'd like to name the resulting file:

gdrive_download ID filename.txt

**References**

-   The gdrive\_download function [link](http://gist.github.com/iamtekeste/3cdfd0366ebfd2c0d805) and [link](http://unix.stackexchange.com/questions/136371/how-to-download-a-folder-from-google-drive-using-terminal).
    
-   [How to set an iframe to fill the frame width and height](http://stackoverflow.com/questions/3306124/how-to-make-a-html-iframe-100-width-and-height)
    
-   [How to Set the Top Margin & Left Margin on Google Docs](http://smallbusiness.chron.com/set-top-margin-left-margin-google-docs-26666.html)
    
-   Drive logo from [link](http://www.google.com/drive/).