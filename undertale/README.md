UNDEERTALE (Original game by Toby Fox)


Game: https://undertale.com

Toby Fox: https://toby.fangamer.com



---------------
DialogueSystem.js
---------------

Manual: https://calmbubbles.github.io/docs/js-plugins/manual/DialogueSystem

Scripting Reference: https://calmbubbles.github.io/docs/js-plugins/reference/DialogueSystem



---------------
Notes:
---------------

"Why unfinsihed?"

    Making these stuff aren't easy, especially on my own.
    While working on DialogueSystem.js I was fighting time, but still ended up
    being late. By like idk 2..? uhhhhhh... 3+ years..? maybe?

    This template got unfinished because working with undertale's portraits is a
    little hard. The images per character don't have the same size and position.
    So I have to apply them manually by code.

    I'll still finish this template and update it occasionally.
    If you do want to help me, feel free to contribute here.


    https://github.com/calmbubbles/dialogue-templates#undertale


Box's size

    All of the elements within the box have a size relative to the window's width.
    By default, it is based on 98% of the window's width.

    To change the base size, you can use the `.textbox` element's `--base-width` CSS variable.
    Which is by default, 98. This means 98% of the window's width.


    CSS:
        /* You can just do this */
        .textbox
        {
            --base-width: 69;
        }

    
    You SHOULD NOT place any measurement unit (i.e., "px" or "%"), it will break.
    The unit is already managed, and is always "vw".


Adding/customizing asterisks

    To set asterisks, call `SetAsterisk` before Typing.
    This`ll show the first line asterisk.


    JavaScript:
        SetAsterisk();
        await Type("What are you looking at?", 1);
    

    To customize it, you've got to use it's parameters.
    The first parameter is for setting the second line.
    Second parameter for the third line.
    Pass in `true` to show, `false` to hide.


    JavaScript:
        SetAsterisk(
            false, // hide second line
            true // show third line
        );

    
    To hide the first line asterisk, use the method's third parameter.
    By default is `true`, which is why it's shown without parameters passed.


    JavaScript:
        SetAsterisk(false, false
            false // hide first line
        );



Switching fonts

    To switch fonts, call the `SetFont` method.
    Pass `1` as the parameter to change to the "sans" font.
    Pass `0`, for "Determination" (default).

    
    JavaScript:
        SetFont(1); // sands umbertale


"Why are there `ref.png` files with the template?"

    I used real ingame screenshots to replicate their dialogue box.
    This template is unfinshed, so still need them.
    I also left them in just in case I need to fix big innacuracies.

    You can also use them to compare the template's accuracy.