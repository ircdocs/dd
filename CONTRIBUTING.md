# Contributing to the IRC DevDocs
Welcome to IRC DevDocs! Thank you very much for taking the time to contribute, it's always good to have more eyes looking at (and editing) these pages.

This page lists a set of guidelines and advice to simplify contributing to this project, and to (in the case of submitted changes) make it more likely that we'll accept your changes.



## Table of Contents

- [CLA](#cla)
- [Submitting a change](#submitting-a-change)
    - [New Reference Page](#new-reference-page)
    - [Reference Page Update](#reference-page-update)
- [Writing Advice](#writing-advice)
    - [Reference Pages](#reference-pages)
        - [Format String](#format-string)


## CLA
By submitting any change to this project, you agree to the [CLA](CLA.md) of this project.


## Submitting a change
The main way to contribute is by submitting changes. This can range from updating a command or a numeric's description to submitting an entirely new guide. Here's a few things to keep in mind, for the different sorts of changes that you can submit.

Note, by submitting any change to this project, you agree to the [CLA](CLA.md) of this project.

Alright, let's go through each type of change:


### New Reference Page
This is documenting a new command, numeric, or mode. We always appreciate new contributions, however there are some checks that we do due to the somewhat fragmented nature of IRC support out there.

If you're documenting a numeric, discuss your change with us on the [issue tracker](https://github.com/ircdocs/dd/issues). Specifically, tell us the number and the name of the numeric you're looking to describe. For example, something like:

> **RPL_HELLO (020)**
>
> Hi there, I'd like to write up a page documenting this numeric, as implemented by the RusNet IRCd and (the original) IRCd.

We'll let you know whether this numeric is one that we'd accept a contribution for. We may say that yes, we'd gladly accept the change, or say that we unfortunately won't merge documentation for this numeric. If we reject it, it will be because [conflicting definitions exist](https://defs.ircdocs.horse/defs/numerics.html) or because there isn't wide enough adoption of the given numeric for our liking.

If we say go for it, or you're documenting a command, then the next step is writing it up! The basic format for commands is shown on the [example command page](_examples/command.md), and the basic format for numerics is shown on the [example numeric page](_examples/numeric.md).

In addition to creating this page and placing it in the appropriate `refs/` directory, for numerics you will need to modify [`_data/numerics.yml`](_data/numerics.yml) and add a short description of the numeric so that it appears on the numeric page.

To make things simple for users, we logically group commands and numerics that include similar information, are used in similar places, and otherwise are linked with other commands/numerics. To do this, you can create command or numeric groups, and then apply those groups to the given pages. For commands, look at [`command-groups.yml`](_data/command-groups.yml), and for numerics the [`numeric-groups.yml`](_data/numeric-groups.yml) file lists your groups.

You can create a new group if necessary, but keep in mind that there should be at least one other (and hopefully more than one other) command/numeric that would be a part of the group.

We've got general page writing advice below in the [Reference Pages](#reference-pages) section.

Once the page is written, and the data files have been updated as appropriate, simply submit your change as a new Pull Request! We appreciate grouping changes as appropriate, so for example if you're documenting a logical group of numerics at once, or a command and the new numerics that command uses, it's better to submit all of these changes as a single PR rather than separately.


### Reference Page Update
For example, updating a command/numeric page, a mode page, or any other general existing reference page.

Try to make each change its own separate commit, to make reviewing your change easy. If you submit a Pull Request with three small commits, each describing the included update, it's relatively easy to review and get pulled in. If you submit a single PR where half the page seems to be rewritted sporadically, then it's much more difficult to review.

Keep in mind the page writing advice below in the [Reference Pages](#reference-pages) section.



## Writing Advice
We have a few different types of pages, and each type of pages has their own style and feel. We've got some advice below for the different types of pages.


### Reference Pages
There are two main objectives with the reference pages:

- Act as an accurate record of how a specific command/numeric/etc acts.
- Make it as simple as possible to write an implementation of the described command/numeric.

These pages need to use fairly specific, standard language. We do our best to make sure all of our reference pages use the same phrases, the same words, and the simplest representations. Where possible, try to keep to the same terms that other pages use (for example, when referring to channel operators, try to always call them "channel operators" rather than just "opers" or "operators").

In addition, to make writing an implementation simple, these pages should describe things in a start-to-end sort of way. For example, when describing how to interpret a given parameter, the page should describe all possible cases in the same place rather and leae no room for misinterpretation. This is a bit of a stickler, and one reason why project maintainers may take submitted work and push their own changes on top to change the structure of it.

#### Format String
This is a specific mention of the 'format string', and how to write it. We could go for something like [ABNF grammer](https://tools.ietf.org/html/rfc5234) as used by the IETF, but that isn't quite readable for average users (and it's difficult to write accurately as well).

Here are the elements our strings use:

- `<param>`: Angle brackets `<>` surrounding something means that it's a variable.
- `[<param>]`: Square brackets `[]` surrounding something means that it's optional. These may be nested.
- `<param>{,<param>}`: Curly brackets `{}` surrounding something means that it may be repeated zero or more times. In this example, `<param>` may be used one or more times, with each use separated by a comma.
- `<channel>|<nick>`: A pipe `|` means that one of the given elements can be used. In this example, either `<channel>` or `<nick>` can be supplied, but nothing else can be.

Our strings are written to be as simple and easily-understood by implementers. We prefer being meaningful and simple over being strictly correct, and in cases will list multiple format strings to make the different uses of a command or numeric explicit.

In cases where the format string may be a little confusing, the examples on the page illustrate the different cases described. Especially when curly brackets or a pipe is used.

When all else fails, fall back to the example set by existing format strings. We always appreciate change suggestions to this section that help implementers, though!

Here's an example format string:

    EXAMPLE [<param1>] <param2> <param3>

In this example, `<param1>` is optional, and the two other parameters are mandatory.

Here's another example:

    EXAMPLE [<param1> [<param2>]] <param3>

In this example, `<param1>` and `<param2>` are optional, but `<param2>` can only be included if `<param1>` is included. `<param3>` is mandatory.
