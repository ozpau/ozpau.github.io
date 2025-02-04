---
title: "Jupyter tips"
author: "Ozell Paukert"
date: "2025-02-03"
image: cover.jpg
categories: [jupyter, tips]
draft: true
---

![Public domain photo of planet Jupiter from [WikiMedia](https://commons.wikimedia.org/wiki/File:Jupiter_Showcases_Auroras,_Hazes_(NIRCam_Closeup).jpg)](cover.jpg)

A collection of Jupyter productivity tips.

## Learn keybinds
   - Press Ctrl+Shift+H to view a short summary
   - There are two edit modes in Jupyter. Text edit inside cells and cell edit.
     To leave cell edit mode, press ESC, to enter it press ENTER.
     In cell edit, you can:
     - drag cells around: Ctrl+Shift+Up/Down
     - change their type: M, Y, R
   - Global navigation (cell edit mode):
     - Space to move down, Shift+Space to move up
   - Ctrl+Enter vs Shift+Enter make a huge difference for cells thar produce lots of output.
     Ctrl+Enter would keep cursor at current cell, allowing you to naturally scroll through the output from top to bottom.

## Make your own shortcuts
   - For example, ESC will take you out of cell edit mode AND will disable fullscreen. Very annoying.
     Rebinding this to Ctrl+Space makes things much more convenient.
     To change settings, in JupyterLab go to Settings->Settings Editor->Keyboard Shortcuts
   - There are also extra settings you can change by editing a json file.

## Run jupyter in standalone browser window
   - This will allow you to use more shortcuts.
   - This also gives you fullscreen which you can't turn off (so, no need to rebind ESC key anymore)
   - To run jupyterlab in Firefox kiosk mode, run:
     `firefox --kiosk --new-window http://localhost:8888/lab`
   - After that, to navigate to other windows, use Alt+Tab, and to close window use Ctrl+W
   - If you have multi-monitor setup, what I found to work is first move terminal from which you
     enter this command to the monitor you want jupyterlab to start on.
   - This works, but some things are broken. For example, clicking on links inside jupyter notebooks will break things.

This solution is a bit hacky. If you can, try jupyterlab-desktop: <https://github.com/jupyterlab/jupyterlab-desktop>

It handles link opening issue slightly better: it opens a new window. But still, it could have been
better if it opened it in the default system browser instead. It is an open bug right now:
<https://github.com/jupyterlab/jupyterlab-desktop/issues/618> (I have a patch that fixes it in my github repo if you need it)

On the plus side, you can use it to connect to your own instance of jupyterlab.

## Exception handling
What if you have a cell that might raise an exception but you must step to the next cell (perhaps to do some cleanup?) even if there is an exception? This is where cell tags come into play.

Select a cell, click on cogwheels on the right, then Common tools, and click add tag.
Write `raises-exception` there and you are good to go. You can now write any cleanup code in the next cell.

This can help you not having to restart the whole notebook just because you got an exception thrown out and you didn't do some critical cleanup.

Also, if you are working on a single notebook, consider using classical Jupyter notebook. It has less crowded interface and is snappier.

# Unsolved questions

- How to persist the location inside a notebook on browser restart/reload?
- How to run all cells without moving all the way to the bottom of the notebook,
  and instead stay where you are?
- Better monitoring? What if I have a lot of data to print? It's easy to do in terminal,
  but jupyter cells don't follow the last input and so it's hard to track down what's going on
  like that.
- How do I enable emacs keybinds?
- How do I search through code output? It seems that Ctrl+F in jupyter only searches through cell inputs, but ignores output.
- Is it possible to use Makefile-style asset generation? I.e. run a notebook
  only if some file is missing or notebook is newer than that file.
  One issue: jupyter updates notebook timestamp even if notebook is not
  newer. Solution: use `nbdev_clean` and then take the diff to see if notebook
  was updated?
- Can I inject one notebook into another notebook?
  This way I wouldn't need to re-run the inner notebook if its target already exists.


