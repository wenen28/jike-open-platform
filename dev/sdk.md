# 开发文档

####  ⚠️IMPORTANT ⚠️

You need to [download chrome developer plugin](https://cdn.ruguoapp.com/open-service/jike-open-extension.crx) first. 

### Installation

```bash
npm install @jike/open-sdk --save
```

### Configuration

{% code-tabs %}
{% code-tabs-item title="main.ts" %}
```typescript
import { JikeOpenSDK } from '@jike/open-sdk'
// FIRST OF ALL: apply for your application at jike open platform.
// replace <OPEN_APP_ID> with your openAppId.
const sdk = new JikeOpenSDK(<OPEN_APP_ID>)
// or
const sdk = new JikeOpenSDK({
  openAppId: <OPEN_APP_ID>
})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### API

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

