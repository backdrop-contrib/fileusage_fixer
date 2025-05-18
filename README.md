# File Usage Fixer

Utility module to fix the odd situation that managed files have a status of
"permanent" but no usage record.

**How could this happen?**

There are multiple reasons for that, the most common is upgrading from
Drupal 7, which didn't handle files the way Backdrop CMS does (managed, with
usage records).
Files and images only used *inline*, for example inserted into a WYSIWYG
editor, aren't handled yet when upgrading, so these files end up in this
odd state.

**How can you know that your site is affected?**

Trying to use such files in the editor via Image library will end up with a form
error "The file used in the XXX field may not be referenced.".

To verify, go to admin/content/files and sort by "Use count" (ascending).
You'll find files with state "permanent", but without usage count.

Files without usage count and in state temporary will automatically get deleted
on cron runs (after a grace time of 6 hours) - that's normal behavior.
Files without usage count, but in state "permanent" will not get deleted,
but they're not actually usable, either.

**What can you do about it?**

Install this utility module, go to TBD..., and submit the form. Depending on the
amount of affected files (more than X000?), you might need to do that multiple times.

When you're done, you can safely uninstall this module again.

You can now safely reference any of the available files.

Or you can wait until either or both of the related core issues got
resolved. todo - insert links


## Installation

- Install this module using the
  [official Backdrop CMS instructions](https://docs.backdropcms.org/documentation/extend-with-modules)

## Issues

Bugs and feature requests should be reported in the
[Issue Queue](https://github.com/backdrop-contrib/fileusage_fixer/issues).

## Current Maintainers

- Indigoxela (https://github.com/indigoxela)

## License

This project is GPL v2 software. See the LICENSE.txt file in this directory for complete text.
