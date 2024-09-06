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
A component can pass values and arguments to another component. These values are called properties. They can be any kind of javascript value. 