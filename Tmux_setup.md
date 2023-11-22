# Download tmux Copy over tmux plugins to home dir

`sudo apt install tmux`
`git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`

# Next, create a .tmux.conf file in the home directory

`touch .tmux.conf`

# The config file should have the following contents:
```bash
  #Change the prefix key to C-a
  set -g prefix C-a
  unbind C-b
  bind C-a send-prefix
  
  #Turn the mouse on, but without copy mode dragging
  set -g mouse on
  set -g @yank_with_mouse on
  #unbind -n MouseDrag1Pane
  #unbind -Tcopy-mode MouseDrag1Pane
  bind -T copy-mode    C-c send -X copy-pipe-no-clear "xsel -i --clipboard"
  bind -T copy-mode-vi C-c send -X copy-pipe-no-clear "xsel -i --clipboard"
  
  
  #List of plugins
  
  set -g @plugin 'tmux-plugins/tpm'
  set -g @plugin 'tmux-plugins/tmux-sensible'
  set -g @plugin 'tmux-plugins/tmux-logging'
  set -g @plugin 'tmux-plugins/tmux-resurrect'
  set -g @plugin 'tmux-plugins/tmux-yank'
  #set -g @yank_action 'copy-pipe-no-clear'
  
  #Initialize TMUX plugin manager (keep at bottom)
  run '~/.tmux/plugins/tpm/tpm'
```

# Enable the source settings
tmux source ~/.tmux.conf
