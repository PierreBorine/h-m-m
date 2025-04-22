
# h-m-m (hackers mind map)

**h-m-m** (pronounced like the interjection "hmm") is a simple, fast, keyboard-centric terminal-based tool for working with mind maps. 

![screenshot](screenshot.png)


# Default key bindings

Adding, removing, and editing nodes:

* `o` or `Enter` - create a new sibling to the active node
* `O` or `Tab` - create a new child for the active node
* `y` - yanks (copies) the active node and its descendants
* `Y` - yanks (copies) the descendants of the active node
* `d` - deletes (cuts) the active node and its descendants
* `D` - deletes (cuts) the descendants of the active node
* `Delete` - deletes the active node and its descendants without putting them in the clipboard 
* `p` - pastes as descendants of the active node
* `P` - pastes as siblings of the active node 
* `Ctrl+p` - appends the clipboard text at the end of the active node's title
* `e`, `i`, or `a` - edits the active node
* `E`, `I`, or `A` - edits the active node, ignoring the existing text
* `u` - undo

Marks:

* `t` - toggles '✓ ', '✗ ', and '' (or your custom symbols) at the beginning of the title
* `#` - adds or removes sequential numbers at the beginning of the titles of a node and its siblings
* `=` - increases the positive ranking
* `+` - decreases the positive ranking
* `-` - increases the negative ranking
* `_` - decreases the negative ranking
* `alt+up` - adds a star
* `alt+down` - removes a star
* `H` - toggles the hidden flag

Relative navigating and moving:

* `h` or `←` - activates the parent of the previously active node
* `l` or `→` - activates the middle child of the previously active node
* `j` or `↓` - activates the lower sibling (or the nearest lower node if there's no lower sibling)
* `k` or `↑` - activates the higher sibling (or the nearest higher node if there's no higher sibling)
* `J` - moves the current node down among its siblings
* `K` - moves the current node up among its siblings
* `T` - sorts the siblings of the active node

Adjusting the view:

* `c` - centers the active node on the screen
* `C` - locks/unlocks active nodes on the center 
* `~` or `m` - activate the root element
* `g` - goes to the highest element
* `G` - goes to the lowest element
* `w` - increases the maximum node width
* `W` - decreases the maximum node width
* `z` - decreases line spacing
* `Z` - increases line spacing 
* `|` - enables/disables aligned levels
* `ctrl+h` - hides/views hidden nodes

Collapsing and expanding:

* `Space` - toggles the active node
* `v` - collapses everything other than the first-level nodes
* `V` - collapses all the children of the active node
* `b` - expands all nodes
* `1` to `9` - collapse the nth level and expand those before
* `f` - focuses by collapsing all, but the ancestors and descendants of the active node
* `F` - locks focus as the active node changes (try it with the center lock)
* `r` - collapses all the first level items except for the one that contains the active node
* `R` - collapses the children of the active node

Search:

* `/` or `Ctrl+f` - searches for a phrase
* `n` - goes to the next search result
* `N` - goes to the previous search result

Save, export, quit, etc.:

* `s` - saves with the previous file name (or asks for one if there's none)
* `S` - saves with a new file name
* `x` - export as an HTML file
* `X` - export as a text map into clipboard
* `q` - quits (if the changes were already saved)
* `Q` - quits, ignoring the changes
* `Ctrl+o` - open the active node as a file or URL using xdg-open

Misc:

* `?` - show the key bindings

In the text editor:

* `↓` - moves the cursor to the end of the line
* `↑` - moves the cursor to the beginning of the line
* `←` or `Home` - moves the cursor to the left
* `→` or `End` - moves the cursor to the right
* `Ctrl+Left` or `Shift+Left` - moves cursor to the previous word
* `Ctrl+Right` or `Shift+right` - moves cursor to the next word
* `Delete` - deletes character
* `Ctrl+Delete` - deletes word
* `Backspace` - deletes previous character
* `ctrl+Backspace`, `ctrl+w` - deletes previous word
* `Ctrl+v` or `Ctrl+Shift+v` - paste
* `Esc` - cancels editing
* `Enter` - wanna guess? ;)

Other than the text editor key bindings, you can change all in your config file.


## Rankings

When working with a group of people in a workshop, sometimes you need to decide on a subtopic (i.e., selecting one of the proposed items). After discussing them, people can vote "yes" or "no" for each item. You can add a positive point for each "yes" (`=`) and a negative one for each "no" (`-`). In the end, you can press shift+t to sort them and see the highest-ranking choices on the top.

Another way of ranking is to use stars. To do so, you can press `alt+up` or `alt+down` to add or remove stars and show a zero to five rank.


# Configuration 

The following are the settings in h-m-m:

    max_parent_node_width = 25
    max_leaf_node_width = 55
    line_spacing = 1
	align_levels = 0
    initial_depth = 1
	center_lock = false
	focus_lock = false
	max_undo_steps = 24
    active_node_color = \033[38;5;0m\033[48;5;172m\033[1m
    message_color = \033[38;5;0m\033[48;5;141m\033[1m
	clipboard = os
	clipboard_file = /tmp/h-m-m
	clipboard_in_command = ""
	clipboard_out_command = ""
	post_export_command = ""
	symbol1 = ✓
	symbol2 = ✗
	auto_save = false

The colors are ASCII escape codes. 

You can also change key bindings with a `bind x = command` syntax. The following are the defaults:

    bind   a                  =   edit_node_append
    bind   A                  =   edit_node_replace
    bind   b                  =   expand_all
    bind   c                  =   center_active_node
    bind   C                  =   toggle_center_lock
    bind   ctrl_c             =   quit
    bind   d                  =   delete_node
    bind   D                  =   delete_children
    bind   del                =   delete_node_without_clipboard
    bind   e                  =   edit_node_append
    bind   E                  =   edit_node_replace
    bind   f                  =   focus
    bind   F                  =   toggle_focus_lock
    bind   g                  =   go_to_top
    bind   G                  =   go_to_bottom
    bind   h                  =   go_left
    bind   H                  =   toggle_hide
    bind   ctrl_h             =   toggle_show_hidden
    bind   i                  =   edit_node_append
    bind   I                  =   edit_node_replace
    bind   j                  =   go_down
    bind   J                  =   move_node_down
    bind   k                  =   go_up
    bind   K                  =   move_node_up
    bind   l                  =   go_right
    bind   m                  =   go_to_root
    bind   ~                  =   go_to_root
    bind   n                  =   next_search_result
    bind   N                  =   previous_search_result
    bind   o                  =   insert_new_sibling
    bind   O                  =   insert_new_child
    bind   ctrl_o             =   open_link
    bind   p                  =   paste_as_children
    bind   P                  =   paste_as_siblings
    bind   ctrl_p             =   append
    bind   q                  =   quit
    bind   Q                  =   shutdown
    bind   ctrl_q             =   quit_with_debug
    bind   r                  =   collapse_other_branches
    bind   R                  =   collapse_inner
    bind   s                  =   save
    bind   S                  =   save_as
    bind   t                  =   toggle_symbol
    bind   T                  =   sort_siblings
    bind   #                  =   toggle_numbers
    bind   u                  =   undo
    bind   v                  =   collapse_all
    bind   V                  =   collapse_children
    bind   w                  =   increase_text_width
    bind   W                  =   decrease_text_width
    bind   x                  =   export_html
    bind   X                  =   export_text
    bind   y                  =   yank_node
    bind   Y                  =   yank_children
    bind   z                  =   decrease_line_spacing
    bind   Z                  =   increase_line_spacing
    bind   enter              =   insert_new_sibling
    bind   tab                =   insert_new_child
    bind   space              =   toggle_node
    bind   arr_down           =   go_down
    bind   arr_up             =   go_up
    bind   arr_right          =   go_right
    bind   arr_left           =   go_left
    bind   alt_arr_up         =   add_star
    bind   alt_arr_down       =   remove_star
    bind   1                  =   collapse_level_1
    bind   2                  =   collapse_level_2
    bind   3                  =   collapse_level_3
    bind   4                  =   collapse_level_4
    bind   5                  =   collapse_level_5
    bind   6                  =   collapse_level_6
    bind   7                  =   collapse_level_7
    bind   8                  =   collapse_level_8
    bind   9                  =   collapse_level_9
    bind   |                  =   toggle_align
    bind   ?                  =   help
    bind   /                  =   search
    bind   ctrl_f             =   search
    bind   equal              =   increase_positive_rank
    bind   +                  =   decrease_positive_rank
    bind   -                  =   increase_negative_rank
    bind   _                  =   decrease_negative_rank

Keys can be `x`, `X` (shift+x), `ctrl_x`, `alt_x`, or special keys: `arr_down`, `arr_left`, `arr_right`, `arr_up`, `back_space`, `ctrl_arr_left`, `ctrl_arr_right`, `ctrl_back_space`, `ctrl_del`, `del`, `end`, `enter`, `equal`, `esc`, `home`, `shift_arr_left`, `shift_arr_right`, `space`, `tab` 

Note: Not every possible key is defined because I'm going to replace this whole system with one that supports key sequences.

Key bindings can only be set in a config file. There are 3 ways of changing settings:

1. Pass them as arguments when running the program; e.g., `h-m-m --focus-lock=true --line-spacing=0 filename`
1. Set them as environment variables with `hmm_` as prefix; e.g., `hmm_line_spacing=0`
1. Store them in a config file. You can pass the location of the config file when running the application like `h-m-m --config=/path/file`, or use the default location:
   * Linux: ~/.config/h-m-m/h-m-m.conf
   * Mac: ~/Library/Preferences/h-m-m/h-m-m.conf
   * Windows: an h-m-m.conf file in the same directory as the script

Both underscores and dashes are accepted for the setting keys.

When multiple values exist, the highest priority goes to the command line arguments and the lowest to the config file. 


# Clipboard

The normal `os` clipboard works fine for most users, but some users may need other options:

* `--clipboard=os` uses the global clipboard via xclip and similar tools.
* `--clipboard=internal` uses an internal variable as the clipboard (won't exchange text with external applications).
* `--clipboard=file` uses `/tmp/h-m-m` by default, or another file set by the `--clipboard_file=/path/filename` setting as the clipboard.
* `--clipboard=command` uses `--clipboard_in_command="command %text%"` to send content to a shell command and `--clipboard_out_command="command"` to read content.


# Exporting

You can export an HTML version of the map using the `x` key binding. This is useful for sending the file to someone who may not have h-m-m or a similar mind mapping application. To make the process easier, you can set a sell command to run after exporting the map; e.g., upload it to a server and copy the link to clipboard: `--post-export-command="upload.sh %filename% &>/dev/null"`.


# Data format

Mind maps are stored in plain text files (with `hmm` file extension by default) without metadata. The tree structure is represented by tab indentations; e.g., 

    root (level 0)
       item A (level 1)
       item B (level 1)
          item Ba (level 2)
          item Bb (level 2)
          item Bc (level 2)
             item BaX (level 3)
             item BaY (level 3)
          item Bd (level 2)
       item C (level 1)

When you yank (copy) or delete (cut) a subtree, the data will be put into your clipboard with a similar structure, and when pasting, the data will be interpreted as such. 

Most mind mapping applications use a similar format for copying and pasting. As a result, if you want to import a map from another application, you can probably select everything in that application, copy it, come to **h-m-m**, and paste it. The same usually works well when copying from HTML/PDF/Doc lists, spreadsheets (e.g., Calc and Excel), etc.


# Installing 

Note: A few issues should be solved before **h-m-m** can be run in Windows. Until then, Windows users can probably use *Windows Subsystem for Linux* to run it.


## 1. Manual installation 

**h-m-m** is a single php file. You can download it from here, or clone it on your computer using git and add a scheduled job to update it once a day or week. 

You also need to have the following installed for h-m-m to work:

* php
  * either php 8, or
  * older versions of php along with the `mbstring` package (e.g., `php7.2-mbstring`)
* `xclip`, `xsel`, `wl-clipboard`, or `klipper` in Linux. (Windows and Mac don't need it)

After downloading or cloning, you can run `php h-m-m` in your terminal to run the program with a blank map or `php h-m-m filename` to open an existing file. Note: You don't need to set up a "web server" to run it because it's not a web application, but rather a terminal application that works like those written in Python, Bash, etc. 

Optionally, you can make the file executable by running the `chmod +x h-m-m` in your terminal, and afterward, you can run it as `h-m-m filename` (assuming that **h-m-m** is in your path).


## 2. Installation for Arch Linux

In Arch Linux, you can use the `h-m-m-git` AUR package to install it.


## 3. Installation script for Linux (and Mac?)

You can run the following command to install h-m-m:

```sh
wget -q -O - 'https://raw.githubusercontent.com/nadrad/h-m-m/main/install.sh' | sh
```

This command downloads and runs the install.sh script, which in turn downloads h-m-m, copies it to `/usr/local/bin`, checks the dependencies, and makes it executable. 

After installing, you can run `h-m-m` from anywhere in your terminal to run the application with an empty map, or `h-m-m filename` to open an existing file.


## 4. Installation with Docker

It's also possible to execute `h-m-m` through docker (or podman):

```sh
# Build the image
docker build -t hmm .

# Run it (mount $pwd for file access, X11 & DISLAY for clipboard access)
docker run --rm -it -v $(pwd):/app/ -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY hmm

# Convinience
alias hmm='docker run --rm -it -v $(pwd):/app/ -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY hmm'
```

## 5. Installation with Nix/NixOS
<details>
<summary>with flakes (NixOS)</summary>

Below is a fragment of a NixOS configuration that add h-m-m to system packages.

```nix
{
  description = "Simple NixOS configurations";
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
    h-m-m = {
      url = "github:nadrad/h-m-m";
      # Optional but recommended to limit the size of your system closure.
      inputs.nixpkgs.follows = "nixpkgs";
    };
  };
  outputs = { nixpkgs, h-m-m, ... }: {
    nixosConfigurations = {
      yourHost = nixpkgs.lib.nixosSystem {
        system = "x86_64-linux";
        modules = [
          # ...
          {
            nixpkgs.overlays = [ h-m-m.overlays.default ];
          }
          # add h-m-m to your system
          ({ pkgs, ... }: {
            environment.systemPackages = [ pkgs.h-m-m ];
          });
        ];
      };
    };
  };
}
```
</details>

<details>
<summary>with <code>nix profile</code></summary>

You can also install it using the imperative method

```sh
$ nix profile install github:nadrad/h-m-m
```
</details>

<details>
<summary>with <code>nix shell</code> / <code>nix run</code></summary>

If you don't want to install it on your system, you can try it with nix run or nix shell.

```sh
$ nix run github:nadrad/h-m-m -- <args>
# or
$ nix shell github:nadrad/h-m-m
$ h-m-m <args>
```
</details>

# Feedback

Programming is not my career, but rather a hobby, and I developed **h-m-m** because I wanted to have something like this application and couldn't find one. Therefore, what I've done here may have a lot of room for improvement. If you see an embarrassing problem in the program or have an idea for improvement, feel free to contact me; I'd be happy to receive your feedback.

Why php? It's simple: I only have a rusty knowledge of Pascal and a little familiarity with php. I thought about learning another language for this project (Nim is my top choice at this moment), but I didn't have time to do it. I'll probably do it later and convert it into a language I can compile :)

