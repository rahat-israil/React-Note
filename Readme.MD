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
