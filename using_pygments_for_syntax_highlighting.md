In a [previous post](http://philwade.org/post/rockin_the_alpha_version/) I
talked a bit about trying to get syntax highlighting working properly in blog
posts. I said something or other about it being more difficult than all the
implementations available would imply, but it turns out its (as suspected)
just as simple as I thought it might be. The real issue was that it didn't
work the way I wanted it to. So I slapped together two other implementations
with features I liked. I've lost the links to those (sorry anonymous other
programmers).

  
My version requires [Beautiful
Soup](http://www.crummy.com/software/BeautifulSoup/) and
[Pygments](http://pygments.org/) and combines two features that I liked in
other versions - automatically including the relevant stylesheets (cause I
don't want to write my own) and understanding the code language based on the
class of the page element (because using the lexer to automatically figure out
the code is a crappy method).

  
Anywho, here is the code: ` from django import template from BeautifulSoup
import BeautifulSoup import pygments import pygments.lexers as lexers import
pygments.formatters as formatters register = template.Library()
@register.filter(name='pygmentize') def pygmentize(value): try: formatter =
formatters.HtmlFormatter(style='trac') tree = BeautifulSoup(value) for code in
tree.findAll('code'): if not code['class']: code['class'] = 'text' lexer =
lexers.get_lexer_by_name(code['class']) new_content =
pygments.highlight(code.decodeContents(), lexer, formatter) new_content += u""
% formatter.get_style_defs('.highlight') code.replaceWith ( "%s\n" %
new_content ) content = str(tree) return content except KeyError: return value
`

  
Used like so in a template: ` {{ value|pygmentize }} ` If you need some
instructions for putting that in place, the django book [has some
pointers](http://www.djangobook.com/en/2.0/chapter09/)

  
Anywho, back to trying to solve the rubik's cube.

