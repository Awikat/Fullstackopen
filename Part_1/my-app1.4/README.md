Here’s the `README.md` for where we store course parts in an array of objects.  

---

# Half Stack Application Development - Refactored to Use Arrays  

This project continues from the previous steps, improving data structure by storing course parts in an **array of objects** instead of individual variables or separate objects.  

## **1. Refactoring to Use an Array of Objects**  

Instead of defining separate objects for each course part, we now store them in an array inside `App.jsx`:  

### **Updated `App.jsx`**
```jsx
import Header from './components/Header';
import Content from './components/Content';
import Total from './components/Total';

const App = () => {
  const course = 'Half Stack application development';
  const parts = [
    {
      name: 'Fundamentals of React',
      exercises: 10,
    },
    {
      name: 'Using props to pass data',
      exercises: 7,
    },
    {
      name: 'State of a component',
      exercises: 14,
    },
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

---

## **2. Refactored Components**  

### **Content Component (`Content.jsx`)**  
Since `parts` is now an array, we access its elements using indices.

```jsx
import Part from './Part';

const Content = ({ parts }) => {
  return (
    <div>
      <Part name={parts[0].name} exercises={parts[0].exercises} />
      <Part name={parts[1].name} exercises={parts[1].exercises} />
      <Part name={parts[2].name} exercises={parts[2].exercises} />
    </div>
  );
};

export default Content;
```

Alternatively, if we wanted to scale the application for more parts in the future, we could use `.map()`:

```jsx
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

---

### **Total Component (`Total.jsx`)**  
We now calculate the total number of exercises using array indexing:

```jsx
const Total = ({ parts }) => {
  const totalExercises = parts[0].exercises + parts[1].exercises + parts[2].exercises;
  return <p>Number of exercises {totalExercises}</p>;
};

export default Total;
```

Or using `.reduce()` for better scalability:

```jsx
const Total = ({ parts }) => {
  const totalExercises = parts.reduce((sum, part) => sum + part.exercises, 0);
  return <p>Number of exercises {totalExercises}</p>;
};

export default Total;
```

---

## **3. Other Components Remain Unchanged**
- `Header.jsx` remains unchanged since it only displays the course name.
- `Part.jsx` continues to handle rendering individual course parts.

---

## **4. Benefits of Using an Array of Objects**
✅ **Better Data Organization** - Keeping parts in an array improves structure.  
✅ **Easier to Extend** - We can easily add new parts without modifying multiple variables.  
✅ **Code Readability** - Code is easier to maintain and understand.  

---

## **5. Running the Application**  
To run the updated application:  

```bash
npm run dev
```

The application should work exactly as before, but with a more structured data model. 🚀  

---

