# static-server

> simplest static server you ever know

> 10 lines to begin a Node.js static server

## source code

```javascript
	/*
	 * built by slashhuang
	 * 17/2/21
	 * static server 
	 */
	var http =require('http');
	var fs =require('fs');
	http.createServer((req,res)=>{
		let path ="."+req.url;
		fs.access(path,fs.constants.F_OK,(err)=>{
			if(err){
				res.end(`${path} 找不到文件`)
			}else{
				var stream = fs.createReadStream(path);
				stream.pipe(res);
			}	
		})
	}).listen(7000)

```
