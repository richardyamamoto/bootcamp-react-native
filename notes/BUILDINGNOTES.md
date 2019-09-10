### Input
React native has standards props for TextInput
- autoCorrect: Auto corrects words, the default is true
- autoCapitalize: Use to captalize the first letter
  - Currently used for name
- placeholder: phrase or words placed on input
  - placeholder has self props to be stylized
- onChangeText: possible to capture the words written on the field
  - Exemple: 
  ```js
  onChangeText={text => this.setState({ newUser: text })}
  ```
