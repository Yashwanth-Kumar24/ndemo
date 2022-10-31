## Lab 08

- Name:
- Email

## Part 1 Answers

1. Currently `xvda1` parition of `xvda` disk is mounted to root `/`, it's of `ext4` and is of 16GB size 
    - `df -h` lists mounted blocks, `lsblk -l` displays all about block devices.
2. Yes, there is `xvdb` of size 4 GB which is unmouted, so total there are 2 drives `xvda, xvdb`.
3. `gdisk` main menu options
   - `p` - `print the partition table`
   - `o` - `create a new empty GUID partition table (GPT)`
   - `n` - `add a new partition`
   - `i` - `show detailed information on a partition`
   - `w` - `write table to disk and exit`
4. Using the `gdisk` utility on the disk: DONE. Used `sudo gdisk /dev/xvdb` followed by `n` and created 1 GB Linux filesystem paritition.
5. `sudo mkfs.ext4 /dev/xvdb1` - Makes ext4 on new parition. To verify `lsblk -l`
6. `sudo mkdir /mnt/expanse` - creates `expanse` in `/mnt`.
7. `sudo mount /dev/xvdb1 /mnt/expanse` - Creates mount point to `/mnt/expanse`. To verify: `df -h`
8. `cd expanse` - get into mount dir. `sudo mkdir x y` - Created two directories. `sudo nano test` entered some text and saved.
9. Used `sudo strings /dev/xvdb1`. It gives the files created and the content which is inside the files as well. It lists in format such that lists all files names followed by each file and contents of it and list of files at the end.
10. On deleting and checking, still we can see the files which existed and the contents inside it. I did this multiple times and can find all the previously created files and it's content as well. Used `sudo strings /dev/xvdb1`.
11. We can use various commands like `shred` , `wipe`, `secure-delete`. 
  - I have used `shred` and did as delete the file.
  - Steps involved: 
   - create a file with some content. `sudo nano demo` and enter some text, save and exit
   - Check `sudo strings /dev/xvdb1`
   - Here is the screenshot of above work:
      - [Before applying shred](Capture1.PNG)
   - Once check content using `cat demo`. Now use `sudo shred -v demo` and then `cat demo`. 
   - We can see text overwritten 3 times(default) and is completely in unreadble format.
   - Here is the screenshot of above work:
      - ![After applying shred](Capture2.png)
   - Now to delete `sudo rm demo` can be used.
   - I have created demo2 and applied `sudo shred -zu demo2`. Here is the work
   - The best way is `sudo shred -zu demo2` - this overwrites the content 3 times(default)(can use -n 5 to make 5 times), replaces final pass with zeros to hide shredding(-z) and then removes the file(-u).
      - ![Applying strings after shred -zu](Capture4.PNG)
   - Now perform `sudo strings /dev/xvdb1` and no traces of data can be found.
   - After deleting, if we try to see the content using `strings`, it is sa follows:
      - ![Applying strings after shred](Capture3.PNG)
12. sudo umount `/dev/xvdb1`. No files and folders cannot be accessed as the disk is removed. `expanse` is now empty. To view content, just mount it to any directory and we can see the files, folders.


## Part 2 Answers

1. 
2. For `original.txt` identify:
   - Command to find the following info about `original.txt`:
   - inode number of `original.txt`:
   - number of blocks storing `original.txt`:
   - number of links to `original.txt`:
3. Command to create a hard link to `original.txt`:
   - What identifiers indicate a hard link was created?
   - Does modifying the hard linked file modify `original.txt`? Explain
4. Command to create a symbolic link to `original.txt`
   - What identifiers indicate a symbolic link was created?
   - If `original.txt` was deleted, and a new `original.txt` was created, would the sym link still work? Explain
5. Command to create a copy of `original.txt`
   - Does modifying the copied file modify `original.txt`? Explain
6. Command to move `original.txt` to another directory.
   - Does it have the same inode? Explain
   - Was the hard link you created affected? Explain
   - Was the symbolic link you created affected? Explain

## Extra Credit Answers

Line added to `/etc/fstab`:

```
Insert line here
```
