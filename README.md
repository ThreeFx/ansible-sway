sway
=========

Ansible role to set up and install sway.

Requirements
------------

On Debian sway is only packaged in experimental (as of 18-12-2019). You have to ensure that
experimental packages are enabled on your system, for example using [my apt role](https://github.com/ThreeFx/ansible-apt).

Role Variables
--------------


| Variable Name | Default Value | Description |
--------------- |---------------|--------------
`sway_terminal_emulator` | "x-terminal-emulator" | Terminal emulator to use
`sway_full_config` | "" | An entire sway config. If you specify this, then no other configuration will be applied.  
`sway_extra_config_early` | "" | optional, additional config to append before autostarting and keybindings
`sway_autostart_programs` | [] | list of programs to start when starting sway (see `defaults/main.yml` for more information)
`sway_keybinding_reload` | "$mod+Shift+c" | Default reload keybinding
`sway_keybinding_kill` | "$mod+Shift+q" | Default kill keybinding
`sway_keybinding_fullscreen` | "$mod+f" | Default fullscreen keybinding
`sway_keybinding_exit` | "$mod+Shift+e" | Default exit keybinding
`sway_keybindings` | [] | extra keybindings to configure, see `defaults/main.yml` for more information.
`sway_extra_config_late` | "" | optional, additional config to append after all config before

Dependencies
------------

My [apt role](https://github.com/ThreeFx/apt) may be useful in configuring and pinning experimental packages.

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: sway
           sway_keybindings:
             - key: "$mod+t"
               action: "/usr/bin/telegram-start"
           sway_extra_config_late: |
               output * {
                   eDP-1 0 0
                   DP-1 0 1080
               }

License
-------

BSD

Author Information
------------------

Find me on [GitHub](https://github.com/ThreeFx).
