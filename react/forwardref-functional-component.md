# ForwardRef Functional Component

{% code title="CustomComponent.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
import {
  ComponentType,
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

type CustomComponentWithRefProps = RefProps;

const CustomComponent = props => {
  console.log("props", props);

  return <View></View>;
};

const CustomComponentMemo = memo(CustomComponent);

const CustomComponentWithRef = forwardRef<RefProps, Props>((props, ref) => {
  const componentRef = useRef<ComponentType>(null);

  useImperativeHandle(ref, () => ({
    // 定义组件实例的方法和属性
    func() {
      console.log("call func");
    },
  }));

  return (
    <CustomComponentMemo
      ref={componentRef}
      {...props}
    />
  );
});

CustomComponentWithRef.displayName = "CustomComponentWithRef";

export {
  CustomComponent,
  CustomComponentMemo,
  CustomComponentWithRef,
  CustomComponentWithRefProps,
};
```
{% endcode %}

{% code title="Page.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
import { createRef } from "react";
import { View } from "@tarojs/components";

export const Page = () => {
  const customComponentRef = createRef<CustomComponentWithRefProps>();

  const handleFunc = () => {
    console.log(customComponentRef.current?.func());
  };

  return (
    <View onClick={handleFunc}>
      <CustomComponentWithRef
        ref={customComponentRef}
        from="Page"
      />
    </View>
  );
};
```
{% endcode %}
