# z-index



```typescript
const makeZIndexes = layers =>
  layers.reduce((agg, layerName, index) => {
    const valueName = `z-index-${layerName}`;
    agg[valueName] = index * 100;

    return agg;
  }, {});

const zIndexes = makeZIndexes(["menu", "modal", "error"]);

// {
//   'z-index-menu': 100,
//   'z-index-modal': 200,
//   'z-index-error': 300,
// }
```

```scss
$z-layers-names: ("menu", "modal", "error");
$z-layers: ();

$i: 0;
@each $layer-name in $z-layers-names {
  $i: $i + 1;
  $css-var-name: "z-index-" + $layer-name;

  $z-layers: map-merge(
    $z-layers,
    ($css-var-name: $i),
  );
}

.div {
  z-index: map-get($z-layers, "z-index-error");
}
```
