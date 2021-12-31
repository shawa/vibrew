```
         ,__
 _   __(_) /_  ________ _      __
| | / / / __ \/ ___/ _ \ | /| / /
| |/ / / /_/ / /  /  __/ |/ |/ / 
|___/_/_.___/_/   \___/|__/|__/
```

# Declarative Homebrew

`vibrew` is a bit like `visudo` or `crontab -e`, but for a
[homebrew](https://brew.sh) `Brewfile`. It makes it a bit easier to maintain a
declarative homebrew installation, if that's what you like.

I've been using it as my only interface to `brew install` since my latest
factory reset.

[Homebrew Bundle](https://github.com/Homebrew/homebrew-bundle) pitches itself as
a "non-ruby dependency" manager -- a bit like `bundler` -- but in practice, it
makes for a very nice means of capturing all of one's homebrew packages and
casks. This can help in, say, bootstrapping a new machine or macOS installation.

You write your dependencies down in a `Brewfile`, which `brew bundle` then
reads, much like a `mix.exs` or `gemfile`:

``` ruby
tap 'railwaycat/emacsmacport'
cask 'emacs-mac'

brew 'tree'
brew 'fzf'
```

`vibrew` is just a script to make editing this file, and re-running `brew
bundle` a bit quicker.

## Setup

1. Place the `vibrew` executable somewhere on your `PATH`.
1. Set and export the `BREWFILE` environment variable. Make sure `EDITOR` is
   also correctly set.


## Usage

1. Run `vibrew`; you'll be dropped into your editor.
1. Add/remove any dependencies (see the `Homebrew Bundle`) link above for more
   instructions
1. If the brewfile has changed (sha sums before/after differ), it'll run `brew
   bundle`.
   
   
## Other notes
- Brew bundle will place a `Brewfile.lock.json` in the same directory as the
  given `Brewfile`
- Unless you pin their versions, each time you run `brew bundle` (and thus make
  a change to your Brewfile with `vibrew`), any installed packages/casks will be
  updated. I don't mind this.
