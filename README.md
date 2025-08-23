# workflows

GitHub Actions workflows
for [shipping software](https://harmelodic.com/software-engineering/philosophy-and-practices/development/shipping-software/).

[GitHub Actions documentation](https://docs.github.com/en/actions).

## Types of workflows

There are 3 types of workflows each with their own purpose:

- Build: Workflows used to build software artifacts.
- Release: Workflows used to release software.
- Verify: Workflows used to verify a project is correct.

Verify workflows are the same or very similar to Build workflows, but they don't produce a releasable artifact. This is
useful for some shipping strategies where Pull Requests should not build and push a releasable artifact due to (e.g.)
security concerns.

## Example shipping strategies

Different shipping strategies are possible, depending on the project's requirements. Below are listed some example
strategies, where a release branch could just be `main`. If
a [tip and tail development model](https://openjdk.org/jeps/14) is in use then the tip is a release branch and all tails
are release branches:

- Pull request will build. Merging to a release branch will release an artifact (artifact promotion). A separate
  deployment system with release a deployment of the artifact.
    - e.g. Web services
- Pull request will verify. Merging to a release branch will build and release an artifact. A separate deployment system
  with release a deployment of the artifact.
    - e.g. Web services, where Pull Request should not auto-build releasable artifacts.
- Pull request will build. Merging to a release branch will release
    - e.g. Libraries with automatic releasing on merge.
- Pull request will verify. Merging to a release branch will build. Tagging a commit on a release branch will release.
    - e.g. Libraries with releasing on tag.
- Pull request will verify. Merging to a release branch will build and release.
    - e.g. Libraries with automatic releasing on merge, where Pull Request should not auto-build releasable artifacts.
- Pull request will verify. Merging to a release branch will directly release (when no build is necessary).
    - e.g. Scripts / Infrastructure as code, where no artifact is made but instead code is directly executed.
- Pull request will verify. Tagging a commit on a release branch will release (when no build is necessary).
    - e.g. Policy / Infrastructure as code, where the code repository is the artifact and needs semantically releasing.
