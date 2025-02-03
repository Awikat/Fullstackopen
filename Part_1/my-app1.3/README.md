Here's the `README.md` for the refactored part:  

---

# Half Stack Application Development - Refactored Version  

This project continues from the previous steps, improving how data is structured by using objects instead of individual variables.  

## **Refactoring to Use Objects**  

In this step, we refactor the `App.jsx` component to store course parts as objects rather than separate variables.  

### **1. Updated `App.jsx`**  

Instead of using separate variables for each part, we now define each course part as an object:  

```jsx
import Header from './components/Header';
import Content from './components/Content';
import Total from './components/Total';

const App = () => {
  const course = 'Half Stack application development';
  const part1 = {
    name: 'Fundamentals of React',
    exercises: 10,
  };
  const part2 = {
    name: 'Using props to pass data',
    exercises: 7,
  };
  const part3 = {
    name: 'State of a component',
    exercises: 14,
  };

  return (
    <div>
      <Header course={course} />
      <Content parts={[part1, part2, part3]} />
      <Total parts={[part1, part2, part3]} />
    </div>
  );
};

export default App;
```

### **2. Content Component Update (`Content.jsx`)**  

The `Content` component now processes an array of objects instead of separate variables:  

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

### **3. Total Component Update (`Total.jsx`)**  

The `Total` component is modified to calculate the total exercises from the array of objects:  

```jsx
const Total = ({ parts }) => {
  const totalExercises = parts.reduce((sum, part) => sum + part.exercises, 0);
  return <p>Number of exercises {totalExercises}</p>;
};

export default Total;
```

### **4. Other Components Remain Unchanged**  

- `Header.jsx` remains the same since it only displays the course name.  
- `Part.jsx` continues to handle rendering individual course parts.  

### **5. Benefits of Refactoring**  

- **Better Data Structure**: Using objects improves data organization.  
- **Scalability**: It is easier to extend the application by adding more course parts.  
- **Readability**: Code is easier to understand and maintain.  

### **6. Running the Application**  

To run the updated application:  

```bash
npm run dev
```

The application should function as before but with a more structured data model. 🚀  

---

