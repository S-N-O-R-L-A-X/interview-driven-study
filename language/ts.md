# Typescript

## Typescript 泛型

## 发布-订阅模式
对象间一对多的依赖关系，当一个对象的状态发送改变时，所有依赖于它的对象都将得到状态改变的通知。
订阅者（Subscriber）把自己想订阅的事件注册（Subscribe）到调度中心（Event Channel），当发布者（Publisher）发布该事件（Publish Event）到调度中心，也就是该事件触发时，由调度中心统一调度（Fire Event）订阅者注册到调度中心的处理代码。

应用程序需要「向大量消费者广播信息」。例如微信订阅号就是一个消费者量庞大的广播平台。
应用程序需要与一个或多个独立开发的应用程序或服务「通信」，这些应用程序或服务可能使用不同的平台、编程语言和通信协议。
应用程序可以向消费者发送信息，而不需要消费者的实时响应。

### 实现思路
创建一个对象
在该对象上创建一个缓存列表（调度中心）
on 方法用来把函数 fn 都加到缓存列表中（订阅者注册事件到调度中心）
emit 方法取到 arguments 里第一个当做 event，根据 event 值去执行对应缓存列表中的函数（发布者发布事件到调度中心，调度中心处理代码）
off 方法可以根据 event 值取消订阅（取消订阅）
once 方法只监听一次，调用完毕后删除缓存函数（订阅一次）

### 代码
```ts
interface Publisher {
  subscriber: string;
  data: any;
}

interface EventChannel {
  on  : (subscriber: string, callback: () => void) => void;
  off : (subscriber: string, callback: () => void) => void;
  emit: (subscriber: string, data: any) => void;
}

interface Subscriber {
  subscriber: string;
  callback: () => void;
}

class ConcreteEventChannel implements EventChannel {
  // 初始化订阅者对象
  private subjects: { [key: string]: Function[] } = {};

  // 实现添加订阅事件
  public on(subscriber: string, callback: () => void): void {
    console.log(`收到订阅信息，订阅事件：${subscriber}`);
    if (!this.subjects[subscriber]) {
      this.subjects[subscriber] = [];
    }
    this.subjects[subscriber].push(callback);
  };

  // 实现取消订阅事件
  public off(subscriber: string, callback: () => void): void {
    console.log(`收到取消订阅请求，需要取消的订阅事件：${subscriber}`);
    if (callback === null) {
      this.subjects[subscriber] = [];
    } else {
      const index: number = this.subjects[subscriber].indexOf(callback);
      ~index && this.subjects[subscriber].splice(index, 1);
    }
  };
  
  // 实现发布订阅事件
  public emit (subscriber: string, data = null): void {
    console.log(`收到发布者信息，执行订阅事件：${subscriber}`);
    this.subjects[subscriber].forEach(item => item(data));
  };
}

class ConcretePublisher implements Publisher {
  public subscriber: string = "";
  public data: any; 
  constructor(subscriber: string, data: any) {
    this.subscriber = subscriber;
    this.data = data;
  }
}

class ConcreteSubscriber implements Subscriber {
  public subscriber: string = "";
  constructor(subscriber: string, callback: () => void) {
    this.subscriber = subscriber;
    this.callback = callback;
  }
  public callback(): void { };
}


/* 运行示例 */
const sub1 = new ConcreteSubscriber(
  "running",
  () => { 
    console.log("订阅者 sub1 订阅事件成功！执行回调~");
  }
);

const sub2 = new ConcreteSubscriber(
  "swimming",
  () => { 
    console.log("订阅者 sub2 订阅事件成功！执行回调~");
  }
);

const sub3 = new ConcreteSubscriber(
  "swimming",
  () => { 
    console.log("订阅者 sub3 订阅事件成功！执行回调~");
  }
);

const pub = new ConcretePublisher(
  "swimming",
  {message: "pub 发布消息~"}
);

const eventBus = new ConcreteEventChannel();
eventBus.on(sub1.subscriber, sub1.callback);
eventBus.on(sub2.subscriber, sub2.callback);
eventBus.on(sub3.subscriber, sub3.callback);

// 发布者 pub 发布 "swimming"相关的事件
eventBus.emit(pub.subscriber, pub.data); 
eventBus.off (sub3.subscriber, sub3.callback);
eventBus.emit(pub.subscriber, pub.data);

/*
输出结果：
[LOG]: 收到订阅信息，订阅事件：running
[LOG]: 收到订阅信息，订阅事件：swimming
[LOG]: 收到订阅信息，订阅事件：swimming
[LOG]: 收到发布者信息，执行订阅事件：swimming 
[LOG]: 订阅者 sub2 订阅事件成功！执行回调~ 
[LOG]: 订阅者 sub3 订阅事件成功！执行回调~ 
[LOG]: 收到取消订阅请求，需要取消的订阅事件：swimming 
[LOG]: 收到发布者信息，执行订阅事件：swimming 
[LOG]: 订阅者 sub2 订阅事件成功！执行回调~ 
*/
```

### 使用例子
Node.js EventEmitter 中的 on 和 emit 方法；
Vue 中的 $on 和 $emit 方法

### 
「观察者模式」和「发布-订阅模式」差别在于「有没有一个中央的事件总线」。如果有，我们就可以认为这是个「发布-订阅模式」。如果没有，那么就可以认为是「观察者模式」。因为其实它们都实现了一个关键的功能：「发布事件-订阅事件并触发事件」。