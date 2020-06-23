# IRC Developer Docs
This set of documentation describes the IRC (Internet Relay Chat) protocol. The docs are written to give developers a good footing when writing software that uses or interacts with IRC.

This documentation takes on a lot of structure from something like the [MDN Web Docs](https://developer.mozilla.org/en-US/), which documents web technology instead.


## Building
The `dev` and `prod` config files are remnants of an old use case for these docs – the `ircdocs` config file is what we use to build the site.

In the `ircdocs` and `dev` modes, the site will build a basic browsable version that can be viewed through the server that Jekyll sets up. In `prod` mode, what's output is instead the HTML and files that get plugged into other sites more cleanly.

**when writing docs**
```sh
bundle exec jekyll serve -w --config _config-ircdocs.yml
```

**building**
```sh
bundle exec jekyll b --config _config-ircdocs.yml
```


## Documentation Structure
Here's the rough breakdown of what's included here:

- Tech References
    - Command Reference
    - Numeric Reference
    - Glossary
- Guides


### Future
Some stuff I want to describe very explicitly in future include:

- Hostname masking/cloaking
- Virtual Hosts
- `refs/modes/c/invite-only` and etc, `modes/c` for chan and `modes/u` for user modes, check the `join` command ref for links
- `refs/isupport/chanlimit` and etc


## Other References
Here are some other IRC references that devs may find useful:

- [IRCv3 Working Group](https://ircv3.net/)
- [ircdocs](http://ircdocs.horse/) generally


## What can I do with this?

The project's [license file](./LICENSE) lays this out in detail, but as a non-normative summary we've designed the license so that:

- If anyone modifies or builds on top of the content in this repo, we can pull those changes back into this project under this project's license.
- If IRC.com / the IRC Foundation or anyone else wants to take any of the content in this repo and pull it into the IETF process (for example, writing a new RFC describing the IRC protocol), they can do that and the content they use will be under the IETF contributor license terms.
