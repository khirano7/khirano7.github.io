---
layout: essay
type: essay
title: "Asking Smart Questions Is Harder Than You Think"
# All dates must be YYYY-MM-DD format!
date: 2022-09-08
published: true
labels:
  - Smart Questions
  - StackOverflow
---

### What Makes A Question Smart?

I definitely do not always ask smart questions. There have been many times where I realize the stupidity of my question as soon as it leaves my mouth. While asking "stupid" or "dumb" questions is not always a horrible thing, it's also important to acknowledge that "smart" questions are more likely to get smart answers. 

[This article](http://www.catb.org/esr/faqs/smart-questions.html) by Eric Steven Raymond and Rick Moen goes in depth into how to ask questions the "smart" way. From creating your question titles, to using specific language and phrases, to even knowing how to find the correct place to post your question, there are many ways to improve your questions so that they are considered "smart". 

### Looking At An Example

Lets look at [this](https://stackoverflow.com/questions/54895002/modulenotfounderror-with-pytest) example I found on Stack Overflow. In this question, the user explains how they are repeatedly getting a ModuleNotFoundError and need some assistance on resolving this.

```
Q: I want my tests folder separate to my application code. My project structure is like so

myproject/
  myproject/
    myproject.py
    moduleone.py
  tests/
    myproject_test.py

myproject.py

from moduleone import ModuleOne
class MyProject(object)
....

myproject_test.py

from myproject.myproject import MyProject
import pytest
...

I use myproject.myproject since I use the command

python -m pytest
from the project root directory ./myproject/

However, then the imports within those modules fail with

E ModuleNotFoundError: No module named 'moduleone'

I am running Python 3.7 and have read that since 3.3, empty __init__ files are no longer needed which means my project becomes an implicit namespace package

However, I have tried adding an __init__.py file in myproject/myproject/ and also tried adding a conftest.py file in myproject/ but neither works

I have read answers that say to mess with the paths and then upvoted comments in other questions saying not to.

What is the correct way and what am I missing?

EDIT;

Possibly related, I used a requirements.txt to install pytest using pip. Could this be related? And if so, what is the correct way to install pytest in this case?

EDIT 2:

One of the paths in sys.path is /usr/src/app/ which is a docker volume lined to /my/local/path/myproject/.

Should the volume be /my/local/path/myproject/myproject/ instead?
```

As you can see from the question above, the user states the problem they are facing, and the various ways they have already tried to fix the issue. This shows to others that they have already researched possible solutions, and that they aren't just asking for help as soon as something goes wrong. In the original Stack Overflow post, they also added links to documentation and other existing questions to reference the solutions they already tried.

The user also included some code in their questions to give others an idea of how they are implementing this into their project. This is helpful, since the user only included the specific lines that were relevant to the issue instead of uploading the whole file. Their question title: "ModuleNotFoundError with pytest", is also concise and to the point, making it easier for others to find this question through internet searches. 

As of writing this essay, this question has 17 answers, with the accepted solution shown below. This questions was asked on February 26, 2019. Although there were answers posted on that same day, there is still activity on this question as recently as October 2021. This suggests that the community views this as a valuable question that others may look at for a solution, since a dumb question would just get ignored by the majority.
```
A: Solution: use the PYTHONPATH env. var

PYTHONPATH=. pytest

As mentioned by @J_H, you need to explicitly add the root directory of your project, since pytest only adds to sys.path directories where test files are (which is why @Mak2006's answer worked.)

Good practice: use a Makefile or some other automation tool
If you do not want to type that long command all the time, one option is to create a Makefile in your project's root dir with, e.g., the following:

.PHONY: test
test:
    PYTHONPATH=. pytest
Which allows you to simply run:

make test

Another common alternative is to use some standard testing tool, such as tox.
```

### A "Dumb" Question?

In contrast to the previous example we saw, let's look at [this](https://stackoverflow.com/questions/64614354/error-matplotlib-installing-please-help-me) question also found on Stack Overflow. This user is also facing an error that needs to be resolved, but their method of approach is different from the previous user.

```
Q: I wanted to install matplotlib like this python -m pip install -U pip python -m pip install -U matplotlib 
and it gave me this Error Code : ERROR: Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output. 
Can you help me ?
```

This user doesn't go into detail about the troubleshooting they did before asking this question, which implies that the user posted this question as soon as they received this error. Even if this was not the case, others are more likely to ignore your question if it looks like you didn't put much effort into finding a solution on your own.

Additionally, their question title is "ERROR Matplotlib installing PLEASE HELP ME?", which does not go into the specifics about the type of error they are getting. They also included a "PLEASE HELP ME" in the title, which may seem like a way to grab attention for an urgent issue, but in reality it's just a surefire way to get ignored.

Luckily, there are a couple of answers posted, with the accepted one shown below. However, this does not have as much interaction as the previous question. Their post was even downvoted, showing that others view this question as unclear or not useful. 

```
A: Try using pip install matplotlib in the terminal (Unix/Linux), cmd or Powershell in Windows.
```

### Questioning Your Questions 

All this talk about "smart" and "dumb" questions could make you more reluctant to reach out to others for help. However, it's important to know how to ask smart questions if you want to receive helpful answers. While it's tempting to post a quick question asking for a quick solution, most people don't want to just give out answers and instead want you to know why that answer is correct. Taking the time to do your own research and problem solving before asking a question will show that you're willing to learn, which in turn makes it more likely for your question to be answered. In the case of Stack Overflow, since this is a public site, normally the more helpful and useful questions are given more attention.

