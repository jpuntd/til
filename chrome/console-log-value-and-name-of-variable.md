# Log value and name of variable to the console

I try to minimise the use of `console.log`for debugging, but sometimes logging a value to the console is the quickest way to find out what is happening.

Need to add the **name** of the variable you are logging to the output as well? Just wrap the variable in an object literal:

    console.log({ stateSlidecontainerOpen });

You can combine multiple variables and a message as well:

    console.log('inside changeHandler', { stateSlidecontainerOpen, sortOrder });
