# Structure

component
└── MyComponent
    ├── index.js
    └── MyComponent.jsx

Each component should have its own folder. Inside the folder create an index.js file that exports the component.

e.g.

```jsx
// index.js
export { default } from './MyComponent'

// MyComponent
const MyComponent = (props) => {
  ...
}

export default MyComponent
```

Then you can import it like this:

```jsx
// AnotherComponent.jsx
import MyComponent from '@/MyComponent'   // Use '@' to avoid nesting's hell
...
```