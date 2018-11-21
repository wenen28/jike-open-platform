# 开发文档

####  ⚠️IMPORTANT ⚠️

You need to [download the chrome developer plugin](https://cdn.ruguoapp.com/open-service/jike-open-extension.crx) first. 

### Installation

```bash
npm install @jike/open-sdk --save
```

### Configuration

{% code-tabs %}
{% code-tabs-item title="main.ts" %}
```typescript
import { JikeOpenSDK } from '@jike/open-sdk'
// FIRST OF ALL: get your app id from jike open platform.
// Replace <OPEN_APP_ID> with your app id.
const sdk = new JikeOpenSDK(<OPEN_APP_ID>)

```
{% endcode-tabs-item %}
{% endcode-tabs %}

* ⚠️you should call other methods\(like `sdk.getUserInfo`\) after  `sdk.ready()` . For Example:

{% code-tabs %}
{% code-tabs-item title="main.ts" %}
```typescript
const init = async () => {
  await sdk.ready()
  ReactDOM.render(<App />, document.getElementById('root'))
}
if (sdk.isInJikeApp()) {
  init()
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### API

#### `sdk.isInJikeApp()`

* App version &gt;= 4.15.0.
* Return a boolean represent for whether runtime is inside Jike App.

#### `sdk.getUserInfo()`

* App version &gt;= 4.15.0.
* Get current user info.

```typescript
sdk.getUserInfo(): Promise<UserInfo>

sdk.getUserInfo().then(({user}) => {
  console.log(user)
  /* 
  {
    id: "SunskyXH",
    isLoginUser: true,
    screenName: "香香鸡"
    gender: "MALE",
    profileImage: {
      format: "jpeg"
      middlePicUrl: "https://cdn.ruguoapp.com/FotVPHP2tLYHZ3W4zk3urw1GVD9i.jpg?imageMogr2/auto-orient/format/jpeg/thumbnail/300x300%3E/quality/30"
      picUrl: "https://cdn.ruguoapp.com/FotVPHP2tLYHZ3W4zk3urw1GVD9i.jpg?imageMogr2/auto-orient/format/jpeg/thumbnail/1000x1000%3E/quality/30"
      thumbnailUrl: "https://cdn.ruguoapp.com/FotVPHP2tLYHZ3W4zk3urw1GVD9i.jpg?imageMogr2/auto-orient/format/jpeg/thumbnail/120x120%3E/quality/30"
    },
  }
  */
  })
```

### Interface

#### `UserInfo`

```typescript
interface UserInfo {
  user: {
    id: string,
    isLoginUser: boolean,
    screenName: string,
    gender: 'MALE' | 'FEMALE'
    profileImage: {
      format: string,
      picUrl: string,
      middlePicUrl: string,
      thumbnailUrl: string,
    }
  }
}
```

