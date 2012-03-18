I've been trying to write about something (anything really) at least once a
week. Last week I failed at this for a variety of reasons, and the week before
I wrote a draft of a recipe post for my (and my girlfriend's) other blog,
[Usversusdinner.com](http://www.usversusdinner.com), which is about our
cooking adventures. I'll post that once I get it edited and put some pictures
into it. This week, I'm getting right back on the horse with this post.

  
I'm a big fan of [Penny Arcade](http://www.penny-arcade.com), and about a
month ago, the [news post](http://penny-arcade.com/2011/10/12) was written by
a game developer who also happened to be an expert in cryptography. In the
post, she included two blocks of numbers: "28-1 10-2 10-3 6-4 18-4 43-1 36-3
9-2 43-4 32-9 41-2 1-1 2-1 45-1 42-3 33-2 3-4" and "42-4 14-2 26-1 32-10 35-3
54-3 56-1 3-3".

  
I was curious about these, so I did a bit of poking around and discovered that
they were the cipher text produced by a type of [Book
Cipher](http://en.wikipedia.org/wiki/Book_cipher). You, much like myself
before this exercise, may not be familiar with a book cipher. Simply put, a
book cipher relies on an existing piece of text, usually a book (go figure),
as a key for decoding a message. The coding of the message often isn't complex
- usually numbers refer to words in the key text. The obscurity of the cipher
comes more from knowing what the key text is, less from the complexity of the
code.

  
Every news post on Penny Arcade accompanies a given comic, so it isn't
terribly difficult to guess what the key text for this particular cipher text
is (it is [this comic](http://penny-arcade.com/comic/2011/10/12)).

  
In this instance, the way the message is coded is "word number-word letter". I
was curious what the message was, so I started to counting through the words
and then counting through the letters. As it turns out, this is an incredibly
dull, slow, and completely unrewarding process. In the past, this was no doubt
was a "security feature" of this type of cipher.

  
Fortunately for me, we live in a world filled with computers, and computers
are great at this type of thing. I whipped up a little program in python that
de-crypted the text in almost no time. The longest part of the coding session
may have been transcribing the text of the comic.

  
` base_cipher = "28-1 10-2 10-3 6-4 18-4 43-1 36-3 9-2 43-4 32-9 41-2 1-1 2-1
45-1 42-3 33-2 3-4 42-4 14-2 26-1 32-10 35-3 54-3 56-1 3-3" key_text = "Sir I
need you to turn off your my what you want me to turn off my book oh you'd
like that I bet you'd love to turn off all books wouldn'tcha yeah just \ like
hitler uh oh too far you're gonna shock my genitals huh the genital region I
think we might start there yeah" code = base_cipher.split(' ') key =
key_text.split(' ') for i in code: parts = i.split('-') index = int(parts[0])
- 1 print key[index][int(parts[1]) - 1] `

  
It's quite simple thanks to the way that python keys strings just like arrays.
I've considered trying to re-write it as a one liner, but it didn't seem like
a good use of time.

  
I split both the cipher text and the key up by spaces, and then cycle through
each word-letter pair of the cipher. I split those by the dash, and then use
the word part of the pair to grab the right word, and the letter part of the
pair to grab the write letter from that word. There is also the subtract by
one to compensate for the cipher using an index that starts with one and
python using an index that starts with zero. Easy stuff.

  
You can grab the code if you like from [my bitbucket
account.](https://bitbucket.org/pivotal/pa_cipher) I won't say what the
message is, but it actually isn't very interesting. No worry though, as I had
a great time finding it. I've found that with most worthwhile pursuits, the
fun isn't in the destination as much as it is in the journey. Enjoy!

