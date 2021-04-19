## Bash
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
- Match command-line arguments to their help text: [explainshell](https://explainshell.com)
- List sizes of current directory recursively:  
`du -hs *`