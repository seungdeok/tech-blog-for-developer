# 🔍 Input Template

### javascript using "fs" module

```javascript
const fs = require("fs");
const input = fs
	.readFileSync("/dev/stdin")
	.toString()
	.split("\n");
```



### javascript using "readline" module

```javascript
const rl = require("readline")
	.createInterface({
		input: process.stdin,
		output: process.stdout,
	});
const input = [];

rl
	.on("line", function(line){
		// execute after pressing the enter key.
		input.push(line);
	})
	.on("close", function(){
		// execute after pressing the ctrl + c or ctrl + d key.
		console.log(input);
		process.exit();
	});
```
