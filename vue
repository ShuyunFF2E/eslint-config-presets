# vim: ft=yaml

env:
  browser: true
  node: true

extends:
  # use recommended rules
  - eslint:recommended

  # custom parser
  - presets/misc/parser.yml

  - presets/misc/vue.yml

  # custom rules
  - presets/rules/base.custom.yml

  # use vue custom rules
  - presets/rules/vue.custom.yml
