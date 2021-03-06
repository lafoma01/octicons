# Octicons Contribution Guidelines

Thank you for your interest in contributing to Octicons! We are currently only accepting submissions from GitHub staff and only include icons that are used in the GitHub UI.

## Adding or updating an icon

Follow these steps to add or update an icon.

### 1. Clone the repository

```shell
# Clone the repository
git clone https://github.com/primer/octicons

# Navigate to the newly cloned directory
cd octicons
```

If you don't have [`write`](https://help.github.com/en/github/getting-started-with-github/access-permissions-on-github) access to the [primer/octicons](https://github.com/primer/octicons) repository, instead of cloning the repository directly, you'll need to [fork](http://help.github.com/fork-a-repo/) the project, clone your fork, and configure the remotes:

```shell
# Clone your fork of the repository
git clone https://github.com/<your-username>/octicons

# Navigate to the newly cloned directory
cd octicons

# Assign the original repo to a remote called "upstream"
git remote add upstream https://github.com/primer/octicons
```

### 2. Create a new feature branch

```shell
git checkout -b <branch-name>
```

### 3. Add or update SVG files in the `/icons` directory

### 4. Add or update keywords in `keywords.json`

```diff
{
  "mark-github": ["octocat", "brand", "github", "logo"],
+ "your-icon": ["foo", "bar"]
}
```

### 5. Commit and push changes

```shell
git add .
git commit -m <message>
git push
```

### 6. Create a pull request

Use GitHub to [create a pull request](https://help.github.com/en/desktop/contributing-to-projects/creating-a-pull-request) for your branch. In your pull request description, be sure to mention where the icon will be used and any relevant timeline information.

If everything looks good, a maintainer will approve and merge the pull request when appropriate. After the pull request is merged, your icon will be available in the next Octicons release.

## Releasing changes 

Once submitted changes have been agreed upon, these instructions will guide maintainers through releasing changes.

### 1. Create a release branch in the [primer/octicons](https://github.com/primer/octicons) repository.

```shell
git checkout -b release-x.y.z
```

In the context of Octicons, the version number is updated as follows:

- Breaking changes to the library or workflow, renaming or removing an icon would all be considered a **major update**. 
- Adding a new icon would be considered a **minor update**.
- Fixing an icon would be considered a **patch**.

Reach out in the #design-systems Slack channel if you're unsure.

### 2. Update the [CHANGELOG](https://github.com/primer/octicons/blob/master/CHANGELOG.md) describing the changes in this release.

When adding changes, be sure to provide a link to any of the relevant PRs merged into the release. 

### 3. Update the version in code base

Find and replace the version number of the current release with the version number of the new release. Exclude anything that does relate directly to the Octicons version. Examples of excluded items include `yargs-parser` and `testing-library_react`.

### 4. Create a release PR

When creating the release PR, include the changes written in the CHANGELOG in the description. We advise changing any bulleted item into a checkbox item. After each update is merged into the release PR, check each item as complete.

### 5. Tag release branch

Pull down any changes from release branch onto your local machine and tag your release with the new version number by running:

```shell
git tag vx.y.z
```
**Example:**

```shell
git tag v10.1.0
```

After the release branch has been tagged, push the tag back to the origin.

```shell
git push --tags
```

### 6. Merge
When all of the checks have passed and the release PR has been approved, merge the new release to the main branch.

### 7. Draft new release
- On the **Code** tab, click **Releases** in the repo sidebar.
- Click **Draft a new release**.
- Select the tag with the new version number tag set in step 5.
- Title the release with the new version number and paste in the changes that were added to the CHANGELOG.
- Click **Publish release**.

**Example:**

![image](https://user-images.githubusercontent.com/10384315/91103190-c6171e80-e61f-11ea-8396-7138996cff30.png)


🎉 Congratulations! The new release has been published.


