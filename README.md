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


📐 Component Props

Prop	Type	Required	Description
items	T[]	✅	The full list of items to render
height	number	✅	The height (in pixels) of the scrollable container
itemHeight	number	✅	The fixed height (in pixels) of each list item
renderItem	(item: T, index: number) => JSX.Element	✅	Function that renders a single item
overscan	number	❌	Number of items to render above/below viewport (default: 5)
💡 Example Use Case
You’re building a dashboard or infinite scroll feed and need to display 10,000+ rows (e.g., users, logs, products). Without virtualization, React will render all 10,000 elements — causing slow initial loads and scroll jank. react-virtual-list solves this by keeping the DOM light and fast.

🛠 Installation for Development
To build or contribute:

bash
Copy
Edit
git clone https://github.com/your-username/react-virtual-list.git
cd react-virtual-list
npm install
npm run build
You can then link it in a local project using:


npm link
cd ../your-app
npm link react-virtual-list
📃 License
MIT © 2025 AmirMohammad Khodabande

🌐 Links
GitHub Repo










