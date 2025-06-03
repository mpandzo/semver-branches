# semver-branches

Semantic versioning of package.json across branches via github actions

# usage

The Github workflow in .github/workflows performs the following tasks:

- Runs on `push` to develop or master branches.
- Clones the repo to the workflow runner.
- Uses mathieudutour/github-tag-action to analyze recent commits and generate a new semver tag (e.g., 0.0.2-develop.0, 0.0.2).
- Pushes the new tag to the repo.
- Updates package.json version field with new version. If on master, removes any suffix (e.g., turn 0.0.2-feature.x into 0.0.2).
- Commits the updated package.json with the new version.
- Pushes the commit to the current branch.
- Uses the new tag to create a GitHub release for master branch only.

# prerequisites

In order to utilize this workflow you must use at least the `develop` and `master` branches. In addition, you must allow your github action (via GITHUB_TOKEN) to both read and write to your repo. To do so, simply do the following in Settings -> Actions:

