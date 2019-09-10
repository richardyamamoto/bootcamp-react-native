### Eslint Prettier Babel
First of all install the eslint `yarn add eslint -D` as devDependencies, and after install the prettier dependencies
`yarn add prettier eslint-config-prettier eslint-plugin-prettier -D`, and install bebel config too `yarn add babel-eslint -D`

[Configs](https://gist.github.com/richardyamamoto/bf72b72bfb5806c0a55bc8d5aeb0b0fc)

### Reactotron
A desktop app for inspecting your React JS and React Native projects.

This dependencie allow to console.log() inside the application. Intall `yarn add reactotron-react-native`, after intallation
inside folder `src` create `config/ReactotronConfig.js`

[ReactotronConfig.js](https://gist.github.com/richardyamamoto/4f57f7bf71d8fb8c7afc1d6b0497db86)

### Routes

Install :
- react-navigation: to navigate through pages
- react-native-gesture-handler: handle the user gestures
- react-native-reanimated: to treat animation on navigate action
- react-navigation-stack: to use the stack navigation

`yarn add react-navigation react-native-gesture-handler react-native-reanimated`

**Note:**
On Android must paste the following lines inside `MainActivity.java`

[Docs](https://kmagiera.github.io/react-native-gesture-handler/docs/getting-started.html)

[MainActivity.java](https://gist.github.com/richardyamamoto/4aa77d770a79089a248eb1a2b1714b7b)

_Erase the + signal_

#### createAppContainer
Similar to BrowserRouter that was used on reactJS, it contains the
configurations to our routes works and create a header.
Always need to be before our routes.

#### createStackNavigator
Allow the user to navigate as a stack. So it is possible to return to the last
navigated page and it will not be erased

`yarn add react-navigation-stack`

#### createSwitchNavigator
When navigate to the next page, the last one will be erased

### Styled Components
The styled components that we are using is very similar to the ReactJS except to some little diferences

`yarn add styled-components`

### Icons
To use the most famous icons let's install `yarn add react-native-vector-icons`, don't forget to add the link
`yarn react-native link react-native-vector-icons`and remount the app `yarn react-native run-android`
the application

### Axios
We are going to use the same librarie that was used on ReactJS
`yarn add axios`

### Local Storage
To prevent the lost of data when refresh the application, we use the async-storage lib, to install
`yarn add @react-native-community/async-storage`

**Note:**
After installing, you must remount the application `yarn react-native run-android`
