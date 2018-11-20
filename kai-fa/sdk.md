# 开发文档

####  ⚠️IMPORTANT ⚠️

You need to download developer plugin while developing. Link is on the way.

### Installation

```bash
npm install @jike/open-sdk --save
```

### Configuration

```javascript
import { JikeOpenJsSDK } from 'jike-open-js-sdk'
// FIST OF ALL: apply for your application at jike open platform.
// replace <openAppId> with your openAppId.
const sdk = new JikeOpenJsSDK(<openAppId>)
// or
const sdk = new JikeOpenJsSDK({
  openAppId: <openAppId>
})
```

### API

> sdkInstance.getUserInfo\(\)

* available version 4.15.0

```javascript
sdkInstance.getUserInfo(): Promise<UserInfo>
```

> sdkInstance.getMessages\(\)

* available version 4.15.0

```javascript
sdkInstance.getMessages(): Promise<{
  message: Array<Message>
  count: number
}>
```

### Interface

> UserInfo

```javascript
interface UserInfo {
  user: {
    id: string,
    isLoginUser: boolean,
    screenName: string,
    profileImage: {
      format: string,
      picUrl: string,
      middlePicUrl: string,
      thumbnailUrl: string,
    }
  }
}

type Message = Record<string, any>
```

