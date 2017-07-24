# Best Practices of React

## Components

1. Small, focused components.
2. Use container components.


### Small, focused components

What this **means** is that for instance you have a Button component.  

You need to **hide** all the **clumsy details inside that component**, and having the component something like this:   

	<Button />  

Now, this component can be **used anywhere** inside the app **without actually knowing** what it does in the hindside. This is known as **encapsulation**.  

***We are encapsulating the logic totally inside that component.***  



