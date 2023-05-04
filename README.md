Download Link: https://assignmentchef.com/product/solved-csc482-homework1-command-line-basics
<br>
The objective of this assignment is for students to develop basic command line skills using the bash shell to navigate the filesystem and work with files. While graphical interfaces are easy to learn, command lines are more powerful and make automation of tasks easy. Furthermore, command line skills are essential to completing future labs in this course.

You will begin this lab by reading and completing the exercises from the first two chatpers of Learn Enough Command Line to be Dangerous. To learn more about the command line, complete the William Schotts’ Learning the Shell tutorial. If you need commands that you have not learned from these sources or the text of the lab, <em>The Linux Command Line </em>is a free online book that will cover everything you need to know.

Readings and related topics.

<ol>

 <li>Michael Hartl. Learn Enough Command Line to be Dangerous. <a href="https://www.learnenough.com/command-line-tutorial">https://www.learnenough. </a><a href="https://www.learnenough.com/command-line-tutorial">com/command-line-tutorial</a><a href="https://www.learnenough.com/command-line-tutorial">.</a></li>

 <li>William Shotts. Learning the Shell. <a href="http://linuxcommand.org/lc3_learning_the_shell.php">http://linuxcommand.org/lc3_learning_the_ </a><a href="http://linuxcommand.org/lc3_learning_the_shell.php">php</a><a href="http://linuxcommand.org/lc3_learning_the_shell.php">.</a></li>

 <li>William Shotts. <em>The Linux Command Line, Fifth Internet Edition</em>. <a href="http://linuxcommand.org/tlcl.php">http://linuxcommand. </a><a href="http://linuxcommand.org/tlcl.php">org/tlcl.php</a><a href="http://linuxcommand.org/tlcl.php">.</a></li>

</ol>

Lab environment. Students will complete the lab on their SEED Linux VM, which is available in their folder on the NKU College of Informatics vSphere server. Here is the <a href="http://faculty.cs.nku.edu/~waldenj/files/csc482-lab0-file.zip">ZIP file used in the lab</a><a href="http://faculty.cs.nku.edu/~waldenj/files/csc482-lab0-file.zip">.</a>

<h1>1          Lab Tasks</h1>

2.1        Task 1: Learn Enough Command Line, Chapter 1

Read the text and complete the exercises in chapter 1 of <a href="https://www.learnenough.com/command-line-tutorial">Learn Enough Command Line to be Dangerous</a><a href="https://www.learnenough.com/command-line-tutorial">. </a>Write the answer to exercise 1 from section 1.7.1 in the Task 1 section of your lab report.

2.2        Task 2: Learn Enough Command Line, Chapter 2

Read the text and complete the exercises in chapter 2 of <a href="https://www.learnenough.com/command-line-tutorial">Learn Enough Command Line to be Dangerous</a><a href="https://www.learnenough.com/command-line-tutorial">. </a>Write the answers to exercises 2 through 4 from section 2.4.1 in the Task 2 section of your lab report, with one exercise per line.

2.3      Task 3: Archiving Files

You will need to be able to extract and uncompress files from archive formats like tar and zip in this assignment, so let us practice a bit with these formats before starting.

$ mkdir temp

$ cd temp

$ cp /bin/ls /bin/bash .

$ cd –

$ zip temp.zip temp

$ zipinfo -l temp.zip

When you run zipinfo to list the contents of the zip archive file, you will see that it does not contain either of the two files in the temp directory. You need to add an option to the zip command to include those files. Read the documentation with man zip to see what option you need to use, then archive the files correctly. Once they are archived correctly, proceed with the next step.

$ cd /tmp

$ unzip ˜/temp.zip

$ ls -l temp

Verify that you see the files before deleting the temporary directory and returning to your home directory.

In the next step, we will create a tar archive (tape archive) of the files. The c option creates an archive, while the t option lists archive contents, and the x option extracts files from the achive. We use the verbose option v to show more output and the f option to create an archive as a file rather than to magnetic tape. The f option must appear last as it takes an option argument–the filename of the archive to create.

$ tar cvf temp.tar temp

$ tar tvf temp.tar temp

$ cd /tmp

$ rm -rf temp

$ tar xvf ˜/temp.tar

Returning to your home directory, notice that the zip archive is smaller than the tar archive.

$ ls -l temp.{tar,zip}

This difference is because tar does not perform compression. While this seems to be a disadvantage on first look, it turns out that separating the creation of an archive from its compression has its advantages. The science of data compression has advanced considerably from the invention of zip in 1989. Once you have created a tar archive, you can compress it with any compression program desired, ranging from GNU’s implementation of the zip compression algorithm, gzip, to widely used standards like bzip2, to modern compression tools like xz. Let’s try and compare these options.

$ cp temp.tar temp1.tar

$ gzip temp1.tar

$ cp temp.tar temp2.tar

$ bzip2 temp2.tar

$ cp temp.tar temp3.tar

$ xz temp3.tar

$ ls -l temp*.tar*

Uncompress each of the compressed archives with the d (decompress) option, then use the binary comparison command cmp to verify that compression and decompression did not cause any data corruption.

$ gzip -d temp1.tar

$ cmp temp.tar temp1.tar

$ bzip2 -d temp2.tar

$ cmp temp.tar temp2.tar

$ xz -d temp3.tar

$ cmp temp.tar temp3.tar

Once you are comfortable with the archive commands, use the curl command to download the lab file from the URL found in Lab Environment section of the Overview of this lab. Write the command you used to unpack the file for this section of your lab report.

2.4       Task 4: Finding the Secret Word

Your goal is to unpack csc482-lab0-file.zip and find the secret word contained within the extracted files. This ZIP file will unpack into a directory structure containing many levels of directories with many files, some of which themselves may be archives that need to be unpacked and explored. The file containing the secret word may contain an extensive amount of data, but you can identify the line containing the password because it will contain the string “The secret is ” followed by the secret word.

While searching for the file, keep track of the commands that you used. The history command will show all commands issued during the current bash session. Write the secret word followed by a blank line then the list of the commands you used to find the secret word in this section of your lab report.