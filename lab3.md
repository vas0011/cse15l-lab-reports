# Part 1 - Bugs
## Code for ChatServer
# Part 2 - Researching Commands
## ```find -empty examples```
**Example 1**
```
$ varun@Varuns-MacBook-Pro technical % find . -empty
  ./911report/empty.txt
```
This command searches the working directory technical and its subdirectories to look for an empty files or directories. In this example there is an empty file called empty.txt (which I created) in the 911report subdirectory of techincal. \

**Example 2**
```
varun@Varuns-MacBook-Pro technical % find ./biomed -empty
```
In this example find just searches the biomed subdirectory of technical for empty files or directories. Since there are no empty files or directories in biomed nothing is outputted by the command.
