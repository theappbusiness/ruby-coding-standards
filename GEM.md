# Summary

This is a gemified collection of tools for checking code and configuration against the
[bbatsov/ruby-style-guide][1] and other sources in order to provide a common
set of guidelines we all should adhere to.

## Tools included

* [RuboCop][2]: "RuboCop is a Ruby static code analyzer. Out of the box it will enforce
  many of the guidelines outlined in the community [Ruby Style Guide][1]."
* [sandi_meter][10]: "Static analysis tool for checking your Ruby code for [Sandi Metz' four rules][11]."
* [RubyCritic][5]: "RubyCritic is a gem that wraps around static analysis gems
  such as [Reek][6], [Flay][7] and [Flog][8] to provide a quality report of your Ruby code."
* [bundler-audit][3]: "Checks for vulnerable versions of gems in `Gemfile.lock`."
* [rails_best_practices][9]: "rails_best_practices is a code metric tool to check the quality of Rails code."
* [Brakeman][4]: "Brakeman is a static analysis tool which checks Ruby on Rails
  applications for security vulnerabilities."

## Installation

Add this to your Gemfile development dependencies (better not to default dependencies because it requires ~70 gems to
run):

  ```
  gem 'ruby-coding-standards', git: 'git@github.com:theappbusiness/ruby-coding-standards.git', require: false
  ```
  
Execute the following to install all the necessary gems and the check_code script. 
  
  ```
  $ bundle install --binstubs
  ```

You should then be able to run this to execute checks and produce reports:

  ```
  $ check_code [OPTIONS]
  ```

Please see the below paragraph for the common options.

For runtime options to run specific checks:

  ```
  $ check_code --help
  ```

## Usage and output

In the paragraphs below, the syntax is the following: "Command (`OPTION`)".

Where:
- "Command" stands for the specific command you want to launch
- `OPTION` is the suffix that you have add to the `check_code` command to launch your specific command.

### Whole suite (`-A`)

Launching all the tools in a row is possible.
All the tools are described in the file [DESCRIPTION.md](DESCRIPTION.md).

### RuboCop (`-C`)

The most important ruby style check is done using [RuboCop][2]. We try to keep to the rules in the community
[Ruby Style Guide][1] as much as possible. Its default configuration reflecting the current ruleset can be found
[here][12]. If the default configuration should be changed or adapted for our purposes, we use the included
`.rubocop.yml` file as per the documentation in the default configuration file above.

The RuboCop report can be found in tmp/rubocop.txt

RuboCop can automatically correct a lot of the reported violations by executing

  ```
  $ rubocop -a
  ```
Please refer to the RuboCop documentation for more.

### RubyCritic (`-T`)

The [RubyCritic][5] report can be found in tmp/rubycritic/overview.html

In the 'Code'-tab, we try to keep as many files as possible at an A rating, only in well-founded cases, exceptions are
allowed, keeping code smells, duplications, and code smells to a minimum.

Every file can be viewed individually in order to get a more detailed report on the points that can and should be
improved.

### sandi_meter (`-S`)

[sandi_meter][10] checks your code for [Sandi Metz' four rules][11] and is called with the `-g` parameter by default
when using `check_code`, opening a browser window if possible.

The HTML test report can be found in `tmp/sandi_meter/index.html` along with a config file (`config.yml`) and a database
with previous report results (`sandi_meter.log`).





[1]: https://github.com/bbatsov/ruby-style-guide
[2]: https://github.com/bbatsov/rubocop
[3]: https://github.com/rubysec/bundler-audit
[4]: https://github.com/presidentbeef/brakeman
[5]: https://github.com/whitesmith/rubycritic
[6]: https://github.com/troessner/reek
[7]: https://github.com/seattlerb/flay
[8]: https://github.com/seattlerb/flog
[9]: https://github.com/railsbp/rails_best_practices
[10]: https://github.com/makaroni4/sandi_meter
[11]: http://robots.thoughtbot.com/post/50655960596/sandi-metz-rules-for-developers
[12]: https://github.com/bbatsov/rubocop/blob/master/config/default.yml
