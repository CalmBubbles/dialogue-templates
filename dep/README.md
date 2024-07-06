Dweller's Empty Path (Original game by Temmie Chang)


Game: https://tuyoki.itch.io/dwellers-empty-path

Temmie: https://tuyoki.itch.io



---------------
DialogueSystem.js
---------------

Manual: https://calmbubbles.github.io/docs/js-plugins/manual/DialogueSystem

Scripting Reference: https://calmbubbles.github.io/docs/js-plugins/reference/DialogueSystem



---------------
Notes:
---------------

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


Adding delays without the arrow indicator appearing

    Using `DialogueLoop.Delay` to add delays will make the arrow indicator appear.
    To avoid that, use the `DialogueData` method.

        https://calmbubbles.github.io/docs/js-plugins/manual/DialogueSystem/start/delays


    I recommend only using the `DialogueData` method on adding delays between Type calls
    that will appear on the same screen, like coma, stutters and newline delays.
    Then using `DialogueLoop.Delay` on anything else, like before clearing or closing the box.
    This is to copy the game's behavior of waiting input, without input.

    Like:
        Yada, {DialogueData} yadayadayada yadayada.

        {DialogueLoop.Delay}
        {clear text}

        Yadayada yadayadayada, {DialogueData}yada yadayada.\n
        Yada yadayada yadayadayada yada yadayada.\n
        {DialogueData}Yadayadayadayada, {DialogueData}yadayada yadayada.

        {DialogueLoop.Delay}
        {close box}


"Why are there `ref.png` files with the template?"

    I used real ingame screenshots to replicate their dialogue box.
    I left them in just in case I need to fix big innacuracies.

    You can also use them to compare the template's accuracy.