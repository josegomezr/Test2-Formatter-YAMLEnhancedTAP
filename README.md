Test2::Formatter::YAMLEnhancedTAP
=================================

Enrich your TAP output with YAML Snippets!

`Test2::Formatter::YAMLEnhancedTAP` makes the TAP output of your perl
`Test2`-based test include additional context in the form of a YAML snippet.

Instead of the plain TAP output like:
```
t/02-singleton.t .. 
1..1
not ok 1 - simple-fail-msg
#   Failed test 'simple-fail-msg'
#   at t/fixtures/tests/simple-fail.st line 14.
# Looks like you failed 1 test of 1.
```

It becomes:

```
t/fixtures/tests/simple-fail.st .. 
1..1
not ok 1 - simple-fail-msg

  ---
  at:
    filename: t/fixtures/tests/simple-fail.st
    line: 14
    test_num: 0
  emitter: Test::More::ok
  message: "Failed test 'simple-fail-msg'\nat t/fixtures/tests/simple-fail.st line 14."
  ...
```

You might find it useful, maybe not? I certainly do with
[`TAP::Formatter::GitHubActions`][0] @
[josegomezr/TAP-Formatter-GitHubActions.git][1] to improve the accuracy of the
annotations and provide a cleaner output.

INSTALLATION
------------
To install this module the good ol' way, type the following:

```bash
perl Makefile.PL
make
make test
make install
```

With `cpanm`, add a feature:

```perl
# cpanfile

feature 'ci' => sub {
  requires 'Test2::Formatter::YAMLEnhancedTAP';
};
```

and then install it:

```bash
# assuming you're in the same dir where the cpanfile resides.
cpanm --installdeps . --with-feature=ci
```

USAGE
-----

```bash
T2_FORMATTER=YAMLEnhancedTAP prove -v
```

There's no other pretty way I know to use this formatter other than with `T2_FORMATTER=YAMLEnhancedTAP`.

DEPENDENCIES
------------
This module requires these other modules and libraries:

  - `TAP::Harness`

COPYRIGHT AND LICENCE
---------------------
Put the correct copyright and licence information here.

Copyright (C) 2023 by Jose D. Gómez R.

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself, either Perl version 5.38.0 or,
at your option, any later version of Perl 5 you may have available.


[0]: https://github.com/josegomezr/TAP-Formatter-GitHubActions.git
[1]: https://metacpan.org/pod/TAP::Formatter::GitHubActions