Git
==================================

`Visualizationlab Github page
<https://github.com/visualisationlab>`_


Git LFS
----------------------------------

What to do with BIG files in Github?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
GitHub doesn’t like big files and will reject anything above 100MB. Git provides a solution in Git Large File Storage (or Git LFS), GitHub also hosts its own version of Git LFS. However we decided to host our own implementation of Git LFS at the Visualisation Lab.

When to use it?
"""""""""""""""
Try to avoid uploading too many big files to the GitHub repository as it makes working with the repository difficult and slow. What files should or should not be added to Git LFS is on your own accord. In general, I would try to move any non-text assets that can – on their own – be above 5MB into Git LFS. In the case of – for instance – audio assets, If it’s just sound effects, I would keep them in the GitHub repository but if it involves a lot of music files, I would move all audio files into Git LFS.

For more information check: https://git-lfs.github.com/

How to use git LFS in a new repository?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
In your repository make a file called .lfsconfig

Add the following text:
::

    [lfs]
        url = “http://visualisationlab.science.uva.nl:8087/”

The next step is to ask the admin of the visualisation lab for a git LFS account.
Mail: j.g.vanderkaaij[at]uva.nl

Make sure you have downloaded and installed the standard Git command line extension. After that, set up Git LFS for your user account by running:
::
    git lfs install

You only need to run this once per user account.

In each Git repository where you want to use Git LFS, select the file types you’d like Git LFS to manage (or directly edit your .gitattributes). You can configure additional file extensions at any time. In this example, I’m tracking PSD files.
::
    git lfs track “*.psd”

Now make sure .gitattributes is tracked:
::
    git add .gitattributes

Note that defining the file types in Git LFS will not convert any pre-existing files to Git LFS. Files on other branches or in your prior commit history will remain in your existing git repository. To migrate those files use the Git LFS migrate command, which has a range of options designed to suit various potential use cases. See below for more information.

There is no step three. Just commit and push to GitHub as you normally would; for instance, if your current branch is named main:
::
    git add file.psd
    git commit -m “Add design file”
    git push origin main

All the PSD files in your repository will now be stored in our own Git LFS and your normal repository will only keep a lightweight reference to that file keeping your GitHub repository a lot leaner.

How to use git LFS in an existing repository?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Clone the existing repository.
Ask the admin for an account on the LFS server.
Mail: j.g.vanderkaaij[at]uva.nl

Run:
::
    git lfs fetch –all

How to Migrate existing files in your repository over to Git LFS?

Git LFS Migrate:
::
    git lfs migrate import –include=”*.mp4″

This will not garbage collect your original git repository, that still needs to happen:

https://stackoverflow.com/questions/51782043/what-does-git-lfs-migrate-do

“The only problem is that the original git-objects of the binary files are still in the .git folder because you didn’t garbage-collected them.”

You should follow the git lfs migration tutorial which explains:

The above successfully converts pre-existing git objects to lfs objects. However, the regular objects still persist in the .git directory. These will be cleaned up eventually by git, but to clean them up right away, run:
::
    git reflog expire –expire-unreachable=now –all
    git gc –prune=now

After running that your .git should be the same size, but if you go into it you should see that objects should be much smaller than before the migrations and that LFS holds the migrated files.

When other developers/applications clone the repo, the large files in the git history will be ignored.