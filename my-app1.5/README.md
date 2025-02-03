Here’s the `README.md` file for where we store course details as a single JavaScript object.  

---

# Half Stack Application Development - Refactored to Use a Single Object  

This step improves the structure of our application by storing the course name and its parts in a **single JavaScript object** instead of separate variables.  

---

## **1. Refactoring to Use a Single Object**  

Instead of defining `course` and `parts` separately, we now store them within a **single object** inside `App.jsx`.  

### **Updated `App.jsx`**
```jsx
import Header from './components/Header';
import Content from './components/Content';
import Total from './components/Total';

const App = () => {
  const course = {
    name: 'Half Stack application development',
    parts: [
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
    ],
  };

  return (
    <div>
      <Header courseName={course.name} />
      <Content parts={course.parts} />
      <Total parts={course.parts} />
    </div>
  );
};

export default App;
```

---

## **2. Refactored Components**  

### **Header Component (`Header.jsx`)**  
Since the course name is now inside an object, we update the prop name accordingly.  

```jsx
const Header = ({ courseName }) => {
  return <h1>{courseName}</h1>;
};

export default Header;
```

---

### **Content Component (`Content.jsx`)**  
The `parts` array is now inside `course`, but the structure remains the same.  

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

---

### **Total Component (`Total.jsx`)**  
Calculate the total exercises using `.reduce()`.  

```jsx
const Total = ({ parts }) => {
  const totalExercises = parts.reduce((sum, part) => sum + part.exercises, 0);
  return <p>Number of exercises {totalExercises}</p>;
};

export default Total;
```

---

## **3. Why This Change?**
✅ **Better Data Structure** - Course name and parts are grouped together.  
✅ **Easier to Extend** - Adding new properties to `course` is now simple.  
✅ **More Maintainable Code** - The app's structure is more logical and scalable.  

---

## **4. Running the Application**  
Start the development server:  

```bash
npm run dev
```

Your application should work exactly as before, but with a **better structured data model**. 🚀  

