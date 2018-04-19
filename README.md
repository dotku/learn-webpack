# learn-webpack
A repo to share what I have learn on webpack

## how to trun off warning for dev mode?  
React with Bable will create > 1m file insize, but after compress, it will decreased to < 100k.
It is annoy to display the warning the warning message. We can disabled it by using following 
setting in webpack.config.js file.
```
performance: {
  hints: process.env.NODE_ENV === 'production' ? "warning" : false
}
```
