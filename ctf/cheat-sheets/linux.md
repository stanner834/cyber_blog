# Linux

#### **Directory and File Navigation**

* `cd <directory>`\
  Change to the specified directory.
  * Example: `cd /home/user/documents`
* `ls [options]`\
  List the contents of the current or specified directory.
  * Common Options:
    * `-l` : Long format listing
    * `-a` : Show hidden files
  * Example: `ls -la`

#### **File Viewing**

* `less <file>`\
  View the contents of a file one screen at a time.
  * Navigation:
    * `Space` : Scroll forward
    * `b` : Scroll backward
    * `q` : Quit

#### **Pattern Searching**

* `grep <pattern> <file>`\
  Search for lines matching a specific pattern in a file.
  * Common Options:
    * `-i` : Case-insensitive search
    * `-r` : Recursively search in directories
    * `-n` : Show line numbers of matches
  * Example: `grep -i "error" logfile.txt`

#### **File and Directory Search**

* `find <path> [criteria]`\
  Search for files and directories based on criteria.
  * Common Criteria:
    * `-name <name>` : Search by name (case-sensitive)
    * `-iname <name>` : Search by name (case-insensitive)
    * `-size <size>` : Search by file size (e.g., `+1M` for files > 1MB)
    * `-type <type>` : Search by type (`f` for files, `d` for directories)
    * `-mtime <days>` : Search by modification time
  * Example: `find /home/user -name "*.txt"`
