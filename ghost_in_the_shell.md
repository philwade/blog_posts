I recently needed to create eight Symfony templates for something at work.
Quick breakdown: every page in Symfony is a combination of an action and a
template. You create a function and follow a naming convention to create the
corresponding template. So, the action "public function executeFoobar()"
renders with the template "foorbarSuccess.php". It's a bit more complicated
than that, but that's all you really need to know at the moment.

  
I had written this set of eight actions, and wanted to create all the
templates. Normally, I just create the files by hand, but that's boring. The
correct answer? Shell script.

` [web@dnysnweb05:~/htdocs_symfony/symfony/apps/content/modules/minisites]$
grep Pretty ../actions/actions.class.php | awk '{ print $3 }' | sed
s/\(.*\/Success\.php/g | sed s/execute//g | sed s/P/p/ | awk '{ system("touch
" $1) }' `

Instead of writing "touch blahfile.php" eight times, I wrote the above. It
probably took three times as long, but it was a hundred times as much fun, and
if I had needed to create a thousand templates, it would have saved me a lot
of time. The moral of the story is keep sharp in the shell. It might come in
handy.

