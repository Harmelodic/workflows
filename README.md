# workflows

GitHub Action workflows for shipping software.

[GitHub Action documentation](https://docs.github.com/en/actions).

## Types of workflows

3 types of workflows:

- [Verify](https://en.wikipedia.org/wiki/Verification_and_validation#Verification): Workflows used to verify a project
  is correct.
- Build: Workflows used to build software artifacts.
- Release: Workflows used to release software.

Typically, one of the following shipping processes will be implemented:

- Pull request will verify. Merging to a release branch will build. Tagging a commit on a release branch will release.
- Pull request will verify and build. Merging to a release branch will release.
- Pull request will verify. Merging to a release branch will build and release.
- Pull request will verify. Merging to a release branch will directly release (when no build is necessary).
- Pull request will verify. Tagging a commit on a release branch will release (when no build is necessary).

A release branch could just be `main`. If a [tip and tail development model](https://openjdk.org/jeps/14) is in use then
the tip is a release branch and all tails are release branches.
