# Application Deployment Workflow

## Install from FloWide-Apps

The FloWide Workbench comes with a pre-installed *FloWide App Installer* to install apps from the *FloWide-Apps* github organization. Without any github token supplied one can install public apps only, otherwise the corresponding private apps will be also available.

### Installation process
- Exactly one remote release can be installed.
- If the release requires configuration ('**-uc**' in git tag, has *install.py*), the git tag will not be saved to workbench and no release will be created.
- If the release does not require configuration (normal git tag, has not *install.py*), the git tag will also be saved to workbench, which means that a local release will be also created.

### Remarks
- Cannot handle more releases at once: if a release is already installed and an other needed, one should remove the app and reinstall it.
- If not the recent release was selected to install, the *update* button may appear immediately at the application, this is normal behavior.

## Configure FloWide apps

Some apps need configuration before use, these have an *install.py* in the repository. To make the configuration, this file should be run in edit mode.

### What does install.py do?
It checks extra requirements of the app (e.g. a docker container is installed?) and tries to fulfill them anyway. It asks for user input to create configuration, saves it to a file (from which the main app will read it), and creates a release with it from the last committed version if user wants it. The release is a floating commit (not the part of any branches) with a tag. The tag format is currently '**cfg-#**', hashtag stands for a number.

Procedure of creating a floating commit with tag:
- check for changes in repo, stash it if any
- detect current branch
- if the current branch is the *config* branch: STOP (it will be too complicated to solve this problem automatically) 
- if the *config* branch is already exists (e.g. former aborted installation): delete it
- create and checkout *config* branch
- save configuration to file
- remove configuration file from *.gitignore* (to make it committable)
- commit changes (configuration file)
- create tag (detect available tags to determine the name of the new, whose number will be the former +1)
- checkout the original branch
- delete *config* branch, this leaves the recent commit floating with its tag
- if something has been stashed: restore it
- re-create the same configuration file (may be deleted when checkout back)
- add configuration file to *.gitignore* (it should not be part of working branch)

If release is also needed:
- ScriptHandler API: query repos
- get ID of the current repo by remote URL
- ScriptHandler API: execute push with tags using the ID, this makes all things be pushed to gitlab
- (after these the gitlab hook creates a ScriptHandler release object from the pushed tag) 

### Remarks
- If one wants to modify *install.py*, it should be committed before running it. This is necessary because it manipulates the local repository by stashing changes, so the *install.py* file will also be modified during the process if it contains uncommitted changes. Streamlit detects a file update, this causes erroneous execution of the script.

## Put apps to FloWide-Apps

This is not an option for normal users, just for FloWide employees. It should be done manually.

### Instructions
- Do not push floating commits with tags to github.
- Apps with separate config (*install.py*) should be pushed without the actual configuration, tagged with an '**-uc**' postfix. This indicates for the Script Handler that it should not generate a local release from this version directly.
- Apps without separate config (no *install.py*) should be pushed with a normal tag.

### Step-by-step guide to push an app with separate config to github
- TBD
