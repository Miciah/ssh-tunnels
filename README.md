# SSH tunnels

This package lets you run and kill SSH tunnels.  To use it:

- Set the variable `ssh-tunnels-configurations`, e.g.:

```emacs-lisp
(setq ssh-tunnels-configurations
      '((:name "my tunnel"
         :local-port 1234
         :remote-port 3306
         :login "me@host")))
```

- Type `M-x ssh-tunnels RET`

- You should see the list of tunnels; running tunnels will have 'R'
  in their state column

- To run the tunnel at the current line, type `r`

- To kill a running tunnel, type `k`

- You may want to temporarily change a tunnel's local port.  To do
  that you may provide a prefix argument to the run command, for
  example by typing `C-u 1235 r`
  
## Auto-ssh-tunnels-mode

This package also includes a global minor-mode that automatically
starts SSH tunnels when Emacs's built-in `open-network-stream`
function is used.  This mode checks whether a new connection is to
localhost and to a port for which `ssh-tunnels-configurations` has a
tunnel with a matching local port, and if so, makes sure that the
tunnel is running.

Use `M-x auto-ssh-tunnels-mode` to enable this global minor-mode.

# License

MIT
