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

&nbsp;
Previously, we tend to do something like this:  

	<Button className="btn"></Button>
	<Button className="btn btn-primary"></Button>

***className here is an implementation detail***  

> Which specific class names my Button component uses. My uses of that component should not care about that.   

The **Button component** should care about it, not us.


So, in **React** we do something like this:  

	<Button></Button>
	<Button primary></Button>

We give button a **property named primary**, which will be used by the **Button component**.