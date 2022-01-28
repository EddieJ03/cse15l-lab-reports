# LAB REPORT 2

## Code Change 1

<img src="./images/issue2.png" alt="test2" width="1500px"/>

Here is the link to code change on GitHub: [link](https://github.com/EddieJ03/markdown-parse/commit/d4d957868986111536c6dfca88949eb8256d6d29)

The the link to the file that caused the failure-inducing input is here: [link](https://raw.githubusercontent.com/EddieJ03/markdown-parse/main/test-file2.md)

Here is the contents in the file:
```
# Title

[a link!](https://something.com)
[another link!](some-page.html)

some paragraph text after the links
```

The symptom that this failure-inducing input gives is shown below:
![Image](./images/showissuetest2.png)

The part of the **failure-inducing input** that results in the bug is the last sequence of characters with no valid links. The **bug** in the code is that in each run of the while loop, the index where the parser starts looking for links continuously gets reset to 0. This is because in the last sequence of characters there exists no closing parenthesis so in the code the variable `closeParen` gets set to -1 and the line `currentIndex = closeParen + 1` resets currentIndex to 0. The **symptom** that results from this bug is an infinite loop which causes an out of memory error. 

<hr/>

## Code Change 2

<img src="./images/issue8.png" alt="test8" width="1500px"/>

Here is the link to code change on GitHub: [link](https://github.com/EddieJ03/markdown-parse/commit/3d7fafa13d1632f54216240579a00f47b818a3a3)

The the link to the file that caused the failure-inducing input is here: [file](https://raw.githubusercontent.com/EddieJ03/markdown-parse/main/test-file8.md)

Here are the contents in the file:
```
[](a link on the first line)
[
```

The symptom that this failure-inducing input gives is shown below:
![Image](./images/showissuetest8.png)

The part of the **failure-inducing input** that results in the bug is that the string between the parentheses contains spaces. The **bug** in the code is that it does not check for the case that the string between the parentheses contains spaces for link validity. The **symptom** that results from this bug is that the parser returns the string bewteen the parentheses as a valid link when it is not. 

<hr/>

## Code Change 3

<img src="./images/issue5.png" alt="test5" width="1500px"/>

Here is the link to code change on GitHub: [link](https://github.com/EddieJ03/markdown-parse/commit/9d484ecab8eed4f9a8b32db44eb6a5cf302dd54b)

The the link to the file that caused the failure-inducing input is here: [file](https://raw.githubusercontent.com/EddieJ03/markdown-parse/main/test-file5.md)

Here are the contents in the file:
```
# title

[stuff]

paragraph

(page.com)
```

The symptom that this failure-inducing input gives is shown here:
![Image](./images/showissuetest5.png)

The part of the **failure-inducing input** that results in the bug is the stand alone parentheses with a link inside it. The **bug** in the code is in line 70 where it does not consider whether the opening parenthesis directly follow the closing square bracket before adding the string to the list that will be returned. The **symptom** that results from this bug is that `page.com` is considered as a valid URL in the markdown file which is incorrect. 