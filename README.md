
# React Mini List

A lightweight, fast, and customizable virtualized list component for React. It helps render large lists efficiently by only rendering visible items, improving performance.

## 📦 Installation

```bash
npm install react-mini-list
```

or using Yarn:

```bash
yarn add react-mini-list
```

## 🔄 Dynamic Virtual List Example (Infinite Scroll)

This example demonstrates how to dynamically load more data as the user scrolls. It simulates an infinite scroll experience using `setTimeout` to mimic an API request:

```tsx
import React, { useState, useEffect } from 'react';
import { VirtualList } from 'react-mini-list';

const generateItems = (start: number, count: number) =>
  Array.from({ length: count }, (_, i) => `Item ${start + i}`);

function DynamicVirtualList() {
  const [items, setItems] = useState<string[]>(() => generateItems(0, 50));
  const [loading, setLoading] = useState(false);

  const loadMoreItems = () => {
    setLoading(true);
    setTimeout(() => {
      setItems((prev) => [...prev, ...generateItems(prev.length, 50)]);
      setLoading(false);
    }, 1000); // simulate API delay
  };

  return (
    <VirtualList
      items={items}
      height={400}
      itemHeight={40}
      overscan={10}
      renderItem={(item, index) => (
        <div
          style={{
            padding: 10,
            borderBottom: '1px solid #eee',
            background: index % 2 ? '#fafafa' : '#fff',
          }}
        >
          {item}
          {index === items.length - 1 && !loading && (
            <button onClick={loadMoreItems} style={{ marginTop: 8 }}>
              Load More
            </button>
          )}
          {index === items.length - 1 && loading && (
            <div style={{ marginTop: 8 }}>Loading...</div>
          )}
        </div>
      )}
    />
  );
}

export default DynamicVirtualList;
```

## 🚀 Basic Usage Example

```tsx
import React from 'react';
import { VirtualList } from 'react-mini-list';

const items = Array.from({ length: 10000 }, (_, i) => `Item ${i}`);

function App() {
  return (
    <VirtualList
      items={items}
      height={400}
      itemHeight={35}
      renderItem={(item) => (
        <div style={{ padding: 8, borderBottom: '1px solid #ddd' }}>
          {item}
        </div>
      )}
    />
  );
}

export default App;
```

## 📚 Props

| Prop        | Type                                    | Description                                          |
|-------------|-----------------------------------------|------------------------------------------------------|
| `items`     | `T[]`                                   | Array of items to render                            |
| `height`    | `number`                                | Height of the scroll container (px)                 |
| `itemHeight`| `number`                                | Estimated height of each item (px)                  |
| `renderItem`| `(item: T, index: number) => ReactNode` | Render function for each visible item               |
| `overscan`  | `number` (optional, default `5`)        | Extra rows rendered above/below viewport            |
| `className` | `string` (optional)                     | CSS class for the outer container                   |
| `style`     | `React.CSSProperties` (optional)        | Inline styles for the outer container               |

## 📝 License

MIT
