# Commit and Push action

[![Action test on Ubuntu](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/ubuntu_action_test.yml/badge.svg)](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/ubuntu_action_test.yml) [![Action test on MacOS](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/macos_action_test.yml/badge.svg)](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/macos_action_test.yml) [![Action test on Windows](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/windows_action_test.yml/badge.svg)](https://github.com/GuillaumeFalourd/git-commit-push/actions/workflows/windows_action_test.yml)

GitHub Action to commit & push changes made in workflows :octocat:

<img width="1253" alt="Screenshot 2021-10-21 at 15 40 50" src="https://user-images.githubusercontent.com/22433243/138337505-49e66480-e084-4611-99f3-594023eab19c.png">

_**Note**: This action is supported on **all runners** operating systems (`ubuntu`, `macos`, `windows`)_

* * *

## 📚 Usage

### ⚠️ Requirements

- The [`actions/checkout`](https://github.com/marketplace/actions/checkout) is mandatory to use this action, as it will be necessary to access the repository files.

### `1️⃣ Minimal`: Commit and Push with `default` parameters

```yaml
    steps:
      - uses: actions/checkout@v2.3.4
      # [...] --> steps with actions or commands updating repository files
      - uses: GuillaumeFalourd/git-commit-push@v1
```

### `2️⃣ Full`: Commit and Push with `customized` parameters

```yaml
    steps:
      - uses: actions/checkout@v2.3.4
      # [...] --> steps with actions or commands updating repository files
      - uses: GuillaumeFalourd/git-commit-push@v1
        with:
          email: ${{ github.actor }}@users.noreply.github.com
          name: ${{ github.actor }}
          commit_message: your_message
          target_branch: target_branch_name
          files: file1 file2 directory1 directory2/file3
          remote_repository: https://github.com/owner/another_repository
          access_token: ${{ github.token }}
          force: true
          empty: true
          tags: true
```

* * *

## ▶️ Action Inputs

Field | Mandatory | Default Value | Observation
------------ | ------------  | ------------- | -------------
**email** | NO | `${{ github.actor }}@users.noreply.github.com` | Github user email <br/> _e.g: `octocat@github.com`_
**name** | NO | `${{ github.actor }}` | Github username <br/> _e.g: `octocat`_
**commit_message** | NO | `Commit performed using Push and Commit action` | Commit message
**target_branch** | NO | `${{ github.ref }}` | Branch to push the changes back
**files** | NO | `.` | Files to add separated by space <br/> _e.g: `file1 file2 directory1 directory2/file3`_
**remote_repository** | NO | `origin` | Repository url to push the code
**access_token** | NO | `${{ github.token }}` | [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) is necessary if push to another repository
**force** | NO | `0` | Whether to perform force push
**empty** | NO | `0` | Whether to allow empty commit
**tags** | NO | `0` | Whether to use --tags

* * *

## 🤝 Contributing

☞ [Guidelines](https://github.com/GuillaumeFalourd/git-commit-push/blob/main/CONTRIBUTING.md)

## 🏅 Licensed

☞ This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/git-commit-push/blob/main/LICENSE)
