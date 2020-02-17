# react-native-upswipe

[![NPM version](https://badge.fury.io/js/react-native-backgroud-shapes.svg)](https://npmjs.org/package/react-native-backgroud-shapes) [![GitHub license](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://raw.githubusercontent.com/kevoj/react-native-backgroud-shapes/master/LICENSE)

> Beautiful Card Swiper to React Native 

### Examples
![screen capture](https://res.cloudinary.com/kush636/image/upload/v1581925084/upswipe.gif)

### Installation

**Yarn**

```bash
yarn add react-native-upswipe
```

**Npm**

```bash
npm i  react-native-upswipe
```

### Usage

```javascript
import React, {PureComponent} from 'react';
import {View, Text, StyleSheet} from 'react-native';
import Upswipe from 'react-native-upswipe';

class App extends PureComponent {
  constructor(props) {
    super(props);
    this.state = {
      serverData: [],
    };
    const apiKey = 'enter your api key ';
    const pageSize = 20;
    const url = `https://newsapi.org/v2/top-headlines?country=in&apiKey=${apiKey}`
    fetch(`${url}`)
      .then(response => response.json())
      .then(responseJson => this.setState({serverData: responseJson.articles}))
      .catch(err => {
        alert(err, 'Sorry for error');
      });
  }
  renderCard(item) {
    return (
      <View style={{alignSelf: 'center'}}>
        <Card key={item.title} image={{uri: item.urlToImage}}>
          <Text style={{marginBottom: 10, height: 50, width: null}}>
            {item.description}
          </Text>
        </Card>
      </View>
    );
  }

  renderNoMoreCards() {
    return (
      <View
        style={{
          height: '100%',
          width: '100%',
          justifyContent: 'center',
          alignItems: 'center',
          backgroundColor: 'pink',
        }}>
        <Text>No More News at this Post Please come after some time</Text>
      </View>
    );
  }

  render() {
    return (
      <View style={styles.container}>
        <Upswipe
          data={this.state.serverData}
          renderCard={this.renderCard}
          renderNoMoreCards={this.renderNoMoreCards}
        />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});
export default App;

```

### Options/Props

```javascript

<Upswipe
          data={this.state.serverData}
          renderCard={this.renderCard}
          renderNoMoreCards={this.renderNoMoreCards}
/>


## License

MIT © [Kush Kumar](https://github.com/kush11/react-native-upswipe.git)