Selection Sorter
================

Did you ever want to sort some class members via their names, easily, or a number of lines via a string in the middle? Well, now you can.

This plugin enables you to sort lines by the text you have currently selected.

Default Commands
----------------

It ships with two commands you can find in the command palette:

 - Sort Lines by Selection
 - Sort Lines by Selection (Case Sensitive)

Customization
-------------

The plugin supports custom morphing of the selected strings before sorting, via little python snippets.
For example you could reverse the string which is used for sorting, sort via the last character, only via the first etc..

You can make your custom sort available by creating a `Default.sublime-commands` file in your `packages/user` folder, or alternatively a keybinding which executes the command.

**Example**

Here a little example for a custom line sort:

*Default.sublime-commands*
````json
    [
        {
            "caption": "Sort Lines by Selection",
            "command": "sort_lines_by_selection",
            "args": {
                "morph": "s[::-1]" // This will reverse the string
            }
        }
    ]
````

As you can see I reference a variable `s` (a string) and reverse it. This would sort the lines by the reversed selection. So a line with a selection of "AZZZZ" would be at the bottom, rather than at the top.

Note however that only a single statement is allowed, otherwise your custom *morph* will not work.

Technically speaking the *morph* argument is the "body" of a python lambda, and will be used as the *key* argument of the built-in *sorted* function.

Happy sorting!