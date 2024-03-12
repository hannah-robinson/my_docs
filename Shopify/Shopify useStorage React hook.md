```js


await storage.write('key', data.id);

const id = await storage.read('key');

await storage.delete('key');

await requestDeleteGC(await storage.read('key'));

```