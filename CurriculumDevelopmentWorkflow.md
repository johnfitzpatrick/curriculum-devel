#Review and Publish Workflow

All Curriculum Development is moving to GitHub under https://github.com/learnchef

The actual repos will be
- https://github.com/learnchef/chef-fundamentals-windows
- https://github.com/learnchef/chef-fundamentals-linux
- https://github.com/learnchef/chef-intermediate

##Reviewing & Feedback

There are two basic means of supplying feedback and/or updating the materials:

- Open a GitHub Issue

> When you discover a typo, inconsistency, or an error with the content

- Submit a Pull Request

> When you have fixed a typo, inconsistency, or error with the content.

###GitHub Issue Process

If you have a number of issues/typos/suggestions on specific slides, then you can browse to the curriculum's repo and submit these via a GitHub Issue.

* Include the version (e.g. v2.1.5) or commit SHA (e.g. 89f3ad132bf575a85973935d3e88ae66c10fcd67)

* Include a picture of the slide or handout page (Issues allow you to drag-and-drop images) and information that identifies the slide or page (e.g. slide/page title, slide/page number)

* For each item, within the issue, use Github markdown's bullet list. This renders each item with a checkbox which is useful to track completion.

```
* [ ] "distribute" is spelled as "distrbute" on the *Course Objectives* (slide 5)
* [ ] Before running `knife node run_list add node1 recipe[apache]` the user needs to run `knife cookbook upload apache` (handout pg 4)
```

###Pull Request Process

It's awesome that you want to make actual changes to the materials. A lot of the materials are binary files. Git merges binary files by simply overwriting the existing file. So merging pull requests require a little more care and attention.

1.  First contact John Fitzpatrick or Nathen Harvey and get invited in as a contributor on the project repo on GitHub.

2.  Contact `@johnfitzpatrick` to ensure there will be no treading on toes and no other edits are imminent while you're making your changes (as binary files cannot be merged)

3.  Then clone the relevant repo and create a new branch
 ```
 $ git clone https://github.com/learnchef/classname
 $ git checkout -b newbranchname
 ```

 __Note__: Always submit PRs from a custom branch to the master branch.

4. Make the changes to the materials on this new branch

5. Update `ReleaseNotes.md` with a list of your changes

6. Add and commit your changes
 ```
 $ git add .
 $ git commit
 ```

7. Enter a list of the changes you've made in your commit message
 ```
     - slide 1 fixed the email address
     - slide 4 changes the footer
     - slide 10 fixed a typo
     etc

     # Please enter the commit message for your changes. Lines starting
     # with '#' will be ignored, and an empty message aborts the commit.
     # On branch john/supermarket_image_update
     # Changes to be committed:
     #       new file:   Chef-Fundamentals.pptx
 ```

 You can always edit your commit message before you do a `git push` by

 ```
 $ git commit --amend
 ```

 __Note__ If screw up and want to reset your git add/commit, then you can

 ```
 $ git reset HEAD~1
 ```

8. Push the new branch to GitHub
```
$ git push origin newbranchname
```

 __Note__: Always issue pull requests off the latest master branch.

9.  Navigate to https://github.com/learnchef/classname and create a new Pull Request

10. Do not merge the pull requests - curriculum development will verify the changes and merge it.

11. If you like you can open a GitHub issue outlining changes, then while making the changes no changes will be done on master. Always include `@johnfitzpatrick` to alert me of the changes.


##Publishing Materials

Once edits have been updated, and the final version updated to GitHub, it will be tagged with the release number.  This tagged verion will be published to Box.net.

All published materials can be found in box.net under the following locations

- Training Materials > Courses > 2 Day Fundamentals
http://bit.ly/chef_fundamentals_materials

- Training Materials > Courses > Chef Intermediate
http://bit.ly/Chef-Intermediate-materials

- Training Materials > Externally Shared

Once a new version is released, the old version will not be deleted for a couple of weeks.

To publish materials:

1. Move to the master branch & merge your branch
 ```
 $ git checkout master
 $ git pull origin master
 $ git merge newbranchname
 $ git commit -m "merged branch 'newbranchname'"
 $ git push origin master
 ```

2. Run the following command with the appropriate version number
 ```
 $ git tag -a v2.1.5 -m 'Classname v2.1.5'
 $ git push origin Classname-v2.1.5
 ```
 e.g.
 ```
 $ git tag -a v2.0.1 -m 'Chef Fundamentals Windows v2.0.1'
 $ git push origin Chef-Fundamentals-Windows_v2.0.1
 ```
 GitHub refers to a tagged version as a 'Release' and creates a `classname.zip` and `classname.tar.gz` of the repo contents.

 > Note: The zip file for the release will contain the name of the repo, so no need to include the class in the tag. E.g., if the repo was called 'chefclass', and you tagged the release `git tag -a ChefClass-v2.0.1`, then the downloaded file would be  `chefclass-ChefClass-v2.0.1`


3. Click on the 'Releases' tab on the GitHub repo

4. Click on the `zip` icon to download `classname.zip` to your local directory

5. Upload `classname.zip` to the appropriate location in box.net.
