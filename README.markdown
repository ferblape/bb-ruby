# bb-ruby

bb-ruby is a [BBCode](http://www.bbcode.org) implementation for Ruby.

It will convert strings with BBCode markup to their HTML equivalent.

This version is a fork from original [bb-ruby](git://github.com/cpjolicoeur/bb-ruby) for adding support
to the [BBCode version of PphpBB forums](http://www.phpbb.com/community/faq.php?mode=bbcode), that adds some tag ids inside of each tag. For example:

`[b:2131ds]some text[/b:2131ds]`

I have been adding too another special features, like redefinition of the HTML that each BBCode tag should be translated to.


## Installation

To install as a plugin:

`./script/plugin install git://github.com/cpjolicoeur/bb-ruby.git`

To install as a gem:

`sudo gem install cpjolicoeur-bb-ruby --source=http://gems.github.com/`


## Usage

`require 'bb-ruby'` (only needed if installed as a gem)

BBRuby has been included directly into the String class for use on any string object:

`text = "[b]Here is some bold text[/b] followed by some [u]underlined text[/u]"`

`output = text.bbcode_to_html`

`text.bbcode_to_html!`

Only allow certain tags:

`output = text.bbcode_to_html({}, :enable, :image, :bold, :quote)`

Disable certain tags:

`output = text.bbcode_to_html({}, :disable, :image, :bold, :quote)`

Alternative Direct usage:

`output = BBRuby.to_html(bbcode_markup)`

Define your own translation, in order to be more flexible:

    my_blockquote = {
      'Quote' => [
        /\[quote(:.*)?=(.*?)\](.*?)\[\/quote\1?\]/mi,
        '<div class="quote"><p><cite>\2</cite></p><blockquote>\3</blockquote></div>',
        'Quote with citation',
        nil, nil,
        :quote],      
    }
 
    text.bbcode_to_html(my_blockquote)


## Developers

* [Fernando Blat](http://github.com/ferblape)
* [Craig P Jolicoeur](http://github.com/cpjolicoeur)


## License

Copyright (c) 2008 Craig P Jolicoeur, Fernando Blat

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


## Acknowledgements

* [ruby-bbcode project](http://code.google.com/p/ruby-bbcode/)
* [Nazgum's Blog](http://www.nazgum.com/2008/01/08/bbcode-with-ruby-on-rails-part-1/)


## TODO
