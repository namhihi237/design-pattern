# SINGLETON

1. What is Singleton Pattern?

```
The Singleton pattern ensures that a class has only on instance and provides a global point of access to it.
```

2. Solution

```
2 steps in common
- Make the default constructor private
- Create a static creation method, this method calls the private constructor to create an object and save it in a static field.
```

3. Implement a Singleton

- Javascript

```js
const Singleton = {
	instance: null,
	getInstance: function () {
		if (!this.instance) {
			this.instance = this.createInstance();
		}
		return this.instance;
	},
	createInstance: function () {
		// Your initialization logic here
		return {
			/* Your singleton object properties */
		};
	},
};
```

```js
const mySingleTonInstance = Singleton.createInstance();
```

- Typescript

```ts
class Singleton {
	private static instance: Singleton | null = null;

	private constructor() {
		// Private constructor to prevent instantiation
	}

	public static getInstance(): Singleton {
		if (!this.instance) {
			this.instance = new Singleton();
		}
		return this.instance;
	}

	public doSomething(): void {
		console.log('Doing something');
	}
}
```

```ts
const mySingletonInstance: Singleton = Singleton.getInstance();
mySingletonInstance.doSomething();
```

4. Example with real case

Implement singleton with redis

```ts
import Redis from 'ioredis';

class RedisSingleton {
	private static instance: RedisSingleton | null = null;
	private redisClient: Redis.Redis;

	private constructor() {
		this.redisClient = new Redis();
	}

	public static getInstance(): RedisSingleton {
		if (!this.instance) {
			this.instance = new RedisSingleton();
		}
		return this.instance;
	}

	public readonly client = this.redisClient;
}

export default RedisSingleton;
```

```ts
const redisClient = RedisSingleton.getInstance().client;
redisClient.set('key', 'value');
```
