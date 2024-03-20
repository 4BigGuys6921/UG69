# UG69

const http = require('http');
const request = require('request');

const port = 8080;

http.createServer((clientReq, clientRes) => {
  const options = {
    url: clientReq.url,
    headers: clientReq.headers,
  };

  request(options, (err, res, body) => {
    if (err) {
      clientRes.writeHead(500);
      clientRes.end(err.message);
    } else {
      clientRes.writeHead(res.statusCode, res.headers);
      clientRes.end(body);
    }
  });
}).listen(port, () => {
  console.log(`Proxy server running on port ${port}`);
});
