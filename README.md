Suspenders is a base Rails project that you can upgrade. It is used by
thoughtbot.

![Suspenders](http://www.blogcdn.com/www.autoblog.com/media/2008/08/misuse-of-hydraulics.jpg)

To create a new project first install suspenders:

  gem install suspenders

Then run:

  suspenders create projectname

This will create a project in `projectname'.  You should then follow the
instructions on Github to upload that project there.  This script creates an
entirely new git repository, and is not meant to be used against an existing
repo.

When making a change to a project that was created via this template, consider
whether it's a change that should be made across all projects.  If so, then
make the change in suspenders instead of your project.  Note: If you don't
have commit access to suspenders, create a github ticket and we'll review your
suggestion.

Once that's committed, you can pull into your project to get all the changes
that have been made in suspenders since your last pull:

  git pull suspenders master

About Suspenders
----------------

Suspenders was created for use at thoughtbot, inc. (http://thoughtbot.com) as a
baseline application setup, with reasonable default plugins that the majority
(if not all) of our applications used, as well as best-practice configuration
options.

Suspenders currently includes a version of Rails from the 2.3 stable branch.
You can determine the changeset with the vendor/rails/REVISION_xxxxx file.

Gems (unpacked in vendor/gems, unless they are compiled gems):
--------------------------------------------------------------

For record pagination:

  will_paginate (2.3.11)

For text formatting:

  RedCloth (4.2.2, not unpacked, this is a compiled gem)

Form builder:

  Formtastic (0.2.1)

File attachments:

  Paperclip (2.3.0)

Basic user auth:

  Clearance (0.7.0 engine)

For testing:

  rspec
  jferris-mocha (standard mocha plus test spies)
  factory_girl (fixture replacement for test data)
  shoulda (rails test helpers and context framework)
  timecop (for time sensitive tests)
  fakeweb (for blocking HTTP calls to third-party services)

Plugins (in vendor/plugins):
----------------------------

  hoptoad_notifier
  limerick_rake
  validation_reflection (used by formtastic to find required fields)

Initializers (in config/initializers)
-------------------------------------

  action_mailer_configs.rb
  We use SMTP by default in all applications.

  hoptoad.rb
  Get your API key at http://hoptoadapp.com

  requires.rb
  Automatically requires everything in
    lib/
    lib/extensions
    test/mocks/RAILS_ENV (Removed in Rails 2, we decided to keep it)
  Add other things you need to require in here.

  time_formats.rb
  Two time formats are available by default, :short_date and :long_date.
  Add other time formats here.

Rake Tasks
----------

Rake tasks are contained in the limerick_rake gem.

  bootstrap
  Provides rake tasks for loading data into the database.  These are used for
  an initial application dataset needed for production.

  capistrano
  Standard capistrano deployment tasks

Testing
-------

Testing is done utilizing RSpec, Shoulda, factory_girl, and mocha.

factory_girl is a fixture replacement library, following the factory pattern.
Place your factories in test/factories.rb.  The fixture directory has been
removed, as fixtures are not used.

Shoulda matchers are used on top of RSpec.

Timecop is used to freeze the time for the entire test suite. It is frozen to
the value of Time.now; that is, the time that the tests suite starts running.

Deployment
----------

Deployment is done using capistrano, and deploys to a mongrel cluster, running
under Apache.

Rake tasks are provided for managing git branches which the different
environments pull from for deploy.

To push the git master to git staging branch run:

  rake git:push:staging

To push the git staging branch to production branch run:

  rake git:push:production

Setup your deployment environment by running:

  cap ENVIRONMENT deploy:setup
  (You'll be prompted for the environment's database password)

Deploy to the desired environment by running:

  cap ENVIRONMENT deploy

The default environment for deploy is staging, to deploy to staging, just run:

  cap deploy

Mascot
------

The official Suspenders mascot is Suspenders Boy:

  http://media.tumblr.com/1TEAMALpseh5xzf0Jt6bcwSMo1_400.png
