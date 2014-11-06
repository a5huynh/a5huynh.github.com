---
title: "Define: Command Line"
location: San Francisco
---

Google has a [search feature](http://www.google.com/intl/en/help/features.html)
that allows you to find the definition of any word or phrase when using the
`define:` prefix on your search term. This along with the built-in dictionary
in OSX provides an incredibly useful set of tools to find a definition for a
word or phrase as quickly as possible.

But if you are a terminal junkie like me, you spend a lot of time on the
command line. Sometimes you just need a definition at that instant and can't be
bothered to switch to another window to find it. Or perhaps you have a list of
words you'd like to quickly `grep` and find definitions. This is where
[sdvc](http://en.wikipedia.org/wiki/Sdcv) comes in.


## What is sdcv? And how do I get it?

sdcv is a console version of [StarDict](http://en.wikipedia.org/wiki/StarDict)
an open source utility used to access dictionary files in multiple languages
using a common dictionary file format.

The nature of the utility also allows you to download multiple dictionaries to
cull through ranging from English dictionaries to dictionaries of hacker
jargon. Finally, to this utility, all you need to do is:

    brew install sdcv

And then choose the necessary [dictionaries](http://abloz.com/huzheng/stardict-
dic/dict.org/) you may need. Dictionaries should be placed under
`/usr/share/stardict/dic` to ensure sdcv can detect it.


## Adding an alias for the define command

Now that you have sdcv installed, why use and remember a obscure name such as
sdcv to query your definitions. I added the following to my `.bash_profile` to
define (hah) a function that will call sdcv with some good defaults with
whatever word or phrase I pass to it.

{% highlight bash %}    
define () {
    # Check if sdcv is installed
    if command -v sdcv > /dev/null; then
        # -0 show UTF-8 output
        # -c show colorized output
        sdcv -0c "$@"
    else
        echo "You need to install sdcv."
    fi
}
{% endhighlight %}