# ForwardRef Functional Component

{% code title="CustomComponent.tsx" overflow="wrap" lineNumbers="true" %}
```tsx


import {
  ComponentType,
  createRef,
  forwardRef,
  memo,
  useImperativeHandle,
  useRef,
} from "react";
import { View } from "@tarojs/components";

interface Props {
  // 定义组件的其他 props
  from: string;
}

interface RefProps {
  // 定义组件的实例方法和属性
  func: () => void;
}

const CustomComponentBase = props => {
  console.log("props", props);

  return <View></View>;
};

export const x = memo(CustomComponentBase);

export const CustomComponentRef = forwardRef<RefProps, Props>((props, ref) => {
  const componentRef = useRef<ComponentType>(null);

  useImperativeHandle(ref, () => ({
    // 定义组件实例的方法和属性
    func() {
      console.log("call func");
    },
  }));

  return <CustomComponent ref={componentRef} {...props} />;
});

CustomComponentRef.displayName = "CustomComponent";
```
{% endcode %}

{% code title="Page.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
export const Page = () => {
  const customComponentRef = createRef<RefProps>();

  const handleFunc = () => {
    console.log(customComponentRef.current?.func());
  };

  return (
    <View onClick={handleFunc}>
      <CustomComponentRef
        ref={customComponentRef}
        from="Page"
      />
    </View>
  );
};
```
{% endcode %}
