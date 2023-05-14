# Purpose

I'm attempting to create a signed macOS bundle/app version of Guiguts. The
current Guiguts install / maintenance experience for Mac users is not great.
There are many steps, it is easy to get lost in the process, and there is a lot
of room for improvement.

# Goal

The end result, I hope, is that users can simply download the .app bundle (in a
`.zip` or `.dmg` file), move it into `/Applications`, and launch it like any
other app. The only dependency should be installing [XQuartz][].

On a modern macOS, this requires the app be signed, and also notarized by
Apple. I don't currently intend to distribute the app via the App Store, but
signing/notarizing are still needed outside the App Store.

[xquartz]: https://www.xquartz.org

# External dependencies

## XQuartz

The user will be instructed that XQuartz must be installed prior to launching
Guiguts. I won't attempt to install it for them.

## Guiguts settings

In older Guiguts, settings were bundled into the app directory. It worked fine,
but in the context of a Mac app bundle, the files are signed and cannot be
changed.

This was improved in [guiguts#959][pr959], which changes the behavior of the
setting.rc file and a couple of other files. Now the files in the app bundle
directory remain static (satisfying macOS), but the setting.rc located
elsewhere can be freely written by Guiguts.

[pr959]: https://github.com/DistributedProofreaders/guiguts/pull/959

## Developer Certificate

Obviously, signing the application will require a Developer Certificate from
Apple. For the time being, that certificate will be mine, at my own expense. I
would not expect DP or PG to take that cost or maintenance responsibility on
(unless they really preferred to do so).
