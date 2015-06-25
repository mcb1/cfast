# Introduction #

[Google Code](http://code.google.com) uses [Subversion](http://subversion.tigris.org) (SVN) for version control.  Subversion is widely considered as an improved versioning method over CVS.  This Wiki page provides instructions on using a browser called _SmartSVN_ or the command line to obtain files from the cfast SVN Repository.

# Using SVN via the Browser SmartSVN #

[SmartSVN](http://smartsvn.com) is available as freeware.  A for-purchase version of _SmartSVN_ is available that has additional capabilities, but for most users the free version will suffice.  Note that other programs are available (list of some found [here](http://subversion.tigris.org/links.html#clients)).

## Adding the Repository to SVN ##

  * After installing _SmartSVN_, launch the program.
  * The program will open with a _Welcome to SmartSVN_ window.  Select **Check out project from repository**.
  * A _Check Out Project_ window will open.
    * In the **Repository** box type http://cfast.googlecode.com/svn
    * Click **Next**
    * In the **Location** window, browse to **trunk**, then **cfast**, then **trunk** a second time.
    * Click **Next**
    * A pop-up window will open asking "Do you want to additionally check out the path up to the project root?" Click **No**
    * In the **Local Directory** box, enter or select the location to place the repository on your local disk.
    * Select the **Into subdirectory** Check out location and enter **cfast** in the text box.
    * Click Next
  * If you desire to see something other than the URL in _Check Out Project_ window select **Add a new project** and enter a name.  'cfast' would be suitable here.
  * Click **Finish** to check out the code

At this point, the entire cfast project will be copied from the repository to your computer.

### After the First Time ###

  * After launching _SmartSVN_, select **Open Existing project(s):**
  * Select the **Project Name** you wish update
  * Click **OK**
  * You can now select either a file or a subdirectory and click the green arrow to update your local files from the repository.



# Using SVN at the Command Line, without using SmartSVN client #

If you have SVN command line client installed, you can check out the cfast repository using the command line version of SVN.

You can download the command line client for your platform here:
http://subversion.tigris.org/project_packages.html

Open a terminal/shell session and change to the directory that you want the cfast project folder to be placed within.  NOTE: the distinction between "https" and "http" below.

## Anonymous Checkout ##
If you are not a member of the cfast development team, then type:

`svn co http://cfast.googlecode.com/svn/trunk/cfast/trunk cfast`

## Developer Checkout ##
NOTE: Replace 'my\_name' in the string below with your google account username.  This is the same username that has been given Project Member status in Google Code.

As a member of the CFAST development team with commit privileges, type:

`svn co https://cfast.googlecode.com/svn/trunk/cfast/trunk cfast --username my_name`

You might be prompted for your password, but this is _**NOT** the password for your Google Account_, this is a special Google Code password that you can find through a link under the "Source" tab of the Google Code cfast project site.  It will be a random bunch of numbers and letters and nothing that you can specify. NOTE: the link will not be available unless you are a Project Member or Owner.


Either way, a directory called cfast will appear in the directory where you executed the checkout command (the 'co' part of the string), with the contents of the CFAST repository contained within.

## Updates ##

To update your local copy of the repository, go to the sub-directory that you want to update (cfast in the example above) and type:

`svn update`

NOTE: This could be used to update any of the sub-directories under cfast.  If you change down to a subdirectory, like 'CFAST' and execute the svn update command, only that directory will be updated.

## Change or Commit Log ##

To obtain a log of transactions for that particular sub-directory, type:

`svn log -r N:M > text_file.txt`

Which will record all transactions from SVN revision N to M in the file text\_file.txt
By switching the order of the revision numbers you can sort the log in ascending or descending order by revision number.