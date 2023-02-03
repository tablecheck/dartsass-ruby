# Dart Sass for Ruby

[![build](https://github.com/tablecheck/dartsass-ruby/actions/workflows/build.yml/badge.svg)](https://github.com/tablecheck/dartsass-ruby/actions/workflows/build.yml)
[![gem](https://badge.fury.io/rb/dartsass-ruby.svg)](https://rubygems.org/gems/dartsass-ruby)

Use [Dart Sass](https://sass-lang.com/dart-sass) with Ruby.

This gem is a fork of [sass/sassc-ruby](https://github.com/sass/sassc-ruby)
which maintains API compatibility but delegates to the
[sass-embedded gem](https://github.com/ntkme/sass-embedded-host-ruby)
which provides native binaries for Dart Sass (instead of the libsass
C implmentation.)

For ease of upgrading, the root namespace `::SassC` is still used by this gem,
although it is now a misnomer. This is planned to be renamed in a future
major version release.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'dartsass-ruby'
```

Rails/Sprockets users should instead add [dartsass-sprockets](https://github.com/tablecheck/dartsass-sprockets):

```ruby
gem 'dartsass-sprockets'
```

### Upgrading to Dart Sass

This gem is a drop-in replacement to [sassc-ruby](https://github.com/sass/sassc-ruby).
Note the following differences:

1. Option `style: :nested` and `style: :compact` behave as `style: :expanded`. Use `style: :compressed` for minification.
2. Option `:precision` is ignored, as Dart Sass sets it to a sufficiently high value.
3. Option `:line_comments` is ignored and will always be disabled.
4. `Sass2Scss` functionality has been removed.

See [the dart-sass documentation](https://github.com/sass/dart-sass#behavioral-differences-from-ruby-sass) for other differences.

## Usage

This library utilizes [dart-sass](https://github.com/sass/dart-sass) to compile
SCSS or SASS syntax to CSS. To compile, use a `SassC::Engine`, e.g.:

```ruby
SassC::Engine.new(".klass1, .klass2 { color: :red; }", style: :compressed).render
```

## Alternatives

* [dartsass-rails](https://github.com/rails/dartsass-rails): The Rails organization
  maintains its own wrapper for Dart Sass. Unlike this gem, dartsass-rails does
  not support Sprockets.

## Credits

* This gem is maintained and used in production by [TableCheck](https://www.tablecheck.com/en/join). (We'd be very glad if the Sass organization could take over maintainership in the future!)
* Kudos to [@ntkme](https://github.com/ntkme) for dart-sass support.
* Credit to [Ryan Boland](https://ryanboland.com) and the authors of the original
  [sass/sassc-ruby](https://github.com/sass/sassc-ruby) gem.
* See our [awesome contributors](https://github.com/tablecheck/sassc-ruby/graphs/contributors).

### Contributing

1. Fork it ([https://github.com/tablecheck/dartsass-ruby/fork](https://github.com/tablecheck/dartsass-ruby/fork))
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`) - try to include tests
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
