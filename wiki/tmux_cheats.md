# tmux

## Execution
    > tmux

## Prefix change
    : set-option -g prefix C-a
    
## mouse on
    : set -g mouse on
    : set -g history-limit 100000

## basic
| key | description |
|:---:|:------------|
| prefix + c | Create new window |
| prefix + n | Right window |
| prefix + SPACE | Right window |
| prefix + p | Left window |
| prefix + C-a | Previous window |
| prefix + 0~9 | Select window |
| prefix + d | Detach client |
| prefix + s | Choose tree |
| prefix + w | Choose tree |
|==========

| 헤더1 | 헤더2 |
|:--------|:--------|
| 컬럼1   | 컬럼2   |
| 컬럼4   | 컬럼5   |
| 컬럼1   | 컬럼2   |
|=====


| Foot1   | Foot2   |

## pane
|key|description|
|:-:|:---|
|prefix + %/v|Split window in vertical|
|prefix + "/b|Split window in horizontal|
|prefix + h/j/k/l|Move to pane|
|prefix + o|Rotate pane|
|prefix + q|Display panes|
|prefix + {/}|Swap pane|
|prefix + Q|Enter key to all panes|
|===========


## misc
|key|description|
|:-:|---|
|prefix + :|Command prompt|
|prefix + #|List buffer|
|prefix + ]|Pase buffer|
|============

    mouse drag --> tmux buffer
    ctrl + mouse drag --> conventional copy
    ctrl + mouse center click --> conventional paste

