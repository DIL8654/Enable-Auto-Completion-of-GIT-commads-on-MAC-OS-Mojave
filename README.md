## Enable Auto Completion of GIT commands on MAC-OS Mojave 10.14

I am a developer and  use git from the command line all of the time. When I consider development perspective, I used to execute lot of commands using commandline for GIT operations. Most of the time it is very annoing that MAC OS dont have automatically support for the command completion which I partialy support. as well as the command suggesions, which means what are the commands available for typed characters. So it is very troublesome to type very long command and mostly repitive task as typo going wrong. :(

Tab completion would certainly be faster and easier. Unfortunately, the default installation of git on some Mac computers doesn not have tab completion enabled.

So that I was searching for fix for the problem and thare are several solutions found from the web search such as stackoverflow, github as well as from the medium. Unfortunately those solutions did not work for me and got frustrated with trying different solutions so many times.

I was searching deeply and trying out different solutions and fortunately it is an easy fix. Below are the steps I have collect from the several posts and finally it worked as expected. So I hope to share with others who have this problem as me.

1. If you go to the web search and you can find many solutions which mentioned about the git completion bash file. Even github guide as well. But I suggest you to check first if the git-completion.bash file is already in you MAC computer with the git-core or something else which came from installation. you can use below command.
    ```
    sudo find / -type f -name "git-completion.bash"
    ```
    you will get below results. (may have some difference according to the content)
    ```
    /Library/Developer/CommandLineTools/usr/share/git-core/git-completion.bash
    /Users/Dilanka/git-completion.bash
    /Users/Dilanka/.oh-my-zsh/plugins/gitfast/git-completion.bash
    /Users/Dilanka/Downloads/git-completion.bash
    ```
    I suggest you to pick which installed from git-core
2. If the git-completion.bash script doesn’t exist on your machine, please retrieve it from the below provided above and save it to your local machine in a new file called git-completion.bash in the /usr/local/etc/bash_completion.d/ directory.

    https://git-scm.com/book/en/v1/Git-Basics-Tips-and-Tricks
    
    If you use the Bash shell, Git comes with a nice auto-completion script you can enable. Download it directly from the Git source code at https://github.com/git/git/blob/master/contrib/completion/git-completion.bash
    
3. If the git-completion.bash script exists on your machine, but is not in the /usr/local/etc/bash_completion.d/ directory, you should create that directory and copy the file into it. Below command will do the job:
    ```
    sudo mkdir /opt/local/etc/bash_completion.d
    sudo cp /Library/Developer/CommandLineTools/usr/share/git-core/git-completion.bash /usr/local/etc/bash_completion.d/git-completion.bash
    ```

4. After the completion of step 3. The git-completion.bash script should exist on your local machine in the/usr/local/etc/bash_completion.d/ directory.

5. Now you need to refresh your profile using below command. It will load your added bash file to the terminal context.
    ```
    source ~/.bash_profile
    ```
Great!!! you have done it. Just start the terminal window and try it. Just type "git sta" it will show suggesions as below:

    ```
    git sta
    stage    stash    status
    
    git chec<TAB> will show git checkout
    
    ```

