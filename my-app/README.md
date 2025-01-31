Here's a detailed `README.md` file for your project:

---

# Half Stack Application Development

This project demonstrates how to create a simple React application by breaking it down into smaller, reusable components. The application displays information about a course, its parts, and the total number of exercises.

## Steps to Set Up the Project

### **1. Initialize the Project with Vite**

To start the project, we will use Vite, a fast development tool that allows us to set up React quickly.

```bash
npm create vite@latest my-app --template react
cd my-app
npm install
```

This command creates a new React application using the Vite template, then installs the necessary dependencies.

### **2. Modify `main.jsx`**

In this step, we modify `main.jsx` to use the `ReactDOM.createRoot` method for rendering the app.

```jsx
import ReactDOM from 'react-dom/client';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(<App />);
```

This sets up the root of the React application to render the `App` component.

### **3. Modify `App.jsx`**

Now we create the main `App` component. Initially, we define the course and its parts, and display the information directly within the component.

```jsx
const App = () => {
  const course = 'Half Stack application development';
  const part1 = 'Fundamentals of React';
  const exercises1 = 10;
  const part2 = 'Using props to pass data';
  const exercises2 = 7;
  const part3 = 'State of a component';
  const exercises3 = 14;

  return (
    <div>
      <h1>{course}</h1>
      <p>{part1} {exercises1}</p>
      <p>{part2} {exercises2}</p>
      <p>{part3} {exercises3}</p>
      <p>Number of exercises {exercises1 + exercises2 + exercises3}</p>
    </div>
  );
};

export default App;
```

This code directly renders the course information and calculates the total number of exercises.

### **4. Refactor the Application into Components**

To make the app modular and easier to manage, we break it down into three components: `Header`, `Content`, and `Total`.

#### **4.1 Create `Header` Component**

The `Header` component will render the course name.

```jsx
const Header = ({ course }) => {
  return <h1>{course}</h1>;
};

export default Header;
```

#### **4.2 Create `Part` Component**

The `Part` component is responsible for rendering individual parts of the course with their respective number of exercises.

```jsx
const Part = ({ name, exercises }) => {
  return <p>{name} {exercises}</p>;
};

export default Part;
```

#### **4.3 Create `Content` Component**

The `Content` component will render multiple `Part` components.

```jsx
import Part from './Part';

const Content = ({ parts }) => {
  return (
    <div>
      {parts.map((part, index) => (
        <Part key={index} name={part.name} exercises={part.exercises} />
      ))}
    </div>
  );
};

export default Content;
```

#### **4.4 Create `Total` Component**

The `Total` component will display the total number of exercises by summing the `exercises` from all parts.

```jsx
const Total = ({ parts }) => {
  const totalExercises = parts.reduce((sum, part) => sum + part.exercises, 0);
  return <p>Number of exercises {totalExercises}</p>;
};

export default Total;
```

### **5. Update `App.jsx` to Use Components**

Finally, we update `App.jsx` to import and use the new components, passing the necessary data via props.

```jsx
import Header from './components/Header';
import Content from './components/Content';
import Total from './components/Total';

const App = () => {
  const course = 'Half Stack application development';
  const parts = [
    { name: 'Fundamentals of React', exercises: 10 },
    { name: 'Using props to pass data', exercises: 7 },
    { name: 'State of a component', exercises: 14 },
  ];

  return (
    <div>
      <Header course={course} />
      <Content parts={parts} />
      <Total parts={parts} />
    </div>
  );
};

export default App;
```

### **6. Remove Unnecessary Files**

We remove the unnecessary files such as `App.css`, `index.css`, and the `assets` directory to keep the project clean and organized.

```bash
rm src/App.css src/index.css -rf src/assets
```

### **7. Running the Application**

To run the application and view the changes, use the following command:

```bash
npm run dev
```

This will launch the development server and open the app in your browser.

## Folder Structure

After refactoring, the project folder structure looks like this:

```
src/
|-- components/
|   |-- Header.jsx
|   |-- Part.jsx
|   |-- Content.jsx
|   |-- Total.jsx
|-- App.jsx
|-- main.jsx
|-- index.html
```

## Conclusion

In this project, we created a simple React application by breaking it into smaller components (`Header`, `Content`, `Part`, and `Total`). The application uses props to pass data between components, making it modular and easy to maintain.

---

Let me know if you need any further modifications or clarifications!
