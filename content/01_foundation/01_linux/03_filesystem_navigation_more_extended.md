<!-- markdownlint-disable MD024 TOP004 -->

### Getting Help
Even seasoned developers don't memorize every command and option. Knowing how to find help is a crucial skill. Linux provides several built-in ways to get information about commands.

**Command Explanations:**

- `--help`: Most modern commands support a -`-help` flag, which provides a brief summary of the command's usage and common options. It's often quicker than `man` for a basic reminder.
  - Example: `ls --help`
- `man`: Manual pages. This is the primary way to get comprehensive documentation for almost any command. man pages are dense but incredibly detailed.
  - Example: `man ls` (press <kbd>q</kbd> to quit the man page).
  - To search within a man page, type <kbd>&#x2F;</kbd> followed by your search term and press <kbd>&#x21B5; Enter</kbd>. Press <kbd>&#x6E;</kbd> for the next match.
  
- `help`: For shell built-in commands (commands that are part of the shell itself, like `cd` or `echo`), `man` might not work or will provide a less detailed explanation. The `help` command is specifically for these.
Example: `help cd`

**Examples**
```bash
ls --help                   # Get a quick summary of `ls` options
man ls                      # Open the full manual page for `ls`
help cd                     # Get help for the built-in `cd` command
```

**Exercises**

**1. Get help for mkdir:**
Use both `--help` and `man` to learn more about the `mkdir` command. Notice the difference in the level of detail.

```bash
mkdir --help
man mkdir
```
**Expected output:** A concise usage summary for `--help` and a multi-page detailed manual for `man`.

**2. Explore a built-in command:**

Use the `help` command to understand how `echo` works, especially its options.
```bash
help echo
```
**Expected output:** The help documentation for the `echo` built-in command.


### Viewing and Searching Files
Beyond just listing files, you often need to look inside them or find specific content. These commands are your digital magnifying glass and search engine.

**Command Explanations:**

- `grep`: Global regular expression print. This powerful command searches for patterns (strings or regular expressions) within files or within the output of other commands.
  - `grep "search_term" file.txt`: Searches for "search_term" in `file.txt`.
  - `grep -i "search_term" file.txt`: Case-insensitive search.
  - `grep -r "search_term" folder/`: Searches recursively through files in `folder/`.
  - Often used with pipes (`|`) to filter the output of other commands: `ps aux | grep chrome`
- `find`: Searches for files and directories in a directory hierarchy based on various criteria (name, size, type, modification date, etc.).
  - `find . -name "*.txt"`: Finds all `.txt` files in the current directory (`.`) and its subdirectories.
  - `find /home/yourusername -type f -size +1G`: Finds files (`-type f`) larger than 1GB (`-size +1G`) in your home directory.

**Examples**
```bash
echo "apple" > fruits.txt
echo "banana" >> fruits.txt
echo "Apple" >> fruits.txt
grep "apple" fruits.txt                # Case-sensitive search
grep -i "apple" fruits.txt             # Case-insensitive search
ls -l | grep "Jun"                     # Find files modified in June (example)

mkdir temp_search
touch temp_search/fileA.log temp_search/data.csv
find . -name "file*.log"               # Find files starting with 'file' and ending with '.log' in current dir and subdirs
find temp_search -type f               # Find all regular files in temp_search
```

**Exercises**

**1. Search for a word in a file:**

Create a file named `my_notes.txt` and add a few lines of text, including the word "important" on at least one line. Then, use `grep` to find lines containing "important".
```bash
echo "This is a test note." > my_notes.txt
echo "Something important here." >> my_notes.txt
echo "Another line." >> my_notes.txt
grep "important" my_notes.txt
```
**Expected output:** The line(s) containing "important" should be displayed.

**2. Case-insensitive search:**

Modify `my_notes.txt` to include "Important" (with a capital I). Perform a case-insensitive search.
```bash
echo "Very Important details." >> my_notes.txt
grep -i "important" my_notes.txt
```

**Expected output:** Both "Something important here." and "Very Important details." should be displayed.

**3. Find specific file types:**

In your `my_project` directory (or create a new one), create a mix of `.txt`, `.log`, and `.csv` files. Use `find` to list only the `.csv` files within `my_project` and its subdirectories.
```bash
# (assuming you are in your home directory)
mkdir find_exercise
cd find_exercise
touch report.txt server.log user_data.csv metrics.log
mkdir data_sub
touch data_sub/more_data.csv data_sub/config.txt
find . -name "*.csv"
```
**Expected output:**

`./user_data.csv`

`./data_sub/more_data.csv`

### Archiving and Unarchiving

When you need to compress files to save space or combine multiple files into a single archive for easy transfer, these commands are invaluable.

**Command Explanations:**

- `zip` and `unzip`: Used for creating and extracting `.zip` archives, which are common across different operating systems.
   - `zip archive.zip file1.txt file2.txt`: Creates `archive.zip` containing `file1.txt` and `file2.txt`.
  - `zip -r archive.zip folder/`: Archives `folder/` recursively.
  - `unzip archive.zip`: Extracts contents of `archive.zip` to the current directory.
- `tar`: Tape ARchiver. A powerful utility for creating archives (often called "tarballs") and extracting them. It's often combined with compression utilities like `gzip` or `bzip2`.
  - `tar -cvf archive.tar file1.txt folder/`: Creates (`c`) a new archive, shows verbose output (`v`), and specifies the filename (`f`).
  - `tar -xvf archive.tar`: Extracts (`x`) contents from `archive.tar` verbosely.
  - `tar -czvf archive.tar.gz file1.txt folder/`: Creates a gzipped tar archive (`z` for gzip).
  - `tar -xzvf archive.tar.gz`: Extracts a gzipped tar archive.
  
**Examples**

```bash
touch doc1.txt doc2.pdf
mkdir images
touch images/photo.jpg
zip my_files.zip doc1.txt images/photo.jpg  # Zip specific files
unzip my_files.zip                      # Unzip the archive
zip -r my_folder.zip images/            # Zip a folder recursively
tar -cvf project.tar doc1.txt doc2.pdf images/ # Create a tar archive
tar -xvf project.tar                    # Extract a tar archive
tar -czvf project.tar.gz doc1.txt images/ # Create a gzipped tar archive
tar -xzvf project.tar.gz                # Extract a gzipped tar archive
```

**Exercises**

**1. Create and extract a zip archive:**

Create a new directory `zip_test`. Inside it, create three empty files: `test1.txt`, `test2.html`, and `test3.css`. Zip these three files into an archive named `my_web_files.zip`. Then, delete the original files and unzip the archive to restore them.

```bash
mkdir zip_test
cd zip_test
touch test1.txt test2.html test3.css
zip my_web_files.zip test1.txt test2.html test3.css
rm test*.txt test*.html test*.css # Be careful with rm!
ls
unzip my_web_files.zip
ls
```
**Expected output:** After `rm`, `ls` should show only `my_web_files.zip`. After `unzip`, `ls` should show all three original files again.

**2. Create and extract a gzipped tar archive:**

Create a new directory `tar_test`. Inside it, create a subdirectory `data` and place a file `config.json` inside `data`. Create a gzipped tar archive of the entire `tar_test` directory. Then, remove the original `tar_test` directory and extract the archive.

```bash
mkdir tar_test
cd tar_test
mkdir data
echo "{}" > data/config.json
cd .. # Go back to the parent directory to archive tar_test
tar -czvf my_data_backup.tar.gz tar_test/
rm -r tar_test/ # Again, be careful with rm -r!
ls
tar -xzvf my_data_backup.tar.gz
ls
ls tar_test/data/
```

**Expected output:** After `rm`, `ls` should show only `my_data_backup.tar.gz`. After `tar -xzvf`, `ls` should show `tar_test/` again, and `ls tar_test/data/` should show `config.json`.


### Let us know how it went!

You've just taken a massive leap into the world of Linux command-line fundamentals! It's completely normal if some of these concepts and commands feel overwhelming or if you need to look them up frequently. This is an ongoing learning process. The goal for now is familiarity and comfort with the basic operations.

Hang in there! The more you practice, the more these commands will become second nature, empowering you to navigate and control your development environment with confidence.

**Additional Resources**

This section contains helpful links to related content. It isn't required, so consider it supplemental.

- **Linux Command Line Tutorial for Beginners:** [A great introductory video to the terminal.](https://www.youtube.com/watch?v=uwAqEzhyjtw)

- **The Linux Command Line - A Complete Introduction by William Shotts (Book):** [A highly recommended free online book for deeper dives into the Linux command line.](https://linuxcommand.org/tlcl.php)

- **Linux Commands Cheat Sheet:** [A quick reference for common commands.](https://www.geeksforgeeks.org/linux-commands-cheat-sheet/)

- **Understanding Linux Permissions (Video):** [A detailed explanation of the permission string from ls -l.](https://www.youtube.com/watch?v=NhwJ22TEIhg)
- **Explaining Shell Initialization Files (.bashrc, .bash_profile):** [A comprehensive guide to understanding these important configuration files.](https://medium.com/@stefan.paladuta17/bash-concepts-bashrc-c65cce17d413)


**Knowledge Check**

The following questions are an opportunity to reflect on key topics in this lesson. 

- What is the purpose of the `pwd` command?
- How do you create a new directory from the command line?
- What is the difference between `cat` and `less` for viewing files?
- How can you find the PID of a running process?
- What is the primary difference between `kill` and `pkill`?
- Where would you typically add custom aliases for your Bash shell?
- How do you get comprehensive help for a command like `ls`?
- What is the purpose of the `grep` command?
- When would you choose `tar.gz` over `zip` for archiving?


**[Understand command here](https://explainshell.com/)**
<!-- end list -->
