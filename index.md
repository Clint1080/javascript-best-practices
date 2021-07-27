Tip 1 {
    Make it Understandable
    Choose easy to understand and short names for variables and functions.

    Bad variable names:

    x1 fe2 xbqne
    Also bad variable names:

    incrementerForMainLoopWhichSpansFromTenToTwenty

    createNewMemberIfAgeOverTwentyOneAndMoonIsFull
    Avoid describing a value with your variable or function name.

    Might not make sense in some countries:

    isOverEighteen()
    Works everywhere:

    isLegalAge()
    Your code is a story - make your storyline easy to follow!
}
Tip 2 {
    Avoid Globals
    Global variables are a terribly bad idea.

    Reason: You run the danger of your code being overwritten by any other JavaScript added to the page after yours.

    Workaround: use closures and the module pattern
}
Tip 3 {
    Modularize
    Keep your code modularized and specialized.

    It is tempting and easy to write one function that does everything. However, as you extend the functionality you will find that you do the same things in several functions.

    To prevent that, make sure to write smaller, generic helper functions that fulfill one specific task rather than catch-all methods.

    At a later stage you can also expose these functions when using the revealing module pattern to create an API to extend the main functionality.

    Good code should be easy to build upon without rewriting the core.
}
Tip 4 {
        Use === Instead of ==
    JavaScript uses two different kinds of equality operators: === and !== are the strict equality operators, while ==  and != are the non-strict operators. It is considered best practice to always use strict equality when comparing.

    "If two operands are of the same type and value, then === produces true and !== produces false." - JavaScript: The Good Parts

    However, when working with == and !=, you'll run into issues when working with different types. When the values you're comparing have different types, the non-strict operators will try to coerce their values, and you may get unexpected results.
}
Tip 5 {
    Don't Use Shorthand
    Technically, you can get away with omitting most curly braces and semi-colons. Most browsers will correctly interpret the following:

    if(someVariableExists)
    x = false
    However, consider this:

    if(someVariableExists)
    x = false
    anotherFunctionCall();
    You might think that the code above would be equivalent to:

    if(someVariableExists) {
    x = false;
    anotherFunctionCall();
    }
    Unfortunately, you'd be wrong. In reality, it means:


    if(someVariableExists) {
    x = false;
    }
    anotherFunctionCall();
    As you'll notice, the indentation mimics the functionality of the curly brace. Needless to say, this is a terrible practice that should be avoided at all costs. The only time that curly braces should be omitted is with one-liners, and even this is a highly debated topic.

    1
    if(2 + 2 === 4) return 'nicely done';
    Always Consider the Future
    What if, at a later date, you need to add more commands to this if statement? In order to do so, you would need to rewrite this block of code. Bottom line—tread with caution when omitting.


}
Tip 6 {
    Declare Variables Outside of the For Statement
    When executing lengthy for statements, don't make the engine work any harder than it must. For example:

    Bad
    for(var i = 0; i < someArray.length; i++) {
    var container = document.getElementById('container');
    container.innerHtml += 'my number: ' + i;
    console.log(i);
    }
    Notice how we must determine the length of the array for each iteration, and how we traverse the DOM to find the "container" element each time—highly inefficient!

    Better
    var container = document.getElementById('container');
    for(var i = 0, len = someArray.length; i < len;  i++) {
    container.innerHtml += 'my number: ' + i;
    console.log(i);
    }
}
Tip 7 {
    Use Single "var" Declaration per Scope
    Since "var" accepts multiple declarations there is no reason to use more. All scope variables are moved to the top of the scope anyway (this is called hoisting). This may help reduce potential unexpected behavior in case duplicate names are introduced or some other logical mistakes are made.

    (function(){

        var firstName = 'John',
            lastName = 'Doe',
            fullName = firstName + ' ' + lastName;
            
        // The rest of the function body
        
    }());

}
Tip 8 {
    Development Code is for Developers
    Do not write code for yourself. Write it for other developers who will take it over from you.

    Prefer Clarity over Brevity. That means that function and variable naming should be meaningful rather than short. JavaScript compressor (Closure Compiler, YUI Compressor) will minify it for you if you end up with really long names. These rules apply to many other languages, too. The same goes the other way: things that work well in other languages may work well in JavaScript, too.

    Log as much as you can. You may see logs in the console when you least expect them. It will help you have a better understanding what is going on, especially if the system is complex. This is very useful for other developer who will maintain the code in the future. Console can be a big time saver when trying to locate needed line of script or sometimes just to be aware what code is being executed. In Google Chrome it shows file and line from which it was called, too.

    Be aware that code may brake if console is not present. To avoid errors replace it with fake console object and methods, when console is not present:

    var console = window.console || {};
    console.log = console.log || function(){};
    console.warn = console.warn || function(){};
    console.error = console.error || function(){};
    console.info = console.info || function(){};
    This is of course not necessary in the production code. Stripping this code can be built in into the build process, so that logging code is removed before compression and deployment to production. Following regex will strip all calls to console:

    ^\\s\*console\\.(log|warn|error|info)\\(.+\\);\\s\*$
    Visual Event is a bookmarklet which provides debugging information about events that have been attached to DOM elements. It can be big time saver when trying to locate what code is being called when an event is triggered.

    Development code is for developers, production code is for machines. Therefore minimize and optimize code for production. Use build process to minify, optimize and combine code files.
}
Tip 9 {
    Organize your declarations
    Be consistent with the way you declare things. Put all your declarations on top starting with the constants down to the variables. Make constants all uppercase to indicate they are constants which will prevent devs from trying to change them.
}
Tip 10 {
    Lint your code and have a consistent style
    Linting your code is the best way to ensure a consistent look and feel of your code and make sure people don't do weird things to it as well. It puts everyone on the same page.

}