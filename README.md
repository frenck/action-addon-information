# 🚀 Frenck's Github Action: Home Assistant Add-on Information

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
![Project Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE.md)

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

🚀 Frenck's GitHub Action for gathering information from an Home Assistant
Add-on.

## About

This GitHub Action is able to extract information from a Home Assistant Add-on,
for use in other GitHub Actions.

It contains information like name, slug, architectures, and a lot more.

## Usage

```yaml
jobs:
  information:
    name: Gather add-on information
    runs-on: ubuntu-latest
    outputs:
      name: ${{ steps.information.outputs.name }}
      description: ${{ steps.information.output.description }}
      architectures: ${{ steps.information.outputs.architectures }}
    steps:
      - name: ⤵️ Check out code from GitHub
        uses: actions/checkout@v2
      - name: 🚀 Run add-on information
        id: information
        uses: frenck/action-addon-information@v1
```

## Arguments

| Input  |                        Description                         |    Usage     |
| :----: | :--------------------------------------------------------: | :----------: |
| `path` | Path to the folder containing the add-on config.json file. | **Optional** |

## Specifying an add-on location

By default, the Action will try to find the add-on in the repository. However,
if you have multiple add-on in a single repository, this can become a problem.

Using the `path` argument, you can point the Action towards the specific add-on
you'd like to get information from.

```yaml
- name: 🚀 Run Home Assistant Add-on Information
  id: information
  uses: frenck/action-addon-information@v1
  with:
    path: "./addon"
```

## Outputs

The Action provides the following information as output:

|     Output      |                        Description                        |
| :-------------: | :-------------------------------------------------------: |
|    `aarch64`    | Boolean if the add-on support the `aarch64` architecture. |
|     `amd64`     |  Boolean if the add-on support the `amd64` architecture.  |
| `architectures` |      List of supported architectures by this add-on.      |
|     `armhf`     |  Boolean if the add-on support the `armhf` architecture.  |
|     `build`     |    File location of the build.json configuration file.    |
|    `config`     |  File location of the add-on config.json configuration.   |
|  `description`  |                Description of the add-on.                 |
|     `i386`      |  Boolean if the add-on support the `i386` architecture.   |
|     `name`      |                  The name of the add-on.                  |
|     `slug`      |                The configured add-on slug.                |
|    `target`     |                 The add-on target folder.                 |
|     `image`     |             The Image-template of the add-on.             |
|    `version`    |                 The version of the addon.                 |

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Versions & Updating

You can specify which version of this GitHub Action your workflow should use.
And even allowing for using the latest major or minor version.

For example; this will use release `v1.1.1` of a GitHub Action:

```yaml
- name: 🚀 Run Home Assistant Add-on Information
  uses: frenck/action-addon-information@v1.1.1
```

While the following example, will use the `v1.1.x` minor release, for example
if `v1.1.2` is the latest releases (starting with `v1.1`), this will run
`v1.1.2`:

```yaml
- name: 🚀 Run Home Assistant Add-on Information
  uses: frenck/action-addon-information@v1.1
```

As in the examples throughout the documentation, the following example is
locked on major version, meaning any `v1.x.x` latest version will be used,
as long as it is version 1.

```yaml
- name: 🚀 Run Home Assistant Add-on Information
  uses: frenck/action-addon-information@v1
```

### Automatically update using Dependabot

The advantage of locking against a more specific version, is that it prevents
surprises if an issue or breaking changes were introduced in a newer release.

The disadvantage of being more specific, is that it requires you to keep things
up to date. Fortunately, GitHub has a tool for that, called: Dependabot.

Dependabot can automatically open a pull request on your repository to update
this Action for you. You can instantly see if the new version works (as the
pull request shows the success or failure status) and you can decide to
merge it in by hitting the merge button. Quick, easy and always up2date.

To enable Dependabot, create a file called `.github/dependabot.yaml`:

```yaml
version: 2
updates:
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: daily
```

Your all set! Dependabot will now check (and update) your GitHub actions
every day. 🤩

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We've set up a separate document for our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2021 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[contributors]: https://github.com/frenck/action-addon-information/graphs/contributors
[frenck]: https://github.com/frenck
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[license-shield]: https://img.shields.io/github/license/frenck/action-addon-information.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2021.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[releases-shield]: https://img.shields.io/github/release/frenck/action-addon-information.svg
[releases]: https://github.com/frenck/action-addon-information/releases
[semver]: http://semver.org/spec/v2.0.0.html
