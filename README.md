# disable_transparent_hugepage

[![Build Status](https://img.shields.io/travis/alexharv074/puppet-disable_transparent_hugepage.svg)](https://travis-ci.org/alexharv074/puppet-disable_transparent_hugepage)

## Overview

This module disables Transparent Hugepages (THP) on Linux platforms as required by applications such as MongoDB and Redis.  The procedure is based on recommendations published at [mongodb.org](https://docs.mongodb.org/manual/tutorial/transparent-huge-pages/).

The module changes the `/sys/kernel/mm/transparent_hugepage/enabled` and `/sys/kernel/mm/transparent_hugepage/defrag` settings, adds an init service to ensure the changes persist across reboots, and if applicable, configures tuned.

## Usage

Basic use:

~~~ puppet
include disable_transparent_hugepage
~~~

## Development

Please read CONTRIBUTING.md before contributing.

### Testing

Make sure you have:

* rake
* bundler

Install the necessary gems:

~~~ text
bundle install
~~~

To run the tests from the root of the source code:

~~~ text
bundle exec rake spec
~~~

To run the acceptance tests:

To run the acceptance tests:

~~~ text
BEAKER_set=centos-66-x64 bundle exec rake spec/acceptance
BEAKER_set=centos-72-x64 bundle exec rake spec/acceptance
~~~

etc.

### Release

This module uses Puppet Blacksmith to publish to the Puppet Forge.

Ensure you have these lines in `~/.bash_profile`:

~~~ text
export BLACKSMITH_FORGE_URL=https://forgeapi.puppetlabs.com
export BLACKSMITH_FORGE_USERNAME=alexharvey
export BLACKSMITH_FORGE_PASSWORD=xxxxxxxxx
~~~

Build the module:

~~~ text
bundle exec rake build
~~~

Push to Forge:

~~~ text
bundle exec rake module:push
~~~

Clean the pkg dir (otherwise Blacksmith will try to push old copies to Forge next time you run it and it will fail):

~~~ text
bundle exec rake module:clean
~~~
