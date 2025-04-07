# ai-course-todo-list


# React TypeScript Todo App

Here's a breakdown:
1. **Import Statements**:
   * `React, { useState } from 'react'`: Imports React and the `useState` hook for managing component state.
   * `{ Plus, Trash2, Check, X } from 'lucide-react'`: Imports icons from the `lucide-react` library. These icons are used for the add button, delete button, and complete status.
2. **Todo Interface**:

```
interface Todo {
  id: number;
  text: string;
  completed: boolean;
}

```

   * Defines the structure of a `Todo` item with properties for `id`, `text`, and `completed`.
3. **App Component**:

```
function App() {
  // ...
}

```

   * This is the main component of the application.
4. **State Variables**:

```
const [todos, setTodos] = useState<Todo[]>([
  { id: 1, text: 'Learn React', completed: false },
  { id: 2, text: 'Build a Todo App', completed: false },
  { id: 3, text: 'Master Tailwind CSS', completed: false },
]);
const [inputValue, setInputValue] = useState('');

```

   * `todos`: An array of `Todo` objects, initialized with some default tasks. The `useState` hook is used to manage this state. `setTodos` is the function to update the `todos` state.
   * `inputValue`: A string representing the current value in the input field. `setInputValue` is used to update this state.
5. **handleAddTodo Function**:

```
const handleAddTodo = (e: React.FormEvent) => {
  e.preventDefault();
  if (inputValue.trim() === '') return;

  const newTodo: Todo = {
    id: Date.now(),
    text: inputValue,
    completed: false,
  };

  setTodos([...todos, newTodo]);
  setInputValue('');
};

```

   * This function is called when the form is submitted (i.e., when the user adds a new todo).
   * `e.preventDefault()`: Prevents the default form submission behavior, which would cause the page to reload.
   * `if (inputValue.trim() === '') return;`: If the input value is empty (or only contains whitespace), the function returns early, preventing the addition of empty todos.
   * A new `Todo` object is created with a unique `id` (using `Date.now()`), the `text` from the input value, and `completed` set to `false`.
   * `setTodos([...todos, newTodo])`: Updates the `todos` state by creating a new array that includes all the existing todos and the new todo.
   * `setInputValue('')`: Clears the input field.
6. **toggleComplete Function**:

```
const toggleComplete = (id: number) => {
  setTodos(
    todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    )
  );
};

```

   * This function is called when the user toggles the complete status of a todo.
   * `todos.map(...)`: Iterates over each todo in the `todos` array.
   * `todo.id === id ? { ...todo, completed: !todo.completed } : todo`: If the current todo's `id` matches the `id` passed to the function, a new object is created with the same properties as the original todo, but with the `completed` property toggled. Otherwise, the original todo is returned.
   * `setTodos(...)`: Updates the `todos` state with the new array.
7. **deleteTodo Function**:

```
const deleteTodo = (id: number) => {
  setTodos(todos.filter(todo => todo.id !== id));
};

```

   * This function is called when the user deletes a todo.
   * `todos.filter(...)`: Creates a new array containing only the todos whose `id` does not match the `id` passed to the function.
   * `setTodos(...)`: Updates the `todos` state with the new array.
8. **JSX Structure**:
   * The `return` statement contains the JSX structure that defines the UI of the component.
   * The main container is a `div` with a gradient background and flex layout.
   * Inside the container, there's a `div` that represents the todo list card, with a white background, rounded corners, and a shadow.
   * A heading displays "Todo List".
   * A form contains an input field and a button for adding new todos.
   * The list of todos is rendered using `todos.map(...)`. Each todo item is a `div` with a checkbox-like button and a delete button.
   * The todo text is displayed with a line-through style if the todo is completed.
   * A footer displays the total number of tasks and the number of completed tasks.
