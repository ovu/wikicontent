Tmux powerline configuration on MAC OS
=============================
First follow all the steps described in the documentation from powerline.

https://powerline.readthedocs.org/en/latest/installation/osx.html

Besides the configuration from the documentation execute the following commands.

It worked in Yosemite with Terminal and iTerm2.

1. Set the locale in the commandline or in your .profile

export LC_ALL=en_US.UTF-8

export LANG=en_US.UTF-8

2. Install psutil (required for the system uptime information)
sudo pip install psutil

3. Window automation

Executing command on a session an window:
  tmux send-keys -t <session_name>:1 C-c "git checkout master" Enter "git pull" Enter vim Enter


Getting the process running in a pane:

  tmux list-panes -t <session_name>:1  -F '#{pane_active} #{pane_pid}'

Getting the child process of a process:
  pgrep -P 46677
