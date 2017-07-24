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


## Split containers and components

Splitting containers and components is a very good practice which will **fetch you clean code**. So let's go and see what does it **mean in code**.  


**Without splitting the container and component**, our **code-base** looks like this: 

	class Sidebar extends React.Component {
		componentDidMount(){
			fetch('api.com/sidebar')
				.then(res => {
					this.setState({
						items: res.items
					})
				});
		
		}

		render(){

			return (
					<div className="sidebar">
						{
							this.state.items.map(item => (
								<div className="sidebar_item")>
								{item}
								</div>
							
							)
						}
					</div>
					
					);
		}
	}


After splitting the container and components, this is something we get:

	class SidebarContainer extends React.Component {
		componentDidMount(){
			fetch('api.com/sidebar')
				.then(res => {
					this.setState({
						items: res.items
					})
				});
		
		}

		render(){

			return (
					<Sidebar>
						{
							this.state.items.map(item => (
								<SidebarItem item={item} />	
							)
						}
					</Sidebar>
					
					);
		}
	}

So, from the above illustration we can clearly see what the **difference** is all about:

***In the second case (the cleaner one):***  

The **container component** is responsible for **fetching** the data and **providing** that data to its children (presentation components).

Whereas, the **presentation components** do the presentation work of **displaying** the data.


This **paradigm** makes our code **cleaner to read** and hence **debugging will be much easier**.

***So the thing that you should always keep in mind is:***
> One component should be responsible for only one task unless an emergency knocks on the door.