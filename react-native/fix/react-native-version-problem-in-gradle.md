# react native version problem in gradle

### 编译错误

Module was compiled with an incompatible version of Kotlin. The binary version of its metadata is 1.6.0, expected version is 1.4.1.

### 排查出来的问题

由于 gradle 的插件依赖树通过`com.facebook.react:react-native:+`代码将`react-native`顶到了最新的`0.71.0-RC.0`版本，导致出现变异无法通过

### 官方 issue

[地址](https://github.com/facebook/react-native/issues/35249)

### 解决方案

将 gradle 所有 project 里的`react-native`锁定为当前 package.json 内申明的版本

```
// file path: android/build.gradle

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
