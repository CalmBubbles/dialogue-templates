OMORI (Original game by OMOCAT, LLC)


Game: https://omori-game.com

OMOCAT, LLC: https://www.omocat-shop.com/pages/about



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


!!!!! REQUIRED !!!!!
Enabling/disabling the manager

    Since this template has a very customized structure, just using the default
    `DialogueManager.SetActive` break things.

    Use the template customized `DiaSetActive` method instead.


    !!!!! ALSO REQUIRED !!!!!

    If you're going to use portraits, make sure to set `enablePortrait` to `true`
    before enabling the box.


    JavaScript:
        enablePortrait = true;
        await DiaSetActive(true);
    

    Disabling the box automatically disables the portrait, and sets `enablePortrait` to `false`.


Broken dialogue portrait

    Refer to previous note.


Adding/changing the character name in dialogues

    To add a character name to the dialogues, set `charName` to the name you want
    before enabling the box.
    Make sure to use all caps/uppcase letters to replicate the game.


    JavaScript:
        charName = "MARI";
        await DiaSetActive(true);


    Disabling the box automatically hides the name, and sets `charName` to `null`.


    To change the character name, it should not be hidden.
    If active, you can call `ChangeName` and pass the new name as parameter.

    JavaScript:
        ChangeName("HERO");


"Why is the previous text shifting when I type with a different font size/scale?"

    Since OMORI has a feature where different font sizes in dialogues
    can exist. You probably want to also replicate that, but ended up finding a
    style bug instead.

    To fix that, simply add `verticalAlign: "bottom"` ONLY on the text with a different size.


    JavaScript:
        await diaManager.Type("Wait, ", 1);
        await diaManager.Type("WHAT?!!", 1.5, new DialogueData({
            fontSize: "2em",
            verticalAlign: "bottom" // here
        }));


Switching fonts

    To switch fonts, call the `SetFont` method.
    Pass `1` as the parameter to change to the "OMORIGAME2" font (the creepy one).
    Pass `0`, for "OMORIGAME" (default).

    
    JavaScript:
        SetFont(1); // creepy


Screen shake

    To shake the screen, just call `ShakeScreen` and pass in the duration (seconds) as the
    first parameter, then the max intensity on the second.


    JavaScript:
        ShakeScreen(
            2, // 2 seconds
            3 // max intensity of 3
        );
    

    The intensity will be random. The value in the parameter is only it's max.
    It's measured by the page's body height percentage.


"How to use the text wave animation?"

    https://calmbubbles.github.io/docs/js-plugins/manual/DialogueSystem/animations


Changing the dialogue audio's base pitch

    Just change `OmoriAudioSource.basePitch`.


    JavaScript:
        // probably makes everything a varying screech
        diaManager.audioSource.basePitch = 40;


"Why are there `ref.png` files with the template?"

    I used real ingame screenshots to replicate their dialogue box.
    I left them in just in case I need to fix big innacuracies.

    You can also use them to compare the template's accuracy.