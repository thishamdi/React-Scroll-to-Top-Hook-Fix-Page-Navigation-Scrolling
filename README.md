# **React Scroll to Top Hook: Fix Page Navigation Scrolling**

When navigating between pages in a React app using **React Router**, the scroll position of the previous page is **remembered**. To reset the scroll position to the top every time a new route is loaded, we use a custom hook: `useScrollToTop`.

---

## **The Problem**

In React SPAs:
1. When you navigate using `<Link>`, the scroll position **remains the same**.
2. Users may start viewing a new page from the bottom or middle, which disrupts the user experience.

---

## **The Solution: `useScrollToTop` Hook**

Here’s a lightweight custom hook that resets the scroll position to the top on every route change.

### **Code: `useScrollToTop.js`**
```jsx
import { useEffect } from 'react';
import { useLocation } from 'react-router-dom';

const useScrollToTop = () => {
    const location = useLocation();

    useEffect(() => {
        window.scrollTo(0, 0); // Scroll to top-left corner
    }, [location]);
};

export default useScrollToTop;
```

---

## **How to Use It**

1. Import the hook into any **page component**.
2. Call the hook at the top of the component.

### **Basic Example**
```jsx
import React from 'react';
import useScrollToTop from './useScrollToTop';

const About = () => {
    useScrollToTop(); // Ensures scroll resets to the top

    return (
        <div>
            <h1>About Us</h1>
            <p>Welcome to the About page!</p>
        </div>
    );
};

export default About;
```

---

## **Why Use This Hook?**

- **Fixes Scroll Behavior**: Ensures the user starts at the top of every new page.
- **Reusable**: Works seamlessly across multiple components.
- **Improves User Experience**: No need to manually reset scroll positions.

---

## **Where to Use It?**

- **Top-Level Page Components** (e.g., `Home`, `About`, `Contact`)
- **Layout Component** wrapping all routes

---

## **Conclusion**

The `useScrollToTop` hook provides a simple and clean solution to fix scroll behavior in React applications. Use it to ensure smooth navigation for your users.
