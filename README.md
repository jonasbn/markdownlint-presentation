# Markdownlint Presentation

Collection of examples and notes for my **Markdownlint** presentation

## Resources

- [Slideshare](https://www.slideshare.net/jonasbn), my presentation referencing this GitHub repository

- [Wikipedia: Markdown](https://en.wikipedia.org/wiki/Markdown)
- [CommonMark](https://commonmark.org/) specification of open Markdown-inspired variation
- [CommonMark GitHub repository](https://github.com/CommonMark/CommonMark)

- [Markdownlint](https://github.com/markdownlint): (`mdl`) the first and original implementation in Ruby
- [Markdownlint](https://github.com/DavidAnson/markdownlint
): implementation in Node inspired and based on the Ruby implementation
- [Markdownlint Command Line Interface](https://github.com/igorshubovych/markdownlint-cli): (`markdownlint`) GUI for the above Markdownlint Node library implementation

- [Sublime Text Markdown editing plugin](https://github.com/SublimeText-Markdown/MarkdownEditing), based on the Ruby implementation (`mdl`)
- [Visual Studio Code Markdownlint plugin](https://github.com/DavidAnson/vscode-markdownlint), based on the Node implementation

## markdownlint configuration

```json
{
    "default": true
}
```

Basic configuration in JSON for `markdownlint`, enabling all rules

## Using markdownlint-cli with Travis CI

```yaml
language: node_js
node_js:
- '6'
install:
- npm install -g markdownlint-cli
script:
- markdownlint *.md ; markdownlint */*.md
```

Example lifted from: [jonasbn: TIL](https://github.com/jonasbn/til) (_Today I Learned_)

Example of staged builds:

```yaml
language: node_js
node_js:
- '6'

before_install:
  - sudo apt-get install -y libxml2-utils

install:
   - npm install -g markdownlint-cli

jobs:
  include:
    - stage: "Documentation test"
      name: "Markdown test"
      script: markdownlint README.md
    - stage: "Product test"
      name: "XML/XSD test"
      script: xmllint --schema epp.xsd xml/*.xml
```

Example lifted from: [DK Hostmaster: epp-xml-files](https://github.com/DK-Hostmaster/epp-xsd-files)

See the fine result at [Travis CI](https://travis-ci.org/DK-Hostmaster/epp-xsd-files)
