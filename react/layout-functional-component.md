# Layout Functional Component

{% code title="Layout.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
// Layout.tsx

import { View } from "react-native";

interface IProps {
  children;
  onLayout;
}

export const Layout = ({ children, onLayout }: IProps) => {
  const handleLayout = event => {
    const { x, y, width, height } = event.nativeEvent.layout;
    onLayout && onLayout({ x, y, width, height });
  };

  return <View onLayout={handleLayout}>{children}</View>;
};
```
{% endcode %}

{% code title="useLayout.ts" overflow="wrap" lineNumbers="true" %}
```tsx
// useLayout.ts

export const useLayout = () => {
  const [layout, setLayout] = useState(null);

  const onLayout = useCallback(layout => {
    setLayout(layout);
  }, []);

  return [layout, onLayout];
};
```
{% endcode %}

{% code title="MyComponent.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
// MyComponent.tsx

import { useCallback, useState } from "react";
import { View, Text } from "react-native";
import { Layout } from "./Layout";
import { useLayout } from "./useLayout";

const MyComponent = () => {
  // method 1: no effect
  const [layout, handleLayout] = useLayout();

  // method 2: has effect
  const [layout, setLayout] = useState(null);
  const handleLayout = layout => {
    setLayout(layout);
    // Side Effect
  };

  return (
    <Layout onLayout={handleLayout}>
      <Text>My Component</Text>
    </Layout>
  );
};
```
{% endcode %}
