# chatBasic

## vue와 socket.io를 활용한 채팅방 구현 (socket.io-client)
 * npm install
 * npm run serve
 
## server 코드
 * npm init
 * npm express
 * npm socket.io
 * node app.js
 
```javascript
// app.js
const express = require('express');


const app = express();



const server = app.listen(3001, function() {
    console.log('server running on port 3001');
});


const io = require('socket.io')(server);

io.on('connection', function(socket) {
    console.log(socket.id)
    socket.on('SEND_MESSAGE', function(data) {
        io.emit('MESSAGE', data)
    });
});
```

