# linux-reference
Linux reference
man -k which				                Search the manual with the k option for search term which
man -k “list directory contents”	  Search for phrase using quotes
man 1 which				                  Open manual section 1 page which. 
man which				                    If something in section 1 you can actually skip specifying input 1
man -k print | grep files		        Search for print and pipe to grep to filter on files keyword
Ctrl+alt+t				                  Shortcut to open terminal window
Ctrl+d					                    Shortcut to close terminal window
Echo Hello		
Echo $PATH				                  Show shell path
cal					                        current month calendar with current day highlighted
cal 2019				cal with current year
cal 12 2019				Cal with example multiple input
cal -y					run cal command with y option (current year)
cat 1> output.txt			concatenate, with redirect of standard output (1) to file output,txt
cat > output.txt			Note you don’t have to put the 1 to identify stdout
cat -k 2>> error.txt			Redirect stderr with append
cat < input.txt			Use input file for stdin, not you don’t need 0 as stdin the only input
which cal				which folder is the command cal stored in
date					current date
date -u					date in UTC
date –universal			date in UTC, with option in long form
date –help				Get help for command
date | cut --delimiter " " --field 1	Pipe date stdout to cut stdin
clear					clean up terminal 
ctrl+l					shortcut to clear the terminal
up and down arrows			Cycle through commands issued
history					Shows history of previous commands
!11					Runs 11th command in the history
!!					Run the most recent command again
history -c; history -w			Clear command history and write changes to make permanent
exit					Close terminal
ls -lh					List directory contents long format, human readable (options l & h)
whoamI
sudo bash
ping – c 3 www.google.com
apt update
apt install open-vm-tools-desktop
hostnamectl
nslookup Mint19
ifconfig -a
pwd					print working directory
ls					list directory
ls ~					list home directory for current user
ls -F					list with classify
ls -l					list using long form format
ls -a					List showing hidden files
ls *					List contents of all directories within current directory
ls D*					List contents of directories starting D within current directory. Use ? when you want to create pattern but care about length
ls file[0-9].txt			List files with prefix file and suffix is digit 0 to 9 e.g. file1.txt. Reg expr for options between []
ls -lF / | grep opt			list with grep to filter for opt directory
ls Documents/ Downloads/ Pictures/ 	List contents of multiple directories
ls -l /etc | head -n 20		List contents of etc directory, showing first 20 by piping to head
cd					change directory
cd /home/JP/Downloads			Using absolute path
cd Downloads				Change directory using relative path
cd ~					Change directory to home directory
cd					Change directory to home directory (default behaviour for cd)
cd /					Jump to base directory of system
cd ~/Desktop				Jump to my desktop directory
file Shakespeare.txt			Get file information for file, including type, resolution and bit encoding (if image)
touch newfile				Create a new file
cat file1.txt				Concatenate and output to std output- can be used to quickly check file contents
cat file1.txt file2.txt > newfile.txt	Concatenate 2 files and redirect to a new file
cat file[1-5].txt > newfile2.txt	Concatenate 5 files, using wildcard, into a new file
cat file[1-5].txt | head -n 2		Concatenate 5 files and pipe to head, showing only first 2 lines
cat file[1-5].txt | tail -n 2		Concatenate 5 files and pipe to tail, showing only last 2 lines	
head -n 20 /etc/cups/cups-browsed.conf		Use head directly to show first 20 lines
head -n 20 /etc/cups/cups-browsed.conf | tail -n 3	Use head piping to tail to cut out lines 18, 19 and 20
tac					Like cat, but reverses file vertically
rev					Reverses lines character wise
rev file[1-5].txt			Concatenate 5 files, keep vertical order but reverse line characters
less newfile.txt			Like cat but allows you to page through file (esp. useful for long input)
find / "*.txt" | less			Can pipe into less to page through long lists
touch folder{1..10}/file{1..100}	In folders 1 to 10 create 100 files
mkdir newdir				Make a directory called newdir
mkdir -p /family/pics/sum19		Make directory sum19, including any directories in path if they don’t exist
mkdir delfolder{1..3}			Make 3 folders using brace expansion
rm					Delete files or directories	
rm deleteme hello.txt			Deletes multiple files
rm *.txt				Deletes all files ending .txt as wildcard used
rm *[2,3]*				Deletes anything that has a 2 or 3 in it (using regex)
rm -r delfolder			Deletes directory delfolder, with -r option (recursive, delete all inside). Note r option dangerous, especially with wildcards

rm -ri delfolder			Deletes directories using i (interactive) option. 
rmdir delfolder/*			Only deletes empty directories
cp file1 file2				Copy file1 to new file2
cp file1 file2 destination		Copy file1 and file2 to the directory “destination”
cp -r file* destination		Copy, using wildcard, multiple files using wildcard, note using recursive option
cp -r destination destination2	Copy entire folder, using recursive option
mv file1 newfile1			Rename file1 to newfile1. Also works for directories
mv target/* .				Move everything in directory “target” to the current working directory
mv destination2/* ~			Move everything in directory “destination2” to the home directory

mv ~/Documents/target ~/Desktop/upload	Move and rename directory target to new directory upload in Desktop
locate *.conf				locate files ending .cong
locate -i *.conf			locate case insensitive
locate --limit 3 *.conf		locate with limit to 3 results
sudo updatedb				update the db used by locate – needs admin privs
find					list all files in current working directory and below it. Note find lists files and folders
find Documents				list all files in Documents directory and below			
find -maxdepth 1			Show whats in current directory
find -maxdepth 2			Show whats in current directory and 1 level down
find . -type f				Search from current directory for only file types
find . -maxdepth 2 -type d		Find directories to max depth of 2 including current working directory
find . -name "file1"			Find file called file 1 starting from working directory
find . -maxdepth 2 -iname "file1"	Search in case insensitive way with iname
find / -name "*.txt" | head -n 5	Find first 5 files by piping to head
sudo find / -type f -size +100k	Search for files, starting from root, that are greater than 100k, using super user so as having permissions to look in some directories  (otherwise permission denied)
sudo find / -type f -size +100k -size -5M | wc -l	Search between 100K and 5 Mb, and pipe into word count command to get count

sudo find / -type f -size -100k -o -size +5M | wc -l	Search less 100K OR greater 5Mb
sudo find / -type f -size +3M -size -5M -exec cp {} copy_here \;	Find all files greater than 3Mb and less than 5Mb, and copy them {} to the copy_here directory. The \; indicates end of exec option
sort words.txt				Sort file alphabetically ascending (default behaviour)
sort words.txt -r			Sort in reverse with r option
sort numbers.txt -n			Sort numerically
sort numbers0-9.txt -u			Sort numerically getting unique values
ls -l /etc | head -n 20 | sort -k 5n	Sort 1st 20 contents of etc dir by column 5 (file size) numerically
grep e -c words.txt			using the c option count number of lines with letter e
wc -l gadsby-manuscript.txt		Count number of lines in the text document
grep -i gadsby gadsby-manuscript.txt	Search for text gadsby in case insensitive manner with i option
grep -ic gadsby gadsby-manuscript.txt	Adding c option to count occurrences of text gadsby
grep -ic "our boys" gadsby-manuscript.txt	Search for phrase enclosed in quotes
grep e -vc gadsby-manuscript.txt	Invert the search with v option to count lines without letter e
grep you -ci gadsby-manuscript.txt newfile2.txt	Count occurrence of word in multiple files

tar -cvf jparchive.tar file*		c option indicates creation of new archive, v for verbose and give feedback, f to accept files, using a wildcard to take a copy of all files starting “file”. Note convention to use .tar extension for tar files.

tar -tf jparchive.tar			Look at contents of tar archive, with t option allowing to check whats inside

tar -xvf	jparchive.tar		Extract contents of tar archive
gzip jparchive.tar			Gzip compress the tar archive
gunzip jparchive.tar.gz		gunzip uncompress the tar archive
bzip2 jparchive.tar			Bzip2 compress the tar archive
bunzip2 jparchive.tar.bz2		Bunzip uncompress the tar archive
zip jpzip.zip file1.txt file2.txt file3.txt	Using the well known zip compression (as commonly found on Windows)
unzip jpzip.zip			Unzip the zip file
tar -cvzf jparchive.tar.gz file[1.2]	Create tarball and gzip compress in one go using z option
tar -xvzf jparchive.tar.gz		Uncompress using tar using the x option
uname -o				Operating system details
sudo yum install gcc			Install gcc package in Fedora with yum
sudo dnf install gcc			Install gcc package in Fedora with dnf
sudo apt-get install gcc		Install gcc package in other distros with apt-get
bash configure				Run the script called configure
lsb_release -a				Get linux distribution release info
uname -m				get computer architecture eg AMD64, X86_64 etc
dnf search / apt-cache search		Search for packages (Fedora/Ubuntu)
dnf search "web server" | less	Search and pipe through less to make easier to read
dnf info / apt-cache show		Give info on specified package
dnf makecache / apt-get update	Update package cache (Fedora/Ubuntu)
sudo dnf upgrade / sudo apt-get upgrade		Update outdated packages on system
dnf install / apt-get install		Install package (Fedora/Ubuntu)
apt remove / dnf remove		Remove packages (keep configuration files)
apt purge				Remove packages and configuration (No DNf alternative)
sudo apt-get autoremove / dnf autoremove	Remove dangling dependencies
sudo apt-get clean / dnf clean packages	Remove cached packages
ps aux					List host processes
curl localhost:8080			Test local host network


