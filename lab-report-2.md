# Lab Report 2

## First Code Change

### Code difference


![](Screenshots/1_codeChange.png)
The [test file](Report-2-Markdown/test-file.md) that had the failure inducing input.

Symptom of *Failing-Inducing* input:
![](Screenshots/1-symptom.png)
While hard to see in the markdown file, there is actually an *empty line* underneath the last link. Since the last line of the method makes the ```currentIndex``` variable only be index value larger than the closed parenthesis, the ```while``` loop's condition is not satisfied once the last closed parenthesis is reached and will continue the loop from the beginning. However, since there is no longer any open brackets, the ```openBracket``` variable and all succeeding variables after it that use the ```markdown.indexOf``` **method** will become ```-1```. Therefore, the value of ```currentIndex``` will once again become ```0``` by the end of the second loop and restart everything from the beginning, causing an ***infinite loop*** until there is no more memory left.

---
## Second Code Change