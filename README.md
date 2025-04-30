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

## 🚀 Usage Example

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

| Prop        | Type                                | Description                                          |
|-------------|-------------------------------------|------------------------------------------------------|
| `items`     | `T[]`                               | Array of items to render                            |
| `height`    | `number`                            | Height of the scroll container (px)                 |
| `itemHeight`| `number`                            | Estimated height of each item (px)                  |
| `renderItem`| `(item: T, index: number) => ReactNode` | Render function for each visible item         |
| `overscan`  | `number` (optional, default `5`)    | Extra rows rendered above/below viewport            |
| `className` | `string` (optional)                 | CSS class for the outer container                   |
| `style`     | `React.CSSProperties` (optional)    | Inline styles for the outer container               |

## 📝 License

MIT
