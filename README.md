# Github Mirroring with CircleCI

[![CircleCI](https://circleci.com/gh/nicksantamaria/git-mirroring-circleci.svg?style=svg)](https://circleci.com/gh/nicksantamaria/git-mirroring-circleci)

This project is an example of how to use CircleCI to automatically mirror a Github repository to another remote.

## Usage

1. Copy the `circle.yml` file from this project into your repository root.
2. Change the `GIT_MIRROR_URL` variable to the destination git remote URL.
3. Commit the file to your repo and push to github.

## Dogfooding

To demonstrate this approach, this project uses CircleCI to mirror the repo to [Bitbucket](https://bitbucket.org/nicksantamaria/git-mirroring-circleci). The CircleCI build history can be viewed here - https://circleci.com/gh/nicksantamaria/git-mirroring-circleci
