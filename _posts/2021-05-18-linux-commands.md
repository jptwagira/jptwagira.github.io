---
layout: post
title: linux basic commands
date: 2021-05-18 14:24:00
description: Linux HOWTOS
tags: code howtos linux
categories: research
related_posts: true
---

### tecmint.com
---
* [60 essential Linux commands](https://www.hostinger.com/tutorials/linux-commands) and bash scripting tutorial for beginners [here](https://linuxconfig.org/bash-scripting-tutorial-for-beginners)

* [Vim cheatsheet](https://devhints.io/vim) and [more](https://github.com/jptwagira/programing-tips/blob/main/computing.md)


* [fdupes – A Command Line Tool to Find and Delete Duplicate Files in Linux](https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/)


* Merge two pdf files side by side in a command line [here](https://superuser.com/questions/917190/merge-two-pdf-files-side-by-side-in-command-line)
* Joining PDFs with Linux command line by [Judith Roth](https://makandracards.com/makandra/151861-joining-pdfs-with-linux-command-line)
```.sh
pdfunite *.pdf output.pdf
sudo apt install texlive-extra-utils
```


* Split files, note the naming scheme
```.sh
pdfseparate File1.pdf temp-%04d-file1.pdf
```

* Adding WaterMarks to pdf [here](https://www.togaware.com/linux/survivor/pdf-watermarks.html) and [here](https://superuser.com/questions/280659/how-can-i-apply-a-watermark-on-every-page-of-a-pdf-file)
```.sh
pdftk survivor.pdf background watermark.pdf output survivor_watermarked.pdf
pdftk original.pdf stamp watermark.pdf output final.pdf
```

* How to reverse the page order of a PDF file [unix](https://unix.stackexchange.com/questions/439959/how-to-reverse-the-page-order-of-a-pdf-file)
```.sh
qpdf --empty --pages infile.pdf z-1 -- outfile.pdf
```

* Displace Days and time for history command [here](https://askubuntu.com/questions/391082/how-to-see-time-stamps-in-bash-history) and [here](https://linuxize.com/post/history-command-in-linux/)
```.sh
echo 'HISTTIMEFORMAT="%F %T "' >> ~/.bashrc
```

* /etc/apt/sources.list
   - Example of /etc/apt/sources.list Ubuntu 18.04 [here](https://gist.github.com/h0bbel/4b28ede18d65c3527b11b12fa36aa8d1)

* Some useful commands
[Copying a Directory with SCP](https://stackabuse.com/copying-a-directory-with-scp) and [here](https://linuxhint.com/rsync_copy_files/)
```.sh
rsync -avz <path to files to copy files from> <path to copy files to>
scp <path to files to copy files from> <path to copy files to>
```

* How To Clear Shell History In Ubuntu Linux [here](https://www.cyberciti.biz/faq/clear-the-shell-history-in-ubuntu-linux/)

* searching a word or a variable using grep command
```.sh
grep -r "n_ice_group" *
grep -r "1.35634" *
```

* How to rename multiple files on Linux [here](https://linuxconfig.org/how-to-rename-multiple-files-on-linux)\
```.sh
mmv "*Log_Likelihood_direction_*" "#1Log_Likelihood_direction_scan_event_11_#2"
```

* Dumping the output file in a 
```.sh
python file >> output.txt
```

* How to make tree output only directories
```.sh
tree -d
tree -d <target_directory>
tree -d -L 2 .
tree -d -L 3 home/downloads/
```

* 10 Useful du (Disk Usage) Commands to Find Disk Usage of Files and Directories [here](https://www.tecmint.com/check-linux-disk-usage-of-files-and-directories/)

* Commands to find disk usage of files and directories
```.sh
du -h downloads/
du -ah downloads/
du -mh downloads/
du -mh --max-depth=1 downloads/
find . -type f -exec du --human {} + | sort --human
find . -type f -exec du --human {} + | sort --human --reverse
find . -type f -exec du --human {} + | sort --human --reverse | head
```

* Sorted output for du -h Commands to find disk usage [cyberciti.biz](https://www.cyberciti.biz/faq/how-do-i-sort-du-h-output-by-size-under-linux/#:~:text=How%20can%20I%20sort%20du,added%20the%20gnu%2Fsort%20command.)
```.sh
du -mh --max-depth=1 downloads/ | sort -h
du -mh --max-depth=1 downloads/ | sort -h -r
du --human-readable --max-depth=1 downloads/ | sort --human-numeric-sort -r
du -h | sort -h | head
du -h | sort -hr | head
du --human-readable | sort --human-numeric-sort | head
du --human-readable | sort --human-numeric-sort -r | head
```
