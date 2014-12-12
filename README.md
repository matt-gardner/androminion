# Androminion

This is an Android app that implements the game Dominion, by Rio Grande Games.
There is a branch in the Google code repository that allows for multiplayer
using a client-server architecture.  I wrote that code.  This repository is
taken from that branch, removing all of the history (the history was long and
ugly, and had lots of problems).

# BUILDING THE APP

## Building/debugging with ant

Make sure you have the android SDK installed (here is a good guide:
http://developer.android.com/training/basics/firstapp/index.html), with
whatever target is found in the project.properties under androminion/ and
actionbarsherlock/ (in both the multiplayer branch and trunk, that is
android-14 for actionbarsherlock/project.properties, and android-15 for
androminion/project.properties; so, using the SDK manager that you'll find when
you get the android SDK, be sure you install the "SDK Platform" for both API
level 14 and API level 15).

With the SDK installed, you can just use ant to build the app (I think you can
also run the app through Eclipse, but I don't know much about how that works -
the guide linked above might help you if that's what you want to do).  So cd
into the androminion/ directory, then run the following two commands:

`ant vdom_lib`
`ant debug`

The first command builds the vdom library code and puts a .jar file in the
androminion directory, and the second command builds the app (including the
actionbarsherlock code) in debug mode.  There's probably a way to change the
build files so you only need one command, but I didn't look hard enough to
figure it out.

Once you've built the app, you can install it on your device using adb.  There
are instructions for that on the page linked above, too.  The command, though,
is

`adb install -r bin/Androminion-debug.apk`

The -r means "please overwrite any version already there".  But it will
probably fail the first time if you already have androminion installed from the
play store, as it's signed by a different certificate.  So you'll have to
uninstall the version from the play store, then run the command.

Once it's installed, if you see a crash, you can get the log output by running

`adb logcat`

This could be long and obnoxious; what I like to do is run

`adb logcat -c`
`adb logcat -d |less`

The -c in the first command clears the log (you do this just before doing
something on the app that you know will crash it), and the -d in the second
command dumps the log and exits, instead of continuously showing messages as
they come in.


## Building/debugging with Eclipse

TODO(matt): I don't use eclipse, so someone else should probably write this...

## LICENSE

This code is licensed under the LGPL.  See the original Androminion repository
for more details (code.androminion.com/p/androminion).
