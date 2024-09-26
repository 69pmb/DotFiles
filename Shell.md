# Shell

- [Shell Style guide](https://google.github.io/styleguide/shellguide.html)
- [ShellCheck](https://www.shellcheck.net) => finds bugs in your shell scripts
- Match command-line arguments to their help text => [explainshell](https://explainshell.com)
- Replaces last digit of given software version by a 'x':  
`echo "5.6.3" | grep -Eoh "[0-9+\.]+\." | xargs -I % echo "%x"`
- Converts all files to Unix line endings:  
`find . -type f -print0 | xargs -0 dos2unix`
- Kills all occurency of searched entry:  
`ps aw | grep <pgm> | grep -v 'grep' | cut -d '?' -f1 | xargs kill -9`
- To create a compressed file:  
`tar -cvzf *filename.tar.gz <directory/*>`
- To extract the contents of a file:  
`tar -xvzf <filename.tar.gz>`
- Adds execute permission for the owner of the file:  
`chmod u+x <file>`
- List sizes of current directory recursively:  
`du -hs *`
- Status of last command ('0' => OK, '1' => KO):  
`echo $?`
- Loop over array to curl:  
`echo -e '27037\n80709\n80730\n80710\n80731' | xargs -I % curl -s -H "PRIVATE-TOKEN: my_token" "https://gitlab.com/api/v4/groups/%/projects" | jq '.[].id' | xargs -I % my_command`
- Recover multiple fields with _jq_:  
`jq -r '.[] | [.id, .name]'`
