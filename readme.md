branch-labeler
---

This repository contains a GitHub Action workflow for automatically labeling pull requests based on branch names. It is designed to streamline the process of managing labels for pull requests.

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Getting Started](#getting-started)
- [Usage](#usage)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Getting Started
---
To use this workflow, include the `the9ball/branch-labeler/.github/workflows/branch-labeler.yaml@v0.1.0` workflow in your repository.

```yaml
on:
  pull_request:
    types:
      - opened
      - reopened
      - edited # for base branch change

jobs:
  call:
    uses: the9ball/branch-labeler/.github/workflows/branch-labeler.yaml@v0.1.0
    permissions:
      contents: write # for creating label
      pull-requests: write
    with:
      branch_name_filter: "(feature|release)/.*"
```

Usage
---

```yaml
on:
  pull_request:
    types:
      - opened
      - reopened
      - edited # for base branch change

jobs:
  call:
    uses: the9ball/branch-labeler/.github/workflows/branch-labeler.yaml@v0.1.0
    permissions:
      contents: write # for creating label
      pull-requests: write
    with:
      # Regular expression representing the branch name.
      # Compliant with Bash syntax.
      branch_name_filter: "(feature|release)/.*"

      # GitHub token.
      # Basically, no need to specify.
      # Default: ${{ github.token }}
      token: ''

      # Specify the prefix/suffix of the label to be created.
      label_prefix: ''
      label_suffix: ''
```

License
---
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
