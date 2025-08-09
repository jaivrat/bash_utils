# Common BASH settings on all my machines
1. Go to new machine's github folder. Create if it does not exist
```
cd /home/jvsingh/work/github
```

2. Clone this repo
```
git clone git@github.com:jaivrat/bash_utils.git

```


3. In your .bashrc, add these lines
```
# Source all my utils from common utility I wrote for all machines
# Source shared bash utilities if available
# Auto-update utilities (optional, might slow login)
GIT_BASH_UTILS="$HOME/work/github/bash-utils"
UTIL_BASHRC="$GIT_BASH_UTILS/.util_bashrc"
if [ -d $GIT_BASH_UTILS ]; then
    cd $GIT_BASH_UTILS && git pull --quiet ||  echo "Warning: Could not update $GIT_BASH_UTILS"
    if [ -f "$UTIL_BASHRC" ]; then
        source "$UTIL_BASHRC"
    else
        echo "Warning: $UTIL_BASHRC not found!"
    fi
else
    echo "Error : Your $GIT_BASH_UTILS directory not found!"
fi
```
