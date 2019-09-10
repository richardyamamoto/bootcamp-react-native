### React Native Component
In ReactJS and React Native, we have two ways to build a component. Stateful
Component and Stateless Component. That means the stateful components are
keeping track of changing data, while stateless components print out what is
given to them via props, or they always render the same thing.

[Stateful and Stateless](https://gist.github.com/richardyamamoto/af4d4a12030c3a657691e8b7322b3065)

---
### Routes
To navigate through the pages, we use the react-navigation as we saw in [Dependencies: Routes](https://github.com/richardyamamoto/bootcamp-react-native/blob/master/notes/DEPENDENCIES.md#routes). The createStackNavigator has second parameter that is a config object, and in this objecti we can set some defaults to our pages header as:
```js
const Routes = createAppContainer(
  createStackNavigator(
    {
      Main,
      User,
    },
    {
      headerLayoutPreset: 'center',
      headerBackTitleVisible: false,
      defaultNavigationOptions: {
        headerStyle: {
          backgroundColor: '#7159c1',
        },
        headerTintColor: '#fff',
      },
    }
  )
);
```
- headerLayoutPreset: Set the alignment of the text (on Android the default is align-left)
- headerBackTitleVisible: The default is to show the last page title on the header
- defaultNavigationOptions: Configurations of the navigation
  - headerStyle: Customize the header
    - backgroundColor: background color
    - headerTintColor: header tint color

**Note:**
On `index.js` we can access the global component called Main an use the method `navigationOptions` to set some configurations:

```js
Main.navigationOptions = {
  title: 'Usuários',
};
```

---
### Api
As we saw in [Depencencies](https://github.com/richardyamamoto/bootcamp-react-native/blob/master/notes/DEPENDENCIES.md#axios), after create the intance of Axios in `src/services/api.js`, let's call the API to we consume some data.

An api consuming always going to be asynchronous, because we are expecting the response. So to handle it functions like:
```js
handleAddUser = async () => {
  const response = await api.get('/api_adress/etc')
}
```

**Note:**
Always using arrow function syntax.

---
### React Native Elements
React Native has elements natives from the device as Keyboard. To use their method we have to import the module from react-native, for exemple:
`import { KeyBoard } from 'react-native'`

- KeyBoard: KeyBoard
- ActivityIndicator: Indicate the loading status based on OS

---
### Input
React native has standards props for TextInput
- autoCorrect: Auto corrects words, the default is true
- autoCapitalize: Use to captalize the first letter
  - Currently used for name
- placeholder: phrase or words placed on input
  - placeholder has self props to be stylized
- value: will receive the value
- onChangeText: possible to capture directly the words written on the field
  - Exemple:
  ```js
  onChangeText={text => this.setState({ newUser: text })}
  ```
- onSubmitEditing: handle the submit after finsh the editing

---
### Buttons
We are using the RectButton as component, that is necessary to import from react-native-gesture-handler
`import {RectButton} from 'react-native-gesture-handler`. Using this button, we have the android effect when pressed.

Properties:
- onPress: analog to onClick. (use the same function of onSubmitEditing)

**Note:**
On styles.js the component must be declared like this:
`export const = styled(RecButton)``;`

---
### List
In another hand compared to ReactJS, in React Native the list does not need to be mapped like: `{users.map(user => {})}`.
Properties:

- data: used to refer from where the data come from
- keyExtractor: like in ReacJS using the map method, we need to found a unique key for the elements
- renderItem: this propertie we pick as parameter **item** from an object and the return of the function is our elements rendered, look at the following exemple:

```js
renderItem={({ item }) => (
  <User>
    <Avatar source={{ uri: item.avatar }} />
    <Name>{item.name}</Name>
    <Bio>{item.bio}</Bio>
    <ProfileButton onPress={() => {}}>
      <ProfileButtonText>Ver perfil</ProfileButtonText>
    </ProfileButton>
  </User>
)}
```

**Note:**
The source of the picture must be declared as a uri propertie form an object

---
### Styled Components
This librarie allow us to use CSS inside JavaScript files besides that we can call properties and attributes too.

In React Native as opposed to ReactJS, we can't stylize components inside our main component like:
```js
export const Bio = styled.Text`
  h1 {
    flex:1;
  }
`;
```
**This is not acceptable.**

By the way, in this case we have to create a unique component for each.

The propertie or attribute call from the component is a great way to manipulate data and customization, here is an exemple:
```js
export const Bio = styled.Text.attrs({
  numberOfLines: 2,
})`
  font-size: 13px;
  line-height: 18px;
  color: #999;
  margin-top: 5px;
  text-align: center;
`;
```
In this case the component **Text** has attribute `numberOfLines` and it shows only the number of lines that we set. There are an ocean of attributes for each component that we can search on documentation.

Another exemple is:
```js
export const List = styled.FlatList.attrs({
  showsVerticalScrollIndicator: false,
})`
  margin-top: 20px;
`;
```
The attribute `showsVerticalScrollIndicator` enable or disable the visible of the scroll indicator.

#### Ternary Operator
On Styled Components to call a propertie we can set a Ternary operator to compare the state, for example:
```js
export const SubmitButton = styled(RectButton)`
  opacity: ${props => (props.loading ? 0.7 : 1)};
`;
```
In this case the `opacity` will be changed to 0.7 if the propertie
`loading = true` else `opacity: 1`. Remember to use the `${}` to call JavaScript
inside CSS
