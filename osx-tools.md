#OS X Tools
***

### Philosophy

The marriage of *NIX underpinnings with a consistent, aesthetically pleasing, and integreated windowing system is the magic of OS X. Thus, tools that fit elegantly into this ecosystem are the preference&mdash;and OS X gets more than its fair share of exemplarary and beautifull programs, tools, and utilities. Possibly because it attracts developers who share this mindset and they end up writing new tools.

Aside: [Wireshark](https://www.wireshark.org) was an example of a tool that didn't fit this model; it [looks like](https://blog.wireshark.org/2013/10/switching-to-qt/) they've gone a long way to [fixing this](http://wiki.wireshark.org/Development/QtShark). Lesson: prefer [Qt](http://qt-project.org) over [GTK+](http://www.gtk.org).

### The Tools

- [Kaleidoscope](http://www.kaleidoscopeapp.com) for visual diffs and merges.
- [Paw](https://luckymarmot.com) for working with HTTP/REST APIs.
- [Reveal](http://revealapp.com) for spelunking iOS apps views/layers/constraints at runtime.
- [1Password](https://agilebits.com/onepassword) for Password storage and syncing. Or just general secure storage.
- [Charles](http://www.charlesproxy.com) for HTTP proxy spelunking. Not an explarary OS X app, but still useful.
- [homebrew](http://brew.sh) for *NIX-style package management; helps bridge the worlds, and means less ./configure && make && make install.
- [Marked 2](http://marked2app.com) for viewing [Markdown](http://daringfireball.net/projects/markdown/).

### Up-and-Coming Candidates (meaning yet to be tried)

##### Database Tools

- [Core Data Editor](http://thermal-core.com/CoreDataEditor/) for a visual interface to Core Data stores.
- [Sqlite Pro](https://www.sqlitepro.com) for a Sqlite visual tool.
- [PG Commander](https://eggerapps.at/pgcommander/) for a Postgres visual tool.
- [Induction](https://github.com/Induction/Induction) for a cross-database visual tool. Also open source by [Triple-t](http://mattt.me).

##### Addendum

- [Marked 2](http://marked2app.com) is great, but also has some limitations due to sandboxing and Brett's philosophy on the app.
  - [Sandboxing introduces permission-prompt nonesense](http://support.markedapp.com/discussions/problems/52307-internal-links-inconsistencies)  with links to local files. Ugh.
  - There is also a navigation issue here; [I desire browser-like back behaviour here, but that doesn't fit Brett's vision for the application](http://support.markedapp.com/discussions/questions/6417-back-buttonopen-preference).
  - Possible idea is to look at adapting Wolf's [MarkdownLive](https://github.com/rentzsch/markdownlive). Wolf seems to have abandoned the project; it doesn't build anymore because it uses GC. I have a [fork](https://github.com/corvino/markdownlive) that converts to ARC and upgrades Discount to 2.1.7 that would serve as a starting point. For mymy copious free time...
    - Being able to plug in different ["Markdown implementations"](http://blog.codinghorror.com/standard-markdown-is-now-common-markdown/). Marked supports [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) and [Discount](https://github.com/Orc/discount), but it's not clear eitehr would fit the implementation when writing for the web. It seems like very little of the applicaiton needs to be implmentation specific; the commonality seems to be taking input and producing HTML. Keeping in-sync with a given publishing platform seems to be desirable.
