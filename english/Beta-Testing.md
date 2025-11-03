## Getting Started as a Joomla Component Builder Beta Tester

### Overview

To help improve the stability and performance of Joomla Component Builder (JCB), the project needs more loyal testers. Beta testers will download, install, and test new beta versions of JCB, then report any issues they find. This document will guide you through the process of becoming a JCB beta tester.

### Steps to become a JCB Beta Tester

1. Join the JCB releases/update channel: https://t.me/jcb_updates
2. Watch for beta releases from the Beta repo and download them.
3. Install the downloaded beta version on a blank Joomla website.
4. Perform a series of tasks and test the new features or changes.
5. Report any issues you find on Gitea: https://git.vdm.dev/joomla/Component-Builder/issues and tag them with the Beta tag.
6. Check for any open issues tagged with Beta before starting your testing.

### How to Test

1. Download the latest release from https://git.vdm.dev/joomla-beta/pkg-component-builder/archive/master.zip
2. Install and test locally
3. Report issues via ticket at https://git.vdm.dev/joomla/Component-Builder/issues

### Change Logs

You can find change logs for each release in the following locations:

- Unofficial Beta channel change log: https://git.vdm.dev/joomla-beta/com-componentbuilder/src/branch/master/CHANGELOG.md
- Official Stable channel change log: https://git.vdm.dev/joomla/Component-Builder/src/branch/staging/CHANGELOG.md

Review the change logs and commit history to understand which features/functions/areas have been updated and require testing.

### Additional Tips and Detailed Steps

1. **Understanding changes:** Keep an eye on the change logs in both the beta channel (https://git.vdm.dev/joomla-beta/com-componentbuilder/src/branch/master/CHANGELOG.md) and the stable channel (https://git.vdm.dev/joomla/Component-Builder/src/branch/staging/CHANGELOG.md). This can help you identify areas that require testing. Also, review the commit history to get a better understanding of the changes made, although this might be overwhelming for non-programmers.

2. **Compiling components:** During the testing process, make sure to compile your components into a git repository. This will allow you to see what has changed and identify any issues. Make it a habit to compile and upload components to git after every update.

3. **Familiarize yourself with JCB's "Powers" feature:** This is an advanced aspect of the platform that can significantly enhance your PHP programming capabilities. As the project evolves, more features will be introduced through Powers, so understanding this aspect is crucial for effective testing.

4. **Actively participate in the JCB updates channel:** Join the JCB updates channel (https://t.me/jcb_updates) and stay up-to-date with the latest beta releases. Engage with the community, share your experiences, and provide valuable feedback to help improve the project.

5. **Using the release checking component:** JCB has a release checking component (https://git.vdm.dev/joomla/com_release_checking) that can be used to mark and provide feedback on the tested features. This component can be installed on a Joomla system linked to Gitea, and accessed using your Gitea account. Utilize this tool to streamline the testing process and make it more efficient.

6. **Collaborate with fellow testers:** Coordinate with other beta testers and share your testing experiences. Create a list of areas that need to be checked for each release and divide the tasks among the testers. This will ensure a comprehensive testing process and help identify potential issues more effectively.

7. **Reporting issues:** If you find any issues during testing, report them at https://git.vdm.dev/joomla/Component-Builder/issues. Make sure to tag the issue with the "Beta" tag and check for existing issues with the same tag before submitting a new one. This will prevent duplicate issue reports and help the development team prioritize their tasks.

This guide assumes you have Git installed on your system. If you don't, please follow the official instructions on how to install Git: [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## How to test the compiler (in the [Octojoom setup](https://git.vdm.dev/octoleo/octojoom)):

### Step 1: Initialize a Git Repository in Your Component's Target Folder (on your production instance)

1. Open your command line interface or terminal.

2. Navigate to the target folder of your component:

```
cd /path/to/your/component/target/folder
```

3. Initialize a Git repository:

```
git init
```

### Step 2: Commit Your Component's Initial State

1. Add all the files in the target folder to the staging area:

```
git add .
```

2. Commit the files with a meaningful message:

```
git commit -m "Initial commit of my component"
```

### Step 3: Copy the Target Folder and Set up the Beta JCB Instance

1. Copy the target folder to a new location that you can delete when you're done:

```
cp -R /path/to/your/component/target/folder /path/to/new/target/folder
```

2. Set up your new blank install of the beta version of JCB to target this new folder.

3. Initialise your repositories in the beta instance and use **Init**/**Reset** to pull the
   component blueprint from source control.

### Step 4: Compile Your Component with the Beta JCB Instance

1. Compile your component.

### Step 5: Review Changes Made by the Beta JCB Instance

1. In the command line interface or terminal, navigate to the new target folder:

```
cd /path/to/new/target/folder
```

2. Check the status of the Git repository:

```
git status
```

3. If there are any changes, add them to the staging area:

```
git add .
```

4. Commit the changes with a message indicating that they were made by the beta JCB instance:

```
git commit -m "Changes made by beta JCB instance"
```

5. To see the differences between the stable JCB instance and the beta JCB instance, use the `git diff` command:

```
git diff HEAD~1
```

This command will show the differences between the current commit (HEAD) and the previous commit (HEAD~1).

6. Review the differences and note any changes that appear to break your Joomla component or that are no longer the same as your stable JCB instance.

### Step 6: Report Any Issues

If you find any issues, report them to the JCB project by opening a new issue and tagging it with the Beta tag: [https://git.vdm.dev/joomla/Component-Builder/issues](https://git.vdm.dev/joomla/Component-Builder/issues)

> Remember that thorough testing is crucial to the project's success. The more active and committed testers we have, the more effectively JCB can evolve and improve.
> Happy testing!