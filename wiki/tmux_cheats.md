# tmux

## Execution
~~~~
> tmux
~~~~

## Prefix change
~~~~~
: set-option -g prefix C-a
~~~~~
    
## mouse on
~~~~
: set -g mouse on
: set -g history-limit 100000
~~~~

## basic

|key|description|
|:---:|:------------|
|prefix + c|Create new window|
|prefix + n|Right window|
|prefix + SPACE|Right window|
|prefix + p|Left window|
|prefix + C-a|Previous window|
|prefix + 0~9|Select window|
|prefix + d|Detach client|
|prefix + s|Choose tree|
|prefix + '|Choose window by index|
|prefix + w|Choose window|
|prefix + r|Reload .tmux.conf file|

* User defined

|key|description|
|:---:|:------------|
|prefix + C-h|Select left window (can be repeated)|
|prefix + C-l|Select right window (can be repeated)|
|prefix + e|Edit current .tmux.conf file|

## pane

|key|description|
|:---:|:------------|
|prefix + %/v|Split window in vertical|
|prefix + "/b|Split window in horizontal|
|prefix + h/j/k/l|Move to pane|
|prefix + o|Rotate pane|
|prefix + q|Display panes|
|prefix + {/}|Swap pane|
|prefix + Q|Enter key to all panes|

### resize-pane

All operations are executed for right, under pane boundaries except the last pane.

~~~~
:resize-pane -U [N]
~~~~
if lowest pane, move upper boundary of current pane 1 or N upward.<br/>
if not lowest pane, move lower boundary of current pane 1 or N upward.

~~~~
:resize-pane -D [N]
~~~~
if lowest pane, move upper boundary of current pane 1 or N downward.<br/>
if not lowest pane, move lower boundary of current pane 1 or N downward.

~~~~
:resize-pane -L [N]
~~~~
if rightest pane, move left boundary of current pane 1 or N leftward.<br/>
if not rightest pane, move right boundary of current pane 1 or N leftward.

~~~~
:resize-pane -R [N]
~~~~
if rightest pane, move left boundary of current pane 1 or N rightward.<br/>
if not rightest pane, move right boundary of current pane 1 or N rightward.


## misc

|key|description|
|:---:|:------------|
|prefix + :|Command prompt|
|prefix + #|List buffer|
|prefix + ]|Pase buffer|
|prefix + t|Show time|

~~~~
mouse drag --> tmux buffer
ctrl + mouse drag --> conventional copy
ctrl + mouse center click --> conventional paste
~~~~

## current .tmux.conf file

~~~~
set-option -g prefix C-a

bind-key C-a last-window
# Set status bar
set -g status-bg black
set -g status-fg white
set -g status-left '#[fg=green]#H'

# Highlight active window
set-window-option -g window-status-current-bg red

#set -g status-right '#[fg=yellow]#(uptime | cut -d "," -f 2-)'
set -g status-right '#[fg=yellow]#(date)'



bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

set -g default-terminal "xterm-256color"

# set window split
bind-key v split-window -h
bind-key b split-window

# title
bind-key A command-prompt "rename-window %%"

# default window title colors
set-window-option -g window-status-fg colour244 #base0
set-window-option -g window-status-bg default
#set-window-option -g window-status-attr dim

# active window title colors
set-window-option -g window-status-current-fg colour166 #orange
set-window-option -g window-status-current-bg default
#set-window-option -g window-status-current-attr bright

# pane border
set-option -g pane-border-fg colour235 #base02
set-option -g pane-active-border-fg colour240 #base01

# message text
set-option -g message-bg colour235 #base02
set-option -g message-fg colour166 #orange

# Start numbering at 1
set -g base-index 1

# reload config
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."                                                                     
bind e send-keys -t : vi Space ~/.tmux.conf Enter

#bind-key Space next-layout
bind-key Space next-window

#bind for windows change without C-a except the first one
bind -r C-h select-window -t :-
bind -r C-l select-window -t :+

#bind-key w list-buffers

#mouse
set -g mouse on
set -g history-limit 100000

#synchronized pane input mode
bind Q setw synchronize-panes
~~~~
