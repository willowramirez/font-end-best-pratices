# react native version problem in gradle

```
def REACT_NATIVE_VERSION = new File(['node', '--print',"JSON.parse(require('fs').readFileSync(require.resolve('react-native/package.json'), 'utf-8')).version"].execute(null, rootDir).text.trim())

allprojects {
    configurations.all {
        resolutionStrategy {
            // Remove this override in 0.65+, as a proper fix is included in react-native itself.
            force "com.facebook.react:react-native:" + REACT_NATIVE_VERSION
        }
    }
}
```
