Title: My favorite code editor is killing my wrist: alternatives to the Escape key in Vim
Date: 2024-09-23 
Category: vim

I love writing code in Vim, but pressing the Escape key constantly hurts.  In Word, the keyboard keys are always "live" and create new characters on the page when they're pressed.  In contrast, Vim is a modal editor: typing makes new characters only when the editor is in insert mode.  There are two other common modes, normal (for entering commands) and visual (for selecting text).  

Switching between modes in Vim involves pressing the Escape key.  For example, to go from insert mode to normal mode and finally visual mode, we press the Escape key followed by the V key.  

Using Vim effectively means changing modes frequently.  Toggling between insert mode and normal mode is very common because normal mode enables cursor movement.  Rapid jumping within and among code files is one of the reasons I love using Vim, and that movement happens from normal mode. 

When I press the Escape key, my wrist turns slightly as my left ring finger moves from the S key on the home row up to the Escape key.  Making this movement hundreds of times a day led to growing pain in my wrist.  I stopped wearing a watch for a while because I didn't want to admit that Vim might be to blame, but the pain finally made me look for alternatives.

It's possible to map various key combinations to mimic the function of the Escape key, but these possible remappings all seem inadequate.  `inoremap jk` seems to be an especially common addition to `.vimrc` files, and some Vim users remap Caps Lock to Escape systemwide.  All of these customizations have an important disadvantage: they become part of muscle memory and are then hard to work around when using a machine other than one's own laptop. 

Luckily, there are built-in alternatives to the Escape key that require no customization at all.  Pressing Ctrl+[ and Ctrl+C both have the same effect as the Escape key.  Of these two combinations, Ctrl+C requires less hand movement to press, but I prefer Ctrl+[ out of habit.

If only I could disable the Escape key altogether, I could break myself of the habit of using it.  Unfortunately, remapping the Escape key to a no-op with, say, `inoremap <Esc> <Nop>` and `vnoremap <Esc> <Nop>` makes Vim unusable.  With those remappings in place, you can return to normal mode using any of the alternatives above, but it's impossible to enter commands without immediately reentering insert mode. 
