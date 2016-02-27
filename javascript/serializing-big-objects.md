# Serializing big objects

- **Requirement**: 
  - Serialize a big (100mb) javascript object into a string so it can be saved into redis
  - Blocking while serializing is okay, blocking while deserializing is NOT.
- **`JSON`**
  - :+1: Native
  - :+1: Pretty fast (~1s)
  - :-1: Blocking the event loop
- **[`msgpack`](https://www.npmjs.com/package/msgpack)**
  - :-1: Slow (about 5x as slow as JSON)
- **[`BSON`](https://www.npmjs.com/package/bson)**
  - :-1: Doesnt handle objects bigger than 17mb in the JS version
- **[`Response.json()`](http://azimi.me/2015/07/30/non-blocking-async-json-parse.html?utm_source=javascriptweekly&utm_medium=email)**
  - :-1: Not available in node.js
- **[`json-parse-stream`](https://www.npmjs.com/package/json-parse-stream)**
  - :-1: Slow
  - :-1: Overhead of building the object again
  