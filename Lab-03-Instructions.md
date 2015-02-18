* Directory A should contain directories B, C and D
* Directory C should contain directories E and F
* Directory D should contain directories G, H and I
* Directory H should contain directories J and K
Now, go to your home account on Github and find the URL for the forked repository. 

Important: you should NOT be copying this:

https://github.com/StThomas-SEIS660/Lab-03

Instead, it should look like this:

https://github.com/your_Github_name/Lab-03
[consider drawing a picture] 

Clone the Github repository you forked as Lesson 03 to your VM, in your /vagrant directory **on the VM**. 

````
vagrant@precise64:/vagrant$ git clone https://github.com/CharlesTBetz/Lab-03.git
Cloning into 'Lab-03'...
remote: Counting objects: 31, done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 31 (delta 7), reused 31 (delta 7), pack-reused 0
Unpacking objects: 100% (31/31), done.
vagrant@precise64:/vagrant$ 
````
Notice I used the username CharlesTBetz; **this must be replaced with your Github user name**. 
**Try git out**
CD to the new Lab-03 directory that git created:
    vagrant@precise64:/vagrant$ cd Lab-03/
Create a file called myStudentID-testfile, e.g. stud0001-testfile.md.

    nano MyStudentID-testfile.md 
    

Put some Markdown content in it, starting with  the phrase "Hello World." ([What's Markdown?](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)).

Exit nano.

Add your file to your git repository

    git add myStudentID-testfile.md
    git commit "my first commit"
    
You will get:

````
vagrant@precise64:/vagrant/Lab-03$ git commit -m "my first commit"
[master 5c9b944] my first commit
 Committer: vagrant <vagrant@precise64.(none)>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 2 insertions(+)
 create mode 100644 teststud-testfile.md
````

Disregard the issue with your user name and email for now.

Now, edit the file again. Add "Hello Again" as a second line. You have now made a change, relative to what you committed. You can see that change through issuing the command 'git diff':

````
vagrant@precise64:/vagrant/Lab-03$ git diff
diff --git a/teststud-testfile.md b/teststud-testfile.md
index 557db03..fcb9459 100644
--- a/teststud-testfile.md
+++ b/teststud-testfile.md
@@ -1 +1,3 @@
 Hello World
+Hello Again
+
````

We will be covering git in more detail as we go, but this clearly shows that Hello Again has been added. 

Commit it again (you only need to add it once): 

````
vagrant@precise64:/vagrant/Lab-03$ git commit teststud-testfile.md -m "second commit"
[master b61fe73] second commit
 Committer: vagrant <vagrant@precise64.(none)>
[ ... email error message ... ]

 1 file changed, 1 insertion(+)
````

Go back into nano and replace "World" with "Mars." 

Run git diff again:

````
vagrant@precise64:/vagrant/Lab-03$ git diff
diff --git a/teststud-testfile.md b/teststud-testfile.md
index fcb9459..dcc7a8e 100644
--- a/teststud-testfile.md
+++ b/teststud-testfile.md
@@ -1,3 +1,3 @@
-Hello World
+Hello Mars
 Hello Again
````

Commit it again:
 
````
vagrant@precise64:/vagrant/Lab-03$ git commit -m "3rd commit"
[master a077b45] 3rd commit
[... email error message ...]
 1 file changed, 1 insertion(+)
````

Now, let's look at our commit history:

````
vagrant@precise64:/vagrant/Lab-03$ git log -p teststud-testfile.md
commit 8057ec263df1830de0099907be08ecc44bd509ff
Author: vagrant <vagrant@precise64.(none)>
Date:   Wed Feb 18 00:32:49 2015 +0000

    third commit

diff --git a/teststud-testfile.md b/teststud-testfile.md
index fcb9459..dcc7a8e 100644
--- a/teststud-testfile.md
+++ b/teststud-testfile.md
@@ -1,3 +1,3 @@
-Hello World
+Hello Mars
 Hello Again
 

commit b61fe735241bd17493e4e0e8222bc9dbd38ca879
Author: vagrant <vagrant@precise64.(none)>
Date:   Wed Feb 18 00:30:43 2015 +0000

    second commit

diff --git a/teststud-testfile.md b/teststud-testfile.md
index 9801343..fcb9459 100644
--- a/teststud-testfile.md
+++ b/teststud-testfile.md
@@ -1,2 +1,3 @@
 Hello World
+Hello Again
 

commit 2d7f98a139ffcef0ea1ceaf47b7ee7ec4e4fefd6
Author: vagrant <vagrant@precise64.(none)>
Date:   Wed Feb 18 00:29:59 2015 +0000

    my first commit

diff --git a/teststud-testfile.md b/teststud-testfile.md
new file mode 100644
index 0000000..9801343
--- /dev/null
+++ b/teststud-testfile.md
@@ -0,0 +1,2 @@
+Hello World
+
````

All of these changes have been locally committed to your git instance on your Vagrant virtual machine. Let's send them back up to your fork at Github:

````
vagrant@precise64:/vagrant/Lab-03$ git push origin master
Username for 'https://github.com': CharlesTBetz
Password for 'https://CharlesTBetz@github.com': 
To https://github.com/CharlesTBetz/Lab-03.git
   99bd033..8057ec2  master -> master
vagrant@precise64:/vagrant/Lab-03$ 
````

Finally, go back to your browser and issue a pull request:
There is much to learn about git and this lab is not intended to be a full tutorial. We will cover further aspects as necessary. 