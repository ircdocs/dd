---
title: "RPL_EXAMPLE (000) Numeric"
ntitle: RPL_EXAMPLE (000)
nsub: "Indicates whatever's described on this page"
layout: numeric

numeric: "000"
numeric-groups:
    - appropriate
    - groups
    - here
# commands that return this numeric
numerics:
    - MOTD
    - JOIN

examples:
    - desc: First example
      content: |
        :irc.example.com 000 .. .. ..

format: |
    :server 000 [<format>] <goes> <here>

# if the numeric is sent by all servers, use this:
used-by-default: true
# if the numeric isn't sent by everything, instead list the ircds here:
used-by:
    unreal: true
    inspircd: true
    hybrid: true

# list of people who have written, edited, or otherwise contributed to this page
contributors:
    - doaks
---
The `RPL_EXAMPLE (000)` numeric is returned from the `XYZ` command. It indicates something described by this page.

-----

{% include numeric-format-header.html %}

- `<format>`: Optional parameter describing XYZ.
- `<goes>`: Short description of the parameter.
- `<here>`: Short description of the parameter.

Following the format description above is one or more paragraphs describing how to interpret the numeric when it's received.
