# react-virtual-list

`react-virtual-list` is a lightweight React component that helps you efficiently render long vertical lists by **only rendering visible items** (and a few extras for smooth scrolling). This technique, known as **virtualization** or **windowing**, drastically improves performance when working with thousands of list items.

---

## 🚀 Why Use This?

Rendering large lists (e.g., 10,000 items) can severely hurt performance in React. Instead of rendering all items at once, `react-virtual-list` calculates which items are visible in the scroll container and renders **only those**. It helps your UI stay fast, smooth, and memory-efficient.

---

## 📦 Installation

Install via npm or yarn:

```bash
npm install react-virtual-list
# or
yarn add react-virtual-list



🔧 Usage
tsx
Copy
Edit
import React from 'react';
import { VirtualList } from 'react-virtual-list';

const App = () => {
  const items = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);

  return (
    <div style={{ width: '300px', margin: '0 auto' }}>
      <h2>Virtualized List</h2>
      <VirtualList
        items={items}
        height={400}
        itemHeight={40}
        renderItem={(item, index) => (
          <div style={{ padding: '0 12px', borderBottom: '1px solid #ccc' }}>
            {item}
          </div>
        )}
      />
    </div>
  );
};

export default App;