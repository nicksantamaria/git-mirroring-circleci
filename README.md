# Github Mirroring with CircleCI

[![CircleCI](https://circleci.com/gh/nicksantamaria/git-mirroring-circleci.svg?style=svg)](https://circleci.com/gh/nicksantamaria/git-mirroring-circleci)

This project is an example of how to use CircleCI to automatically mirror a Github repository to another remote. CircleCI offers a [free-tier](https://circleci.com/pricing/) which is sufficient for this use-case.

## Usage

### Repository Setup

1. Copy [circle.yml](circle.yml) from this project into your repository root.
2. Change the `GIT_MIRROR_URL` variable to the destination git remote URL.
3. Commit the file to your repo and push to github.

### CircleCI Setup

1. Sign in to CircleCI, authorize it to access Github if asked.
2. Go to "Add Projects" in the sidebar.
3. Choose your Github user or organsation which owns the repo.
4. Click the "Build project" button for the repo.

This first build will likely fail as there is no authentication credentials set up yet - see the next section.

### Authentication Setup

This example will only cover SSH key authentication. 

1. Generate a new SSH key, eg `ssh-keygen -t rsa -C "reponame-mirror" -f ./reponame-id_rsa`
2. Go to the CircleCI dashboard, hover over the repository, and click on the cog icon.
3. Go to the "SSH Permissions" tab.
4. Copy the newly created private key and paste into the "Private key" field, eg `pbcopy < ./reponame-id_rsa`
5. Set the "Hostname" field to the hostname of the destination git remote.
6. Copy the newly created SSH public key, eg `pbcopy < ./reponame-id_rsa.pub`
7. Add this public key to the destination remote. This process will depend on the system which manages the destination repository. For example:
   - A deploy key with write access to the destination project (ie, another github repo).
   - A ssh key for a specific user with write permission to the repo (ie, bitbucket as they dont have write access for deploy keys)
   - An entry in `~/.ssh/authorized_keys` for custom git setups.
8. Return to the CircleCI project, find the previously failed build and click "rebuild".

At this point you should have a working system!

## Dogfooding

To demonstrate this approach, this project uses CircleCI to mirror the [GitHub](https://github.com/nicksantamaria/git-mirroring-circleci) repo to [Bitbucket](https://bitbucket.org/nicksantamaria/git-mirroring-circleci). The CircleCI build history can be viewed here - https://circleci.com/gh/nicksantamaria/git-mirroring-circleci
