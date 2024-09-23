## Tools
The react library was created using existing tools in the javascript world. In this section, we will go through them and understand it all properly.
### Babel
Babel is a javascript compiler that aims to convert ECMAScript 2015+ code into backwards compatible version of javascript in current and older browsers or environments. It can transform syntax, polyfill features that are missing in your target environment and source transformations.
These kind of transformations are supported through plugins. These plugins are javascript library codes that you use to instruct babel how to transform your source code.
In order to configure the babel compiler behavior, you can create a file `.babelrc` or `babe.config.json`. The `.babelrc` is a file that can be used to define specific transformations for files or directories. The `babel.config.json` applies to the entire project, even if you have another `package.json`.
#### PreSets
Babel and its plugins has a lot of configurations to make it work properly. It would be very inefficient to write it every time you need to use them. So, in order to make this process efficient, the presets were created. The presets are an assortment of plugins and configurations that you can apply to your project directly.
### Webpack
It's a module bundler that takes all your files and transform it into one single file. It can handle js, css, sass, png and any other kind of file.
## Definition
React is an User Interface library for rendering user interfaces built. It was created by facebook in 2011. 
In order to create a react project, you should use a template. In react, you will use most of the times `npx create-react-app <project-name>`. This command will generate a folder with all the structure and dependencies installed for you.
## Project Structure
- public: Folder containing the public files that are retrieved from the server
- src: The source code containing all the javascript files.
	- index.js: The first code that is loaded into the HTML and it would load your entire application inside the div with id root.
## Building Blocks
### JSX
JSX is a new syntax created by Facebook to make creating components easy. It mixes the Javascript syntax with the HTML syntax. Because of this, you're able to write HTML inside the Javascript code. But, you need to write it in a different way, since it's not real HTML. For example, in JSX, you can return an HTML object:
```
const App = () => {
    return (
        <div className="App">
            <h1>Hello DIO!</h1>
            <p>1 + 1 = { 1 + 1 }</p>
        </div>
    )
}
```
Besides, you can use javascript inside the HTML code. But, in order to do that, you should encapsulate it inside brackets. In addition, keep in mind that everything inside the brackets will be returned to the HTML and It'll be displayed as HTML.
There're differences in some html properties, like `class`. `class` is a reserved keyword of Javascript. So, in order to use `class` property in HTML JSX, you should use `className`.
### Functional Components
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

> Components can be also created as classes, but it's an old approach and it's strongly recommended to use the functional approach. 

Besides, components can only return one tag. So, in some cases, you can use empty elements to represent a "container" like the example below:
```
<>
	<div>
		<p>Hello World</p>
	</div>
</>
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

If you want to pass another react component as a property, you can do this using the `chidren` value of `props`.

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

> Children, in this case, can be typed as a React Component or anything else, like text.

When the value of the props change, a new render of this children will be triggered and the new props will be reflected in the dom. But, you cannot change which params you pass to the children, but the value can be changed. 
### Component Lifecycle 
All components has a lifecycle. It all starts at the `constructing`. The constructing step is responsible to determine what it needs to be built and initialize states.

After that, the next method is the `render` method. This method is called when the component is inserted inside the real DOM. It only draw the content to the DOM. Then, any kind of side effect can't be done through this method.

Now, after rendering, you have the `componentDidMount` method. This method is executed right after the component is rendered for the first time. This method is used for running operations that can create side effects. Side Effects are actions that can cause the DOM to re-render.

When you have some side effect, you enter the `Updating Phase`. This phase occurs when the component has any update or it re-renders. This can occur when the props or states are updated or changed.

By default, every component and its children will re-render when a prop or state is changed. But, you can override this implementing the `shouldComponentUpdate`. This method returns true or false and receives the new state or props as parameters to help you determine if the component should update

After `shouldComponentUpdate` is called, React will call `render` to re-render the UI again. After this, the `componentDidUpdate` will be called.

When a component is not needed anymore, it starts the Unmounting Phase. It refers to the step that it will remove the component from the DOM. The method `componentWillUnmount` is called just before the component is removed from the DOM. It allows you to perform any kind of cleanup operation. All of the component data is destroyed.
### Conditional Rendering
Sometimes, you need to render something when some expression is true and render nothing or other component when the expression is false. In order to do this, you can use `if` expressions, ternary operator and the logical `&&` operator. For example:
```
export default function AlertModal({ channel, message, title, show = false }: Props) {  
  const toggleModal = () => {  
    channel.send("close_modal", !show);  
  };  
  return show && <div className={"z-10 h-screen w-screen bg-gray-500 bg-opacity-90 absolute top-0 left-0"}>  
    <div className={"w-[90%] h-1/4 bg-white rounded text-center p-4 relative"} style={{  
      margin: '0 auto',  
      transform: 'translateY(150%)'  
    }}>  
      <CloseIcon onClick={() => toggleModal()} className={"absolute top-5 right-5"}/>  
      <div className={"flex flex-col items-center justify-center h-full"}>  
        <WarningIcon fontSize={"large"} color={"warning"} />  
        <div className={"flex flex-col mt-6"}>  
          <span className="text-2xl">{title}</span>  
          <p className={"mt-4"}>{message}</p>  
        </div>      </div>    </div>  </div>;  
}
```

This component will only be rendered if the variable `show` is true. Otherwise, it would render nothing.  You still can use `if` and ternary operators to execute the same thing. 
### Rendering Lists
If you want to render lists, you can use javascript array functions to handle these operations, like filter or map. At first, you need to extract the data that will be rendered in a list to a separated array. Now, you can use the `map` operation, for example, to generate the list of items to be displayed.

```
const people = [
	"Leonardo",
	"Maria",
	"Carlos"
]

return <ul>
	{people.map(person => <li>{person}</li>)}
</ul>
```

This approach can be used to create a list of items, but you must pass some way to identify the item uniquely in this list. For example, imagine that you have 10 items in your list. If something happens to that list and the tree will be rendered again, react will not known which element has truly changed. So, in order to track the changes in each item, you must given them an unique key.

```
const people = [
	"Leonardo",
	"Maria",
	"Carlos"
]

return <ul>
	{people.map((person, index) => <li key={index}>{person}</li>)}
</ul>
```

> The key property can be used, but you should use something else.
## CSS Modules
A CSS Module is a file in which every class or animation is scoped locally. Besides, all URL and imports are in module request format (`./xxx` means relative and `xxx/yyy` means in module folder, for example, `node_modules`). It compiles to a low-level interchange format called ICSS but are like normal CSS files.