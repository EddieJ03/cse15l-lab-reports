# LAB REPORT 2


## Code Change 1

![Image](./images/test2issue.png)

Here is the link to code change on GitHub: [link](https://github.com/EddieJ03/markdown-parse/commit/d4d957868986111536c6dfca88949eb8256d6d29)

The the link to the file that caused the failure-inducing input is here: [link](./test-file2.md)

The symptom that this failure-inducing input gives is shown below:
![Image](./images/showissuetest2.png)

The part of the **failure-inducing input** that results in the bug is the last sequence of characters with no valid links. The **bug** in the code is that in each run of the while loop, the index where the parser starts looking for links continuously gets reset to 0 since the closing parenthesis' index is -1 because it does not exist in the last sequence of characters. The **symptom** that results from this bug is an infinite loop which causes an out of memory error. 



