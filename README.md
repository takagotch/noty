### noty
---
https://github.com/needim/noty

```
npm run dev
npm test
npm run build
npm run brwoserstack
npm run serve-docs

npm install web-push
node sendPushExample.js
```

```js
import Noty from 'noty';
new Noty(
  text: 'Notification text'
).show();
const Noty = require('noty');
new Noty({
  text: 'Notification text'
}).show();
```

```js
new Noty({
  type: 'success',
  layout: 'topRight',
  text: 'Some notification text'
}).show();


new Noty({
  text : 'Some notification text',
  container: '.custom-container'
}).show();

const NotyPush = Noty.Push('/service-worker.js')
  .on('onPermissionGranted', function () {
    console.log('Perm: granted')
  })
  .on('onPermissionDenied', function () {
    console.log('Perm: denied')
  })
  .on('onSubscriptionSuccess', function (subData) {
    console.log('Subscription:', subData)
  })
  .on('onSubscriptionCancel', function (subData) {
    console.log('Subscription: canceled')
  })  
  .on('onWorkerSuccess', function () {
    console.log('Worker: installed')
  })
  .on('onWorkerError', function (err) {
    console.log('Worker: failed', err)
  })
  .on('onWorkerNotSupported', function (err) {
    console.log('Worker: not supported', err)
  })

NotyPush.requestSubscription()


const webpush = require('web-push')

const vapidKeys = webpush('YOUR-SERVER-KEY-FROM-FIREBASE-CONSOLE')

webpush.setGCMPIKey('YOUR-SERVER-KEY-FROM-FIREBASE-CONSOLE')

webpush.setVapidDettails(
  'mailto:your@email.com',
  vapidKeys.publicKey,
  vapidKeys.privateKey
)

const pushSubscription = {
  endpoint: '',
  keys: {
    auth: '',
    p256dh: ''
  }
}

webpush.sendNotification(pushSubscription, JSON.stringify({
  title: 'Noty title',
  body: 'Noty body',
  icon: 'https://your-icon0-url.png',
  image: 'https://your-image-url.png',
  url: 'http://ned.im/noty/?ref=webPushTest',
  actions: [
    {action: 'actionYes', 'title': 'Yes', 'icon': 'https://your-icon1-url.png'}
    {action: 'actionNo', 'title': 'No', 'icon': 'https://your-icon2-url.png'}
  ]
}))

NotyPush.getPermissionStatus() === 'granted'
NotyPush.getPermissionStatus() === 'default'
NotyPush.getPermissionStatus() === 'denied'

NotyPush.isSWRegistered() === true
```

