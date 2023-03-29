# React - 语法规则和关键字

## export

### export

```
export const UserManager = "123";
```

Use

```
import { UserManager } from './xxxxx'
```



### export default 

```
export const UserManager = "123";
export default UserManager
```

Use

```
import UserManager from './xxxxx'
```



在React中，`declare`关键字的作用是定义一个不可变的类型声明

```
export declare const themeContext: import("react").Context<FcrTheme>;
```

