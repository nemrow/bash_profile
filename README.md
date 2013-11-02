export PATH=/usr/local/bin:$PATH
export DYLD_FALLBACK_LIBRARY_PATH=/Applications/Postgres.app/Contents/MacOS/lib:$DYLD_LIBRARY_PATH
source ~/.bashrc

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

alias nemrow='cd Dropbox/Foxes/Jordan\ Nemrow/Phase_3/'
alias dev='cd Dropbox/Dev/'
alias dbreset='rake db:drop && rake db:create && rake db:migrate && rake db:test:prepare'
alias cuc='cucumber'

c_cyan=`tput setaf 6`
  c_red=`tput setaf 1`
  c_green=`tput setaf 2`
  c_sgr0=`tput sgr0`
  
  
   
  parse_git_branch ()
  {
    if git rev-parse --git-dir >/dev/null 2>&1
    then
            gitver=$(git branch 2>/dev/null| sed -n '/^\*/s/^\* //p')
    else
            return 0
    fi
    echo -e $gitver
  }
  
  branch_color ()
  {
          if git rev-parse --git-dir >/dev/null 2>&1
          then
                  color=""
                  if git diff --quiet 2>/dev/null >&2 
                  then
                          color="${c_green}"
                  else
                          color=${c_red}
                  fi
          else
                  return 0
          fi
          echo -ne $color
  }
  
  PS1='[\[$(branch_color)\]$(parse_git_branch)\[${c_sgr0}\]]\[${c_cyan}\]\W\[${c_sgr0}\]: '
