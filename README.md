# ssh-exec

Execute a script over ssh using Node.JS and pipe to and from it

```
npm install git+https://github.com/ipburger/ssh-exec.js.git
```

This fork merges the most helpful commits across github on ssh-exec

## Latest Fixes

- Occasional truncated stdout 
- ssh agent forwarding



## Usage

``` js
var exec = require('ssh-exec')

// using ~/.ssh/id_rsa as the private key

exec('ls -lh', 'ubuntu@my-remote.com').pipe(process.stdout)

// or using the more settings

exec('ls -lh', {
  user: 'ubuntu',
  host: 'my-remote.com',
  key: myKeyFileOrBuffer,
  password: 'my-user-password'
}).pipe(process.stdout)

// or if you want to pipe some data to the remote process

process.stdin
  .pipe(exec('echo try typing something; cat -', 'ubuntu@my-remote.com'))
  .pipe(process.stdout)
```

Optionally there is a callback api as well

``` js
exec('ls -lh', 'ubuntu@my-remote.com', function (err, stdout, stderr) {
  console.log(err, stdout, stderr)
})
```

## Options

Look at [the source](https://github.com/ipburger/ssh-exec.js/blob/47d4cec9c8b92c75471ccdbad5f609ac69a6462d/index.js#L82).

## License

MIT
