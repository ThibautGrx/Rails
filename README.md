# Rails cheat sheet [WIP]

# I. Create and configure

# Table of contents
1. [Create the app](#create_app)
2. [Configure](#Configure)
    1. [Add Rspec](#rspec)
    2. [Add Rubocop](#rubocop)

## 1) Create the app <a name="create_app"></a>
`rails new --help` to show default configuration options.

Useful options: 
`-d postgresql` Preconfigure for selected database
`-T` Skip test 
`./` Create app in the current folder. App name, is the name of the folder.

## 2) Configure test  <a name="configure"></a>
### a) Install Rspec <a name="rspec"></a>
[GitHub - rspec/rspec-rails: RSpec for Rails-3+](https://github.com/rspec/rspec-rails)
* Add gem to gemfile & `bundle install`
* Initialize the spec/ directory
`rails generate rspec:install`
* To include rails_helper by default, append to generated .rspec file:
`--require rails_helper`

### b) Add rubocop <a name="rubocop"></a>
* Add gem to gemfile & `bundle install`
* Add Relaxed Rubocop (https://relaxed.ruby.style/): Add the following lines to your `.rubocop.yml`:
```YAML
inherit_from:
  https://relaxed.ruby.style/rubocop.yml
```
* Add more config in `.rubocop.yml`:


```yaml
inherit_from:
  - http://relaxed.ruby.style/rubocop.yml

AllCops:
  DisplayStyleGuide: true
  DisplayCopNames: true
  Exclude:
    - 'db/schema.rb'
    - 'vendor/**/*'
    - 'config/environments/*.rb'
    - 'bin/*'

Rails:
  Enabled: True

Style/FrozenStringLiteralComment:
  Enabled: false

Metrics/BlockLength:
  Exclude:
    - 'spec/**/*.rb'
    - 'Guardfile'
    - 'vendor/bundle'

```
