# react-native-swiper
# Follow link
  https://chat.openai.com/share/d81f5245-ab6d-4f42-961d-3aede9d8a4ce
# Dependencies
  npm install react-native-swiper react-native-svg
# imports
  ```js
import React, { useState } from 'react';
import { View, StyleSheet, Dimensions } from 'react-native';
import Swiper from 'react-native-swiper';
import { SvgXml } from 'react-native-svg';
```
# Define svg icons
```js
const svgIcon1 = `<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg"><circle cx="50" cy="50" r="40" fill="red" /></svg>`;

const svgIcon2 = `<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg"><rect width="80" height="80" fill="blue" /></svg>`;

const svgIcon3 = `<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg"><polygon points="50,5 90,80 10,80" fill="green" /></svg>`;
```
# Component

```js
const SwipableSVGScreen = () => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const handleIndexChanged = (index) => {
    setCurrentIndex(index);
  };

  return (
    <View style={styles.container}>
      <Swiper
        style={styles.wrapper}
        loop={false}
        onIndexChanged={handleIndexChanged}
        showsButtons={true}
        dotStyle={styles.dot}
        activeDotStyle={styles.activeDot}
      >
        <SvgXml xml={svgIcon1} width={Dimensions.get('window').width} height={200} />
        <SvgXml xml={svgIcon2} width={Dimensions.get('window').width} height={200} />
        <SvgXml xml={svgIcon3} width={Dimensions.get('window').width} height={200} />
      </Swiper>
      <View style={styles.indicator}>
        <Text>{`Page ${currentIndex + 1}/3`}</Text>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  wrapper: {},
  dot: {
    backgroundColor: 'rgba(255,255,255,.3)',
    width: 8,
    height: 8,
    borderRadius: 4,
    margin: 3,
  },
  activeDot: {
    backgroundColor: '#fff',
    width: 12,
    height: 12,
    borderRadius: 6,
    margin: 3,
  },
  indicator: {
    position: 'absolute',
    bottom: 20,
    left: 0,
    right: 0,
    alignItems: 'center',
  },
});

export default SwipableSVGScreen;
  ```
