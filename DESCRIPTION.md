# Summary

We at The App Business try to keep as closely as possible to the [Community Ruby-Style-Guide][1]. We use the gem
provided in this repository as a means to automatically check our Ruby(-on-Rails) projects against this style-guide and
other aspects of code-quality and security known to the Ruby community. We also integrate this static analysis into our
continuous integration scheme to ensure that only viable code leaves our house.

## Aspects we check for

### Style-guide

First and foremost our code must be formatted according to the [Community Ruby-Style-Guide][1] which represents the
Ruby community's opinion, how Ruby code is supposed to look like. Static analysis is done using [RuboCop][2] which can
also be used to automatically enforce most violations of the style-guide.

#### Differences of our in-house rules to the style-guide

In rare cases we decide that a rule or guideline in the [Community Ruby-Style-Guide][1] is detrimental for our own use
cases. Then we document those differences here and adapt the rubocop configuration we use accordingly. Of course we stay
up-to-date with the changes to the [Community Ruby-Style-Guide][1] and discuss and decide whether or not to adopt
changes.

#### Differences in detail

At this time we are in full agreement with the [Community Ruby-Style-Guide][1].

### Sandi Metz' four rules

In order to achieve a maximum of readability, class decomposition, class specialization, cleanliness and to keep
complexity low, Sandi Metz proposed the following [four rules][11]:

1. Classes can be no longer than one hundred lines of code.
2. Methods can be no longer than five lines of code.
3. Pass no more than four parameters into a method. Hash options are parameters.
4. Controllers can instantiate only one object. Therefore, views can only know about one instance variable.

Rule 4 is considered more as an add-on to the other 3 in case an MVC approach is used (i.e. Ruby-on-Rails).

Again, exact percentages of the 'correct to violating'-ratio are still to be determined. But in general they give a
good indication of the present code quality.

### Code Smells, Duplication, and Complexity

We try to keep the three aspects mentioned as low as possible. We use [RubyCritic][5] to analyse our code to check for
these.

RubyCritic itself uses the tools [Reek][6], [Flay][7] and [Flog][8] to analyse these aspects:
* [Reek][6] is used to detect code smells
* [Flay][7] analyses the code to find duplications
* [Flog][8] checks for code readability and
complexity.

While exact threshold values for both frequency and severity of those aspects are still to be determined,
we strive to keep them as low as possible and treat cumulations of these values as an alarm signal which has to be
looked into and discussed.

### Detection of vulnerable versions of gems

A Ruby application often requires some ruby gems.
Assuming that bundler software is used to manage the required gems and their dependencies, their names and versions will be consigned in the `Gemfile`.

Several problems are identified, among them:
* misspelling of the gems' names, that can lead to insecure gems
* gem's version is obsolete, that can lead to security vulnerability.

To check the integrity of the required gems, the software [bundler-audit][3] is used.
It basically screens the `Gemfile.lock` and mainly makes sure that the specified gems are healthy.
The exhaustive list of all known vulnerabilities that bundler-audit checks can be found [here][16].

### Quality of Rails code

Best practices exist for writing Rails applications code. The exhaustive list of the best practices can be found [here][15].

To ensure the quality of our Rails code, the code metric tool [rails_best_practices][9] is used. All the features covered by this tool can be found [here][14], among these features:
* protect against mass assignment
* restrict auto-generated routes
* avoid needless deep nesting.

### Security vulnerabilities of Ruby on Rails applications

Security vulnerabilities such as SQL injection, Cross Site Scripting, command injection... must be tackled.

A lot of known security vulnerabilities are identified in the [Ruby On Rails' security Guide][13].
This manual also gives countermeasures for the identified security vulnerabilities.
In order to be sure that all the common security problems are reviewed, a systematic and automatic scan has to be performed.

To achieve this point, the tool [Brakeman][4] is used. Brakeman is an open source vulnerability scanner.
It will basically perform static analysis of the source code, running the application is not required.

###


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
[13]: http://guide.rubyonrails.org/security.html
[14]: http://rails-bestpractices.com
[15]: https://github.com/bbatsov/rails-style-guide
[16]: https://github.com/rubysec/ruby-advisory-db
