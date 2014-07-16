## Design Guidelines
_Keep it simple, keep it smart, keep it consistent._
***
### General

The concept is simple. It needs to make sense. We will have many developers with different backgrounds working together. The last thing we need is more chaos. Thus our design motto: **Keep it simple, keep it smart, keep it consistent.**

### Structure

When designing an application, make sure your structure is logical. Segment code effectively, and don't be afraid to create new files if necessary. Make things as modular as possible. If you are building a collage program pull the code that actually builds the collage (the guts) and the code that just initializes it (the trigger) into different files.

Along with that aim to make your code as reusable as possible. Encapsulate custom functionality into classes or factories. Use protected or unique names, and document the bindings used to control your module. It may seem cumbersome, but two months from now you'll be glad you did.

As for the actual program structure...

Place functions chronologically on the page. If a function is always called first, place it at the top of the document. If a function is closely related to another, place them close together. If many of your functions call a custom utility function pull it out into it's own segment at the bottom of the document. Keep it clean, and easy to navigate.

### Syntax

To easy navigation please follow proper indentation, spacing, and statement closure.

All functions should have two newlines placed between them, for example:

    function one(){
        console.log("I am awesome!")
    }


    function two(){
        console.log("Nope.")
    }

If two functions are strongly related, or are one line this rule maybe relaxed.

**All indentations are to be four spaces, not tabs, not five spaces, not two, four spaces.**

This will become important since we will all be developing on different devices/operating systems. Newline characters should also be Unix based but for now we shouldn't need to worry about it.

Again make sure your indentation makes sense. Changes in scope should be indented, for example the statements inside loops, conditionals, or callback functions.

Do not use indentation when it would just add needless clutter. What constitutes clutter is a gray area, but typically keep related content close and use indentation and newlines to mark differences.

When to overstack slightly...

    function doEverything(){
        someLibrary.waitTillDone.then(function (){ //<-- Please don't break this onto a newline.
            alert("It's done!")
        },{ //<-- Notice multiple parenthesis here.
            options: [ //<-- This might look a little goofy, but it is really easy to add elements to, do it.
                         {option: "Option 1"},
                         {option: "Option 2"}
                     ]
        })
    }

When to not...

    function doAlmostEverything(){
       
        if (running){ doFirst() } //<-- If you are are only executing one command feel free to compress it like this, make sure you use the spaces and brackets.
       
        else{
            for (var index = 0; index < 100; index++){
                var secondTimer = setTimeout(100, doThird) //<-- Clump together related commands.
                doSecond(secondTimer)
            }

            //Since the second step tripped the third.
            doFourth()
        }
    }
        
It may seem trivial, but it is important the code looks similar across the board.
Finally just a few points about variable use.

Make sure you use the `var` declaration on local variables. JavaScript creates globals by default, so you will quickly pollute the namespace otherwise. Make sure you name your variables logically. If I was working on that collage library I would name the picture collageImage or collageElement. Camel case is preferred, when in doubt use longer variable names. We can always minify later.

If you do need globals try to group these together either at the top of your file or in an initialization function. Typically object encapsulation will be preferred, but for smaller libraries it might not make sense. For all variables set them before use, and clean them up after. Do not trust that a global has been set, check it, or better still set it yourself. When a variable is no longer required set it to undefined `x = undefined`, and add checks to make sure the data you are working with is valid.

### Comments

Comment everything. On longer functions add notes about what it will do, and in appropriate placed tell how it works. Make notes about your logic and todos if necessary.

Formatting and position for comments is a little less important, but try to match the below example. Make sure that you use `//` for all commenting. The multi-line comment `/*  */` should only be used in debugging to deactivate chunks of code.

    function cleanUp(){
        //Wrap up the final processing and clean unnecessary variables.
        
        //Go through all our values and delete them.
        for (var index = 0; index < 100; index++){
            if (values.length == 0){ break; } //Skip processing if nothing is there.
            values[index] = undefined;
        }

        goodBye()
        //Sends final goodbye to the system and cuts power.
        //Seems to work well but there is a slight delay.
        //TODO: Investigate and patch delay problem.
    }

That wasn't too painful. You have finished part one. You should have a general idea what we are looking for. The rest of the rules in this documentation set describe particular instances of when and how to implement these design strategies. If you learned nothing else from this document just please remember:

**Keep it simple, keep it smart, keep it consistent.**