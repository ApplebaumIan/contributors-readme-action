[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<br />

<p align="center">
    <h2 align="center">Contributors-Readme-Action</h3>
</p>

Contributors-Readme-Action is a simple GitHub action to automate contributors list in README file. Not only contributors, collborators, bots or any user.

As it uses a GitHub action it's secure and very easy to integrate into your projects. Once added it will automatically add all the repository contributors to your readme in a well-formatted table, including future contributors :smile:. Now why would you need a contributors list? Come on man, show some love to the ones who contribute to your project.:wink:

The contributors list is fetched from [GitHub API](https://developer.github.com/v3/repos/statistics/).

## Getting Started

### First Step

If you're new to actions, add these to your `.github/workflows/main.yml` file. If this file does not exist, create one.

```yml
on:
    push:
        branches:
            - main

jobs:
    contrib-readme-job:
        runs-on: ubuntu-latest
        name: A job to automate contrib in readme
        steps:
            - name: Contribute List
              uses: akhilmhdh/contributors-readme-action@v2.3.6
              env:
                  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

That's it!

To add it to your to your existing workflow, append this to your current `.yml` workflow script.

```yml
- uses: akhilmhdh/contributors-readme-action@v2.3.6
  env:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Second Step

1. Add a `README.md` file
2. Add the below comment inside your `README.md` where you want it to appear.

```md
<!-- readme: contributors -start -->
<!-- readme: contributors -end -->
```

3. Save it, wait for the action to complete and tadaa :smile:

### But wait!!!

-   What if you wanted to add direct collaborators of a project, no worries

```md
## Collaborators

<!-- readme: collaborators -start -->
<!-- readme: collaborators -end -->

## Contributors

<!-- readme: contributors -start -->
<!-- readme: contributors -end -->
```

-   Now you decided that you want to join this into one list, no issue

```md
## Contributors

<!-- readme: collaborators,contributors -start -->
<!-- readme: collaborators,contributors -end -->
```

-   Then you decided to add some github users who are important figure in this project

```md
## Contributors

<!-- readme: <username1>,collaborators,<username2>,contributors -start -->
<!-- readme: <username1>,collaborators,<username3>,contributors -end -->
```

> The order of the list will be given priority. So username1 will appear first collaborators then username2 likewise.(No brackets for usernames)

> The subject inside start and end must be same.

### Keywords

| keywords      | Definition                                       |
| ------------- | ------------------------------------------------ |
| contributors  | contributors of the repo                         |
| collaborators | collaborators of the repo                        |
| sponsors      | sponsors of the repo's user/organization         |
| bots          | bots of the repo                                 |
| username      | any username that you want to add on to the list |

-   [An example of this action can be found here](./contributors.md)

### Operators

Operators are in a nutshell simple modifiers that can be applied to a list like removing a person from a list. They can be applied accordingly to a keyword like `akhilmhdh/-` with a / as seperator.

| operator | Definition                    | Example     |
| -------- | ----------------------------- | ----------- |
| /-       | remove the username from list | akhilmhdh/- |

### Optional parameters

You can add these optional parameters in your action script to modify the appearance of the resulting list.

```yml
- name: Contribute List
  uses: akhilmhdh/contributors-readme-action@v2.3.6
  with:
      image_size: 100
```

| Option                        | Default Value                                               | Description                                                     | Required |
| ----------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------- | -------- |
| image_size                    | 100(px)                                                     | Size of square images in the stack                              | false    |
| readme_path                   | README.md                                                   | Path of the readme file you want to update                      | false    |
| use_username                  | false                                                       | To use username instead of full name                            | false    |
| columns_per_row               | 6                                                           | Number of columns in a row                                      | false    |
| collaborators                 | direct                                                      | Type of collaborators options: all/direct/outside               | false    |
| commit_message                | docs(contributor): contrib-readme-action has updated readme | Commit message of the github action                             | false    |
| committer_username            | ""                                                          | Username on commit                                              | false    |
| committer_email               | ""                                                          | Email id of committer                                           | false    |
| pr_title_on_protected         | docs(contributor): contributors readme action update        | Title of the PR that will be created if the branch is protected | false    |
| auto_detect_branch_protection | true                                                        | To override auto protected branch detection                     | false    |

> committer_username and committer_email both must be provided to use as a replacement to GH action committer

> The action will update Readme as PR when the branch is protected, else it will directly commit it.
> But if your branch is protected and you passed personal access token to avoid PR mode by trusting the action, you could set auto_detect_branch_protection to false

### Outputs

Following outputs are generated on the execution of this action.

| Output | Value  | Description                                                  |
| ------ | ------ | ------------------------------------------------------------ |
| pr_id  | string | Id of the generated PR when the branch is in protected mode. |

## Contributing

Please see [CONTRIBUTING.md](/CONTRIBUTING.md) for getting started with the contribution.

Make sure that you follow [CODE_OF_CONDUCT.md](/CODE_OF_CONDUCT.md) while contributing and engaging in the discussions.

**When contributing, please first discuss the change you wish to make via an issue on this repository before making the actual change**.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

-   [all-contributors-bot](https://github.com/all-contributors/all-contributors): Inspiration for this project
-   [image-shield](https://shields.io/): For the cool badges

[contributors-shield]: https://img.shields.io/github/contributors/akhilmhdh/contributors-readme-action.svg?style=for-the-badge
[contributors-url]: https://github.com/akhilmhdh/contributors-readme-action/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/akhilmhdh/contributors-readme-action.svg?style=for-the-badge
[forks-url]: https://github.com/akhilmhdh/contributors-readme-action/network/members
[stars-shield]: https://img.shields.io/github/stars/akhilmhdh/contributors-readme-action?style=for-the-badge
[stars-url]: https://github.com/akhilmhdh/contributors-readme-action/stargazers
[issues-shield]: https://img.shields.io/github/issues/akhilmhdh/contributors-readme-action.svg?style=for-the-badge
[issues-url]: https://github.com/akhilmhdh/contributors-readme-action/issues
[license-shield]: https://img.shields.io/github/license/akhilmhdh/contributors-readme-action.svg?style=for-the-badge
[license-url]: https://github.com/akhilmhdh/contributors-readme-action/blob/master/LICENSE.txt
