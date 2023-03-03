# Layout Class Component

{% code title="ParentComponent.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
// ParentComponent.tsx

import React, { Component } from "react";
import { LayoutRectangle } from "react-native";
import ChildComponent from "./ChildComponent";

class ParentComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      layout: null,
    };

    this.handleChildLayout = this.handleChildLayout.bind(this);
  }
  handleChildLayout = (layout: LayoutRectangle) => {
    // 处理子组件layout变化的逻辑
    console.log(layout);
    this.setState({ layout });
  };

  render() {
    return <ChildComponent onLayout={this.handleChildLayout} />;
  }
}

export default ParentComponent;
```
{% endcode %}

{% code title="ChildComponent.tsx" overflow="wrap" lineNumbers="true" %}
```tsx
// ChildComponent.tsx

import React, { Component } from "react";
import { LayoutRectangle, View } from "react-native";

interface IProps {
  onLayout: (layout: LayoutRectangle) => void;
}

class ChildComponent extends Component<IProps> {
  handleLayout = event => {
    const layout = event.nativeEvent.layout;
    this.props.onLayout(layout);
  };

  render() {
    return <View onLayout={this.handleLayout}>{/* 子组件的内容 */}</View>;
  }
}

export default ChildComponent;
```
{% endcode %}
