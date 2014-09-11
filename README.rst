Rake + Ant + JRuby
==================

This shows how to compile a jar project using Rake and Ant running on JRuby. JRuby is started with nailgun
to improve task execution time with Rake.

IMHO this is a nice intersection of mature build tools, convenient build tasks, and a flexible language.

Startup time is also important. This could be used quickly from something like `gosh (the go shell)`_.

*Requirements*:

- Rake (``gem install rake``)
- Apache ANT, the ``ANT_HOME`` environment variable must be set
- JRuby

*Usage*:

.. code-block:: bash

  # start jruby using nailgun
  jruby --ng-server

  # root of ant tool
  export ANT_HOME="$HOME/tools/ant"

  # connect using nailgun client; --dev option to improve startup time (https://github.com/jruby/jruby/wiki/Improving-startup-time)
  export JRUBY_OPTS="--ng --dev"

  # run rake 
  rake ant:compile ant:jar
  Compiling java from src/main/java to target/classes
  /home/tony/work/rake-jruby-test/Rakefile:12: warning: 'includeantruntime' was not set, defaulting to build.sysclasspath=last; set to false for repeatable builds
  Creating target/project.jar
  Building jar: /home/tony/work/rake-jruby-test/target/project.jar

  real    0m1.897s
  user    0m0.201s
  sys     0m0.246s

.. _gosh (the go shell): https://github.com/formwork-io/gosh
