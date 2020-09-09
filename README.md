<div align="center">

# BLC Action

</div>

## Table of Contents

- [About the Project](#-about)
- [Getting Started](#🚀-getting-started)
  - [Optional Parameters](#optional-parameters)
  - [Test](#test)
- [Contributing](#🤝-contributing)
- [License](#📝-license)
- [Credits](#🙏-credits)

## 📄 About

This is a fork of https://github.com/celinekurpershoek/link-checker

This action uses: https://github.com/stevenvachon/broken-link-checker

Find broken links in your website.

## 🚀 Getting Started

Create a new file in your repository .github/workflows/action.yml.

Copy-paste the following workflow in your action.yml file:

```yml
name: Broken link check
on: [push]

jobs:
  broken_link_checker_job:
    runs-on: ubuntu-latest
    name: Check for broken links
    steps:
    - name: Check for broken links
      id: link-report
      uses: ocular-d/blc-action@v0.0.1
      with:
        # Required:
        url: 'https://...'
        # optional:
        honorRobotExclusions: false
        ignorePatterns: 'github,google'
        recursiveLinks: false # Check all urls on all reachable pages (could take a while)
    - name: Get the result
      run: echo "${{steps.link-report.outputs.result}}"
```

### Optional Parameters

`honorRobotExclusions`

Type: `Boolean`
Default value: `true`
The script does not scan pages that search engine crawlers would not follow.
https://github.com/stevenvachon/broken-link-checker#honorrobotexclusions

`ignorePatterns`

type: `String`
Default value: `''`
A comma separated string of matched urls to ignore. Check documentation about patterns here: https://github.com/stevenvachon/broken-link-checker#excludedkeywords

`recursiveLinks`

type: `Boolean`
Default value: `false`
A boolean to do a site-wide check, it will add the `blc` `-ro` param to the command

## Test
There is a broken link in this document as a test:
[A broken link](http://jhgfdsadfghjklkjhgfdsasdfgh.com)

## 🤝 Contributing

We are a community effort, and everybody is most welcome to participate!

Be it filing bugs, formulating enhancements, creating pull requests, or any other means of contribution, we encourage contributions from everyone.

## 📝 License

Distributed under the [MIT](https://choosealicense.com/licenses/mit/ "Link to license") license.

## 🙏 Credits

- https://github.com/celinekurpershoek/link-checker
- https://github.com/stevenvachon/broken-link-checker