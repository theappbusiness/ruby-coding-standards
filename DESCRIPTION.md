# Summary

We at The App Business try to keep as closely as possible to the [Community Ruby-Style-Guide][1]. We use the gem
provided in this repository as a means to automatically check our Ruby(-on-Rails) projects against this style-guide and
other aspects of code-quality and security known to the Ruby community. We also integrate this static analysis into our
continuous integration scheme to ensure that only viable code leaves our house. 

# Aspects we check for

## Style-guide

First and foremost our code must be formatted according to the [Community Ruby-Style-Guide][1] which represents the
Ruby community's opinion, how Ruby code is supposed to look like. Static analysis is done using [RuboCop][2] which can
also be used to automatically enforce most violations of the style-guide.

### Differences of our in-house rules to the style-guide
 
In rare cases we decide that a rule or guideline in the [Community Ruby-Style-Guide][1] is detrimental for our own use
cases. Then we document those differences here and adapt the rubocop configuration we use accordingly. Of course we stay
up-to-date with the changes to the [Community Ruby-Style-Guide][1] and discuss and decide whether or not to adopt
changes. 

### Differences in detail

At this time we are in full agreement with the [Community Ruby-Style-Guide][1].

## Code Smells, Duplication, and Complexity

We try to keep the three aspects mentioned as low as possible. We use [RubyCritic][5] to analyse our code to check for
these. RubyCritic itself uses the tools [Reek][6], [Flay][7] and [Flog][8] to analyse these aspects. [Reek][6] is used
to detect code smells, [Flay][7] analyses the code to find duplications, and [Flog][8] checks for code readability and
complexity. While exact threshold values for both frequency and severity of those aspects are still to be determined,
we strive to keep them as low as possible and treat cumulations of these values as an alarm signal which has to be
looked into and discussed.
 
 



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