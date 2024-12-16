## **What is component**

- React-এ **কম্পোনেন্ট** হলো UI (User Interface)-এর একটি মৌলিক উপাদান। এটি একটি **পুনর্ব্যবহারযোগ্য** এবং **স্বনির্ভর কোডের অংশ** যা UI-এর একটি নির্দিষ্ট অংশ উপস্থাপন করে। React কম্পোনেন্ট মূলত **JavaScript ফাংশন** বা **ক্লাস** যা ইনপুট (যাকে **props** বলা হয়) গ্রহণ করে এবং স্ক্রিনে কী দেখাবে তা বর্ণনা করে।

### **ফাংশনাল কম্পোনেন্ট**

- এটি সাধারণ একটি JavaScript ফাংশন যা `props` গ্রহণ করে এবং JSX রিটার্ন করে।
- সহজে লেখা যায় এবং **hooks** (যেমন `useState`, `useEffect`) ব্যবহার করে ফাংশনালিটি যোগ করা যায়।

### React কম্পোনেন্টের বৈশিষ্ট্য

- **পুনর্ব্যবহারযোগ্য (Reusable)**: কম্পোনেন্ট একাধিকবার ব্যবহার করা যায়, যা কোড পুনরাবৃত্তি কমায়।
- **কম্পোজেবল (Composable)**: এক কম্পোনেন্টের মধ্যে অন্য কম্পোনেন্ট বসিয়ে জটিল UI তৈরি করা যায়।
- **বিচ্ছিন্ন (Isolated)**: প্রতিটি কম্পোনেন্ট তার নিজস্ব স্টেট এবং রেন্ডারিং পরিচালনা করে, যা ডিবাগ ও টেস্ট করা সহজ করে।


## **JSX & Its Rules**

- **JSX (JavaScript XML)** React-এর জন্য একটি **সিনট্যাক্স এক্সটেনশন**, যা HTML-এর মতো দেখতে কোড লিখে JavaScript এর ভেতরেই UI গঠন করা সহজ করে। এটি JavaScript এবং HTML-এর মিশ্রণ, যা রিয়াক্ট কম্পোনেন্ট তৈরি করা আরও কার্যকর করে তোলে।

---

### **JSX-এর বৈশিষ্ট্য**

- **HTML-এর মতো সিনট্যাক্স**: JavaScript এর ভিতরে HTML লিখতে দেয়।
- **JavaScript এর সংমিশ্রণ**: `{}` ব্যবহার করে JavaScript এক্সপ্রেশন যোগ করা যায়।
- **JavaScript-এ রূপান্তর**: JSX সরাসরি ব্রাউজারে চলে না; এটি Babel-এর মতো টুল দিয়ে JavaScript-এ রূপান্তরিত হয়।

---

### **Rules of JSX**

1. **Return a Single Parent Element**:
    
    JSX expressions must return a single parent element.
    
    ```xml
    // Correct
    return (
        <div>
            <h1>Heading</h1>
            <p>Paragraph</p>
        </div>
    );
    ```
    
2. **Self-closing Tags**:
    
    Elements without children must be self-closed.
    
    ```jsx
    <img src="image.png" />  // Correct
    <br />                  // Correct
    ```
    
3. **JavaScript in Curly Braces**:
    
    Embed JavaScript expressions inside `{}` in JSX.
    
    ```jsx
    const name = "Ali";
    return <h1>Hello, {name}!</h1>;
    ```
    
4. **Class is `className`**:
    
    Since `class` is a reserved keyword in JavaScript, use `className` instead.
    
    ```jsx
    <div className="container">Hello</div>
    ```
    
5. **Style Attribute**:
    
    Use camelCase for CSS properties and provide them as an object.
    
    ```jsx
    const style = { color: "blue", fontSize: "20px" };
    return <h1 style={style}>Styled Text</h1>;
    ```
    
6. **Fragments for Grouping**:
    
    Use `<React.Fragment>` or shorthand `<>` to group elements without adding an extra DOM node.
    
    ```jsx
    return (
        <>
            <h1>Heading</h1>
            <p>Paragraph</p>
        </>
    );
    ```
    
7. **Expressions, Not Statements**:
    
    JSX allows expressions (e.g., ternary operators) but not full statements like `if` or `for`.
    
    ```jsx
    // Correct
    return isLoggedIn ? <h1>Welcome!</h1> : <h1>Please Login</h1>;
    
    // Incorrect
    if (isLoggedIn) {
        return <h1>Welcome!</h1>;
    }
    ```
    
8. **Avoid Injecting Objects Directly**:
    
    You cannot embed objects in JSX unless explicitly rendered as strings or mapped.
    
    ```jsx
    const obj = { key: "value" };
    return <div>{obj.key}</div>; // Correct
    ```
    
9. **Comments in JSX**:
    
    Comments should be wrapped in curly braces `{}`.
    
    ```jsx
    return (
        <div>
            {/* This is a comment */}
            <h1>Hello</h1>
        </div>
    );
    ```

## **Dynamic Content to JSX**

- **JSX-এ ডায়নামিক কনটেন্ট** বলতে বোঝায় এমন কন্টেন্ট যা অ্যাপ্লিকেশনের **স্টেট**, **প্রপস**, বা **ইউজারের ইন্টারঅ্যাকশন** এর উপর ভিত্তি করে পরিবর্তিত হয়। JSX-এ `{}` (কার্লি ব্রেস) ব্যবহার করে সহজেই ভ্যারিয়েবল, এক্সপ্রেশন বা ফাংশনের আউটপুট যুক্ত করা যায়।

    ```jsx
    const name = "Ali";
    return <h1>Hello, {name}!</h1>;
    //Output: Hello, Ali!
    ```

    ```jsx
    function DynamicImage() {
        const imageUrl = "https://via.placeholder.com/150"; // Dynamic Image URL
        const imageAlt = "Placeholder Image"; // Dynamic alt text

        return (
            <div>
                <img src={imageUrl} alt={imageAlt} />
                <p>{imageAlt}</p>
            </div>
        );
    }

    export default DynamicImage;
    ```

    ## **What is React?**

- React is a **JavaScript library** used for building **user interfaces (UIs)**, especially for single-page applications. It allows developers to create reusable UI components, making the development process faster, more efficient, and easier to maintain.

## **Why Use React?**

- **Reusable Components:** Build once and reuse components across different parts of the application.
- **Fast Rendering:** React's virtual DOM ensures fast and efficient updates to the UI.
- **Large Ecosystem:** React has a vast ecosystem of tools, libraries, and resources to help with development.
- **Community Support:** React is maintained by Facebook and a large community, ensuring regular updates and best practices.

## **React Component কী?**

**React Component** হলো React-এর একটি মূল ধারণা। এটি এমন একটি পুনঃব্যবহারযোগ্য কোড ব্লক যা UI (User Interface) তৈরি করতে ব্যবহৃত হয়। Component-গুলোর মাধ্যমে বড় অ্যাপ্লিকেশনকে ছোট, আলাদা অংশে ভেঙে ফেলা যায়, যা সহজে ব্যবস্থাপনাযোগ্য এবং পুনঃব্যবহারযোগ্য।

- React Component একটি JavaScript ফাংশনের মতো কাজ করে। এটি **input (props)** নেয় এবং **output হিসেবে JSX (HTML-like structure)** প্রদান করে।

## **React Component-এর ধরণ**

React-এ দুটি প্রধান ধরনের Component রয়েছে:

### **১. Functional Component**

- এটি একটি সাধারণ JavaScript ফাংশন যা JSX রিটার্ন করে।
- React Hooks-এর সাহায্যে Functional Component-এ state এবং lifecycle method ব্যবহার করা যায়।
- এটি হালকা ও সহজ এবং আধুনিক React অ্যাপে বেশি ব্যবহৃত হয়।

**উদাহরণ:**

```jsx
const Greeting = () => {
  return <h1>Hello, World!</h1>;
};

export default Greeting;
```

### **২. Class Component**

- এটি একটি ES6 ক্লাস যা `React.Component` থেকে এক্সটেন্ড করে।
- এতে `render()` মেথড থাকে যা JSX রিটার্ন করে।
- এটি React Hooks আসার আগে state এবং lifecycle method পরিচালনার জন্য ব্যবহৃত হতো।
- Class Component এখন কম ব্যবহৃত হয়।

**উদাহরণ:**

```jsx
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, World!</h1>;
  }
}
```

## **Functional vs Class Component কবে ব্যবহার করবেন?**

- **Functional Component:** আধুনিক React-এ সবসময় Functional Component ব্যবহার করুন। এগুলো সহজ এবং Hooks সাপোর্ট করে।
- **Class Component:** শুধুমাত্র পুরোনো প্রোজেক্টে যেখানে Hooks নেই।

## **JSX কী?**

**JSX (JavaScript XML)** হলো জাভাস্ক্রিপ্টের একটি সিনট্যাক্স এক্সটেনশন, যা দেখতে HTML-এর মতো লাগে কিন্তু এটি জাভাস্ক্রিপ্টের ভেতরে কাজ করে। **React**-এ UI (User Interface) স্ট্রাকচার বর্ণনা করার জন্য JSX ব্যবহার করা হয়।

---

### **JSX-এর বৈশিষ্ট্য**

1. **HTML-এর মতো কোড লেখা যায়:**
    
    JSX আপনাকে JavaScript-এর ভেতরে সরাসরি HTML-এর মতো কোড লিখতে দেয়।
    
2. **HTML নয়, তবে HTML-এর মতো:**
    
    JSX কোনো প্রকৃত HTML নয়। এটি একটি জাভাস্ক্রিপ্ট সিনট্যাক্স যা **Babel** এর মতো টুল ব্যবহার করে সাধারণ JavaScript-এ রূপান্তরিত হয়।
    

---

### **কেন JSX ব্যবহার করা হয়?**

JSX ব্যবহার করলে জাভাস্ক্রিপ্ট এবং HTML একত্রে ব্যবহারের সুবিধা পাওয়া যায়। এটি React-এ UI তৈরি করার প্রক্রিয়াকে দ্রুত এবং সহজ করে তোলে।

## **How to Add Dynamic Content in JSX**

- You can embed any JavaScript expression inside JSX using curly braces `{}`.

### **Example 1: Display a Variable**

```jsx
const App = () => {
  const name = "John";
  return <h1>Hello, {name}!</h1>;
};
```

Here, `name` is dynamically added to JSX.

### **Example 2: Conditional Rendering in JSX**

Use ternary operators to conditionally display content:

```jsx
const App = () => {
  const isLoggedIn = true;
  return <h1>{isLoggedIn ? "Welcome back!" : "Please log in."}</h1>;
};
```

## **Create a Component with Dynamic Content**

- Inside the `src` folder, create a file `Greeting.jsx`:

```jsx
import React from "react";

const Greeting = () => {
  const user = { name: "Alice", age: 25 };
  const isLoggedIn = true;

  return (
    <div>
      <h1>Welcome, {isLoggedIn ? user.name : "Guest"}!</h1>
      <p>Your age is {user.age}.</p>
    </div>
  );
};

export default Greeting;
```

## **React-এর Props কী?**

- **Props** (properties-এর সংক্ষেপ) হলো React-এ ডেটা পাস করার একটি পদ্ধতি। সাধারণত, **parent component** থেকে **child component**-এ ডেটা পাঠানোর জন্য এটি ব্যবহার করা হয়। Props **read-only**, অর্থাৎ child component এটি পরিবর্তন করতে পারে না।
- Props React-এর কম্পোনেন্টকে ডাইনামিক এবং পুনরায় ব্যবহারযোগ্য করে তোলে।

### **Props-এর উদাহরণ**

1. **Parent Component (App):**
    
    ```jsx
    import React from 'react';
    import Greeting from './Greeting';
    
    const App = () => {
      return (
        <div>
          <Greeting name="Alice" />
          <Greeting name="Bob" />
        </div>
      );
    };
    
    export default App;
    ```
    
2. **Child Component (Greeting):**
    
    ```jsx
    import React from 'react';
    
    const Greeting = (props) => {
      return <h1>Hello, {props.name}!</h1>;
    };
    
    export default Greeting;
    ```
    

### **Props কেন দরকার?**

1. **কম্পোনেন্টের মধ্যে ডেটা শেয়ার করা।**
2. **UI ডাইনামিক করা।**
3. **কম্পোনেন্টকে পুনরায় ব্যবহারযোগ্য করা।**

### **Props-এর বেসিক ব্যবহার**

1. **Props পাঠানো:**
    
    Props HTML-এর অ্যাট্রিবিউটের মতো পাঠানো হয়।
    
    ```jsx
    jsx
    Copy code
    <ChildComponent attributeName="value" />
    
    ```
    
2. **Props গ্রহণ করা:**
    
    Props child component-এ একটি প্যারামিটার (`props`) হিসেবে পাওয়া যায়।
    
    ```jsx
    jsx
    Copy code
    const ChildComponent = (props) => {
      return <h1>{props.attributeName}</h1>;
    };
    
    ```
    
3. **Props ডিস্ট্রাকচারিং করা:**
    
    `props.attributeName` না লিখে সরাসরি ডিস্ট্রাকচারিং করা যায়:
    
    ```jsx
    jsx
    Copy code
    const ChildComponent = ({ attributeName }) => {
      return <h1>{attributeName}</h1>;
    };
    
    ```
    

### **Destructuring Multiple Props**

```jsx
jsx
Copy code
import React from 'react';

const ProductDetails = ({ name, price, description }) => {
  return (
    <div>
      <h2>Product Name: {name}</h2>
      <p>Price: ${price}</p>
      <p>Description: {description}</p>
    </div>
  );
};

export default ProductDetails;

```

## **Props এবং PropTypes কি?**

**Props (Properties):**

React-এ `props` ব্যবহার করে আমরা এক কম্পোনেন্ট থেকে অন্য কম্পোনেন্টে ডেটা পাঠাতে পারি। এটি একটি **read-only** ডেটা, যা আমরা শুধু পাস করতে পারি এবং কম্পোনেন্টের ভেতরে পরিবর্তন করতে পারি না।

---

## **PropTypes কি?**

React-এ **PropTypes** ব্যবহার করে আমরা নিশ্চিত করতে পারি যে একটি কম্পোনেন্ট সঠিক টাইপের props পাচ্ছে। এটি ডেভেলপমেন্টের সময় টাইপ সম্পর্কিত ত্রুটি ধরা সহজ করে তোলে।

**PropTypes** প্যাকেজটি React-এ বিল্ট-ইন আসে এবং এটি **runtime validation** করে।

---

### **PropTypes ব্যবহার করার ধাপ**

1. **PropTypes প্যাকেজ ইনস্টল করা:**
    
    ```bash
    npm install prop-types
    ```
    
2. **PropTypes ডিফাইন করা:**
    
    PropTypes ব্যবহার করে প্রত্যাশিত props টাইপ এবং তাদের বাধ্যতামূলকতা সেট করা হয়।


### **উদাহরণ ১: Basic Prop Validation**

```jsx
import React from 'react';
import PropTypes from 'prop-types';

const Greeting = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};

// PropTypes ডিফাইন করা
Greeting.propTypes = {
  name: PropTypes.string.isRequired, // name অবশ্যই string হতে হবে এবং এটি বাধ্যতামূলক
  age: PropTypes.number,             // age একটি সংখ্যা হতে হবে
};

export default Greeting;
```

**Parent Component-এ ব্যবহার:**

```jsx
import React from 'react';
import Greeting from './Greeting';

const App = () => {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" age={25} />
    </div>
  );
};

export default App;
```

### **PropTypes Validation টাইপসমূহ**

| PropTypes টাইপ | বর্ণনা |
| --- | --- |
| `PropTypes.string` | props টি string হতে হবে। |
| `PropTypes.number` | props টি number হতে হবে। |
| `PropTypes.bool` | props টি boolean হতে হবে। |
| `PropTypes.array` | props টি array হতে হবে। |
| `PropTypes.object` | props টি object হতে হবে। |
| `PropTypes.func` | props টি function হতে হবে। |
| `PropTypes.node` | render করা যায় এমন কিছু (string, JSX)। |
| `PropTypes.element` | একটি React element হতে হবে। |
| `PropTypes.oneOf` | নির্দিষ্ট কিছু মানের একটি হতে হবে। |
| `PropTypes.arrayOf` | নির্দিষ্ট টাইপের array হতে হবে। |
| `PropTypes.shape` | নির্দিষ্ট গঠনযুক্ত object হতে হবে। |
| `PropTypes.any` | যেকোনো টাইপ হতে পারে। |

---

### **উদাহরণ ২: Object এবং Array Validation**

```jsx
import React from 'react';
import PropTypes from 'prop-types';

const UserCard = ({ user }) => {
  return (
    <div>
      <h2>{user.name}</h2>
      <p>Email: {user.email}</p>
      <p>Age: {user.age}</p>
    </div>
  );
};

UserCard.propTypes = {
  user: PropTypes.shape({
    name: PropTypes.string.isRequired, // name বাধ্যতামূলক এবং string হতে হবে
    email: PropTypes.string.isRequired,
    age: PropTypes.number,
  }).isRequired,
};

export default UserCard;
```

**Parent Component-এ ব্যবহার:**

```jsx
import React from 'react';
import UserCard from './UserCard';

const App = () => {
  const user = { name: "Alice", email: "alice@example.com", age: 30 };

  return <UserCard user={user} />;
};

export default App;
```

## **Props পাস করার উপায়**

1. **একটি props পাস করা:**
    
    ```jsx
    <ComponentName propName="value" />
    ```
    
2. **একাধিক props পাস করা:**
    
    ```jsx
    <ComponentName prop1="value1" prop2={value2} />
    ```
    
3. **Object পাস করা:**
    
    ```jsx
    const user = { name: "Alice", email: "alice@example.com" };
    <ComponentName user={user} />
    ```
    

## **Props পড়ার উপায়**

1. **`props` এর মাধ্যমে এক্সেস:**
    
    ```jsx
    const ComponentName = (props) => {
      return <h1>{props.propName}</h1>;
    };
    
    ```
    
2. **Props destructuring:**
    
    ```jsx
    const ComponentName = ({ propName }) => {
      return <h1>{propName}</h1>;
    };
    ```
    
### **Using Destructuring in Function Parameters**

Destructuring ব্যবহার করে props এর নির্দিষ্ট মানগুলো সহজে পড়া যায়।

```jsx
// Parent Component:
const App = () => {
  return <WelcomeMessage name="Rahat" age={21} />;
};

export default App;
```

```jsx
const WelcomeMessage = ({ name, age }) => {
  return (
    <div>
      <h1>Welcome, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};

```

### **Passing an Object as a Prop**

যখন একটি অবজেক্ট পাস করা হয়, তখন অবজেক্টের ভেতরের ডেটা পড়া যায়।

```jsx
// Parent Component:
const App = () => {
  const userInfo = { name: "Rahat", email: "rahat@example.com", age: 21 };
  return <UserCard user={userInfo} />;
};

export default App;
```

```jsx
const UserCard = ({ user }) => {
  return (
    <div>
      <h2>{user.name}</h2>
      <p>Email: {user.email}</p>
      <p>Age: {user.age}</p>
    </div>
  );
};
```

## **React Conditional Rendering**

React-এ **Conditional Rendering** ব্যবহার করে আমরা শর্ত সাপেক্ষে UI-এ বিভিন্ন অংশ দেখাতে পারি। এখানে 5টি পদ্ধতি ব্যবহার করে Conditional Rendering দেখানো হয়েছে।

---

### **Parent Component (মূল কম্পোনেন্ট)**

```jsx
const App = () => {
  return (
    <div>
      <ToDo task="Learn React" isDone={true} />
      <ToDo task="Explore React Documentation" isDone={false} />
    </div>
  );
};

export default App;
```

**ব্যাখ্যা:**

- এখানে দুটি `ToDo` কম্পোনেন্ট ব্যবহার করা হয়েছে।
- `isDone={true}` হলে সম্পন্ন টাস্ক দেখাবে।
- `isDone={false}` হলে অসম্পন্ন টাস্ক দেখাবে।

---

### **পদ্ধতি ১: `if-else` ব্যবহার করা**

```jsx
const ToDo = ({ task, isDone }) => {
  if (isDone === true) {
    return <li>Finished: {task}</li>;
  } else {
    return <li>Work on: {task}</li>;
  }
};
```

**ব্যাখ্যা:**

- এখানে `if-else` ব্লক ব্যবহার করা হয়েছে।
- যদি `isDone` সত্য (true) হয়, তাহলে "Finished: {task}" দেখাবে।
- যদি `isDone` মিথ্যা (false) হয়, তাহলে "Work on: {task}" দেখাবে।
- পড়তে সহজ, তবে কোড একটু বেশি বড় হয়।

---

### **পদ্ধতি ২: শুধুমাত্র `if` ব্যবহার করা (বিনা `else`)**

```jsx
const ToDo = ({ task, isDone }) => {
  if (isDone) {
    return <li>Finished: {task}</li>;
  }
  return <li>Work on: {task}</li>;
};
```

### **পদ্ধতি ৩: Ternary Operator ব্যবহার করা**

```jsx
const ToDo = ({ task, isDone }) => {
  return <li>{isDone ? 'Finished' : 'Work on'}: {task}</li>;
};
```

**ব্যাখ্যা:**

- এখানে Ternary Operator (`?`) ব্যবহার করা হয়েছে।
- যদি `isDone` সত্য হয়, তাহলে "Finished: {task}" দেখাবে।
- যদি মিথ্যা হয়, তাহলে "Work on: {task}" দেখাবে।
- এটি সংক্ষিপ্ত এবং সরাসরি।

---

### **পদ্ধতি ৪: `&&` (Logical AND) ব্যবহার করা**

```jsx
const ToDo = ({ task, isDone }) => {
  return <li>{task} {isDone && ': Done'}</li>;
};
```

**ব্যাখ্যা:**

- `&&` ব্যবহার করে শর্ত সত্য হলে কেবল ডানপাশের অংশ দেখানো হয়।
- যদি `isDone` সত্য হয়, তাহলে `{task}` এর পরে ": Done" যোগ হবে।
- যদি মিথ্যা হয়, তাহলে শুধুমাত্র `{task}` দেখাবে।

---

### **পদ্ধতি ৫: `||` (Logical OR) ব্যবহার করা**

```jsx
const ToDo = ({ task, isDone }) => {
  return <li>{task} {isDone || ': Do it'}</li>;
};
```

**ব্যাখ্যা:**

- `||` ব্যবহার করে শর্ত মিথ্যা হলে ডানপাশের অংশ দেখানো হয়।
- যদি `isDone` সত্য হয়, তাহলে শুধুমাত্র `{task}` দেখাবে।
- যদি মিথ্যা হয়, তাহলে ": Do it" যোগ হবে।

---

## **Rendering Lists of Books using `map()` (Advanced)**

React-এ `map()` মেথড ব্যবহার করে একটি লিস্ট ডাইনামিকভাবে রেন্ডার করা খুবই সাধারণ এবং গুরুত্বপূর্ণ। এটি এমন অবস্থায় ব্যবহৃত হয় যখন আপনি একাধিক আইটেম বা ডেটা (যেমন ইউজারের লিস্ট) ডাইনামিক্যালি দেখাতে চান।

---

### **কীভাবে `map()` দিয়ে লিস্ট রেন্ডার করবেন**

1. **ডেটার জন্য একটি অ্যারে তৈরি করুন:** ইউজারের তথ্য (যেমন `id`, `name`, `email`) নিয়ে একটি অ্যারে তৈরি করুন।
2. **`map()` মেথড ব্যবহার করুন:** এই মেথড ব্যবহার করে অ্যারের প্রতিটি অবজেক্ট লুপ করুন এবং JSX তৈরি করুন।
3. **ইউনিক `key` প্রপ ব্যবহার করুন:** প্রতিটি লিস্ট আইটেমে একটি ইউনিক `key` প্রপ যোগ করুন, যাতে React সহজেই চেঞ্জ ট্র্যাক করতে পারে।
4. **লিস্ট রেন্ডার করুন:** ডাইনামিক্যালি তৈরি করা JSX লিস্ট রিটার্ন করুন।

### **১. Main Component: `App`**

```jsx

function App() {
  const books = [
    { id: 1, name: 'Bangla', price: 100 },
    { id: 2, name: 'English', price: 150 },
    { id: 3, name: 'Math', price: 200 },
    { id: 4, name: 'History', price: 250 },
  ];

  return (
    <>
      <Books books={books}></Books>
    </>
  );
}

```

### **ব্যাখ্যা:**

1. **`books` অ্যারে:** এটি একটি ডেটা সেট, যেখানে প্রতিটি অবজেক্টে একটি বইয়ের নাম (`name`), দাম (`price`), এবং একটি ইউনিক আইডি (`id`) রয়েছে।
2. **`<Books>` কম্পোনেন্ট:** `Books` কম্পোনেন্টে `books` ডেটা পাঠানো হয়েছে একটি প্রপ হিসেবে।

### **২. Books Component: `Books`**

```jsx
const Books = ({ books }) => {
  return (
    <div className="border p-10 mt-7 border-red-800 ml-6 w-fit rounded-xl">
      <h3>Books: {books.length}</h3>
      {
        books.map(book => <Book key={book.id} book={book}></Book>)
      }
    </div>
  );
};
```

### **ব্যাখ্যা:**

1. **প্রপস ডেসট্রাকচারিং:** `Books` কম্পোনেন্টটি `App` থেকে প্রপ হিসেবে `books` গ্রহণ করেছে।
    - `({ books })` এর মাধ্যমে সরাসরি `books` অ্যারে ব্যবহার করা হয়েছে।
2. **`books.length`:** মোট কয়টি বই রয়েছে তা দেখানোর জন্য ব্যবহার করা হয়েছে।
3. **`map()` মেথড:** প্রতিটি বইয়ের জন্য একটি `<Book>` কম্পোনেন্ট তৈরি করতে `map()` ব্যবহার করা হয়েছে।
4. **`key` প্রপ:** প্রতিটি বইকে ইউনিক করতে তার `id` ব্যবহার করে `key` প্রপ হিসেবে সেট করা হয়েছে। এটি React-কে লিস্ট আপডেট ট্র্যাক করতে সাহায্য করে।

---

### **৩. Book Component: `Book`**

```jsx
const Book = ({ book }) => {
  return (
    <div className="border p-3 mt-2 border-red-800 w-fit rounded-xl">
      <h3>Book Name: {book.name} </h3>
      <h3>Book Price: {book.price} </h3>
    </div>
  );
};

```

### **ব্যাখ্যা:**

1. **ডেসট্রাকচারিং:**
    - `book` নামক প্রপ `Books` থেকে পাঠানো হয়েছে।
    - ডেসট্রাকচারিং না করেও সরাসরি `book.name` এবং `book.price` এক্সেস করা হয়েছে।
2. **ডেটা রেন্ডার:** প্রতিটি বইয়ের নাম এবং দাম আলাদাভাবে দেখানো হয়েছে।

## **Event Handling**  কী?

ইভেন্ট হ্যান্ডলিং হলো ব্যবহারকারীর ইন্টারঅ্যাকশন (যেমন: বাটন ক্লিক, মাউস ওভার, কি বোর্ডের কী চাপা) পরিচালনার প্রক্রিয়া। এটি সাধারণত **ইভেন্ট লিসেনার** এবং **ইভেন্ট হ্যান্ডলার** ব্যবহার করে কাজ করে।

React-এ ইভেন্ট হ্যান্ডলিং JavaScript DOM ইভেন্টগুলির মতোই কাজ করে, তবে এটি **CamelCase** সিনট্যাক্স (যেমন: `onClick`, `onChange`) ব্যবহার করে এবং ফাংশনকে হ্যান্ডলার হিসেবে পাস করা হয়।


### **1. Inline Event Handling**

Directly defining the event handler inline when the event is triggered.

```jsx
function App() {
  return <button onClick={() => alert('Button clicked!')}>Click Me</button>;
}
```

### **2. Event Handler as a Function**

Defining the event handler as a separate function in the component.

```jsx
function App() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

### **3. Using Arrow Functions in Render**

Passing an arrow function directly in the JSX.

```jsx
function App() {
  const showMessage = (message) => {
    alert(message);
  };

  return <button onClick={() => showMessage('Hello!')}>Click Me</button>;
}
```

