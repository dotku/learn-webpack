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

## Modulized style for React
We can have modulized style for react by configing webpack

```
// file app.js
import React from 'react';
import styles from './App.css';

export default class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {test: 'foo'};
  }
  render() {
    return (
      <div className={styles.app}>
        bar
      </div>
    );
  }
}
```
File: webpack.config.js
```
{
      test: /\.css$/,
      use: [
        {
          loader: "css-loader",
          options: {
           modules: true,
           localIdentName: '[path][name]__[local]--[hash:base64:5]'
          }
        }
      ],
      include: path.join(__dirname, 'app')
    }
```

