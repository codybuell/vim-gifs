Vim Gifs
========

A collection of gifs on how to use vim.

Recording
---------

- new terminal
  - window 30 x 90
  - no transparency
  - source code pro 11pt

- tomorrow-night base16 theme (terminal and vim)
- startup tmux

        tmux new -A -s "gifcast" "tmux new-window 'bash -i'
        tmux send-keys 'watch -t -n 60 echo' Enter
        tmux split -v -p 100
        tmux split -v -l 3
        tmux send-keys 'watch -t -n 60 echo' Enter
        tmux selectp -t 2
        tmux set pane-active-border-fg '#333333'"

- startup visualize
  - disable mouse clicks
  - fade in: 0.5
  - remain for: 2.0
  - fade out: 0.5
  - display area fully transparent
  - source code pro 35pt #939393
  - position 0,0
  - size 640 x 100

- startup screenflow

Editing
-------

- crop to 640x480
- export mp4 100% size and use motion blur
- convert to gif

        ffmpeg -v warning -i recording.mp4 -vf 'setpts=0.50*PTS,fps=30,scale=640:-1:flags=lanczos,palettegen=stats_mode=diff' -y /tmp/palette.png
        ffmpeg -v warning -i recording.mp4 -i /tmp/palette.png -lavfi 'setpts=0.50*PTS,fps=30,scale=640:-1:flags=lanczos [x]; [x][1:v] paletteuse=dither=floyd_steinberg' -y /tmp/rawgif.gif
        gifsicle --optimize=3 --delay=3 < /tmp/rawgif.gif > recording.gif
