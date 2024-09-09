React is an User Interface library for rendering user interfaces built.
## Building Blocks
Every UI component in React is called component. It can be anything from a single text to a whole page. For example:
```
function Photo() {
	return <img src="photo1.jpeg" />
}
```
This is a component called `Photo`. If you want to use, you can call it in any other component just like HTML tags. For example, there's a gallery component that you can combine `Photo` to form another component, like:
```
import Photo from './Photo.js';

export function Gallery() {
	return(
		<section>
			<Photo />
		</section>
	);
}
```
### Component Properties
A component can pass values and arguments to another component. These values are called properties. They can be any kind of javascript value. For example, you will see that some native react components can receive props, like:
```
<div className={"m-0"} />
```
The `<div>` component can receive `className` which is all the `CSS` classes that are going to be applied to the div.

In order to pass properties to a custom component, you can do it just like with `className`:
```
export function App() {
	return <Avatar 
		name={"leonardo"} 
		age={24}
		documentation={{
			rg: "31.191.910-4",
			cpf: "182.080.157-84",
			birthdate: "2000-04-24"
		}} />
}
```
Now, you can get this properties values can be extracted from the component function argument:
```
export function Avatar({ name, age, documentation }) {
	// content...
}
```
The argument itself is called `props`, but you can apply spreading operator to only extract what you want to extract. If you are using typescript, you can create a type or an interface to type exactly the content you want to receive.
```
type Props = {
	name: string;
	age: number;
	documentation: {
		rg: string;
		cpf: string;
		birthdate: string;
	}
}

export function Avatar({ name, age, documentation }: Props) {
	//content...
}
```

Besides, let's imagine that the age property can be defined as optional. How could you handle this? If you want to, you can add a default value when no value is specified by the parent:

```
type Props = {
	name?: string;
	age: number;
	documentation: {
		rg: string;
		cpf: string;
		birthdate: string;
	}
}

export function Avatar({ name = "void", age = 0 , documentation }: Props) {
	//content...
}
```

If you want to pass another react component as a property, you can do this using the `childrene` value of `props`.

```
export function TitleContainer({ children }) {
	return <div className="rounded-lg">
		{children}
	</div>
}

export function App() {
	return <div>
		<TitleContainer>
			<p> Teste </p>
		</TitleContainer>
	</div>
}
```

