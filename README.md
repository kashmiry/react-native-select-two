# react-native-select-two

## Component like [Select2](https://select2.org/) on web for React Native

![Single select](https://raw.githubusercontent.com/xuho/demo-images/master/react-native-select2-single-select.gif)

## Add it to your project

1. Insall package
   - Using NPM
     `npm install react-native-select-two`
   - or:
   - Using Yarn
     `yarn add react-native-select-two`
2. Install React Native Modal dependence

- Using NPM
  `npm install react-native-modal`
- or
  -Using Yarn
  `yarn add react-native-modal`

3. Import package
   `import Select2 from 'react-native-select-two';`

## Usage

```javascript
import React, { Component } from "react"
import { View, Text, StyleSheet } from "react-native"
import Select2 from "react-native-select-two"

const mockData = [
  { id: 1, name: "React Native Developer", checked: true }, // set default checked for render option item
  { id: 2, name: "Android Developer" },
  { id: 3, name: "iOS Developer" }
]

// create a component
class CreateNewAppointment extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Select2
          isSelectSingle
          style={{ borderRadius: 5 }}
          colorTheme="blue"
          popupTitle="Select item"
          title="Select item"
          data={mockData}
          onSelect={data => {
            this.setState({ data })
          }}
          onRemoveItem={data => {
            this.setState({ data })
          }}
        />
      </View>
    )
  }
}
```

### Multiple select

![Multiple select](https://raw.githubusercontent.com/xuho/demo-images/master/react-native-select2-multipe-select.gif)

## Properties

| Property name             | Type           | Default                         | Description                                                                                 |
| ------------------------- | -------------- | ------------------------------- | ------------------------------------------------------------------------------------------- |
| **style**                 | _Object_       | none                            | Custom style for component                                                                  |
| **modalStyle**            | _Object_       | none                            | Custom style for modal                                                                      |
| **title**                 | _String_       | none                            | String display when you don't select any item                                               |
| **data**                  | _Array_        | \*required                      | Datasource of list options: an array of objects (each object have `name` and `id` property) |
| **onSelect**              | _Function_     | none                            | The callback function trigger after you press select button                                 |
| **onRemoveItem**          | _Function_     | none                            | The callback function trigger after you press tags to remove them                           |
| **popupTitle**            | _String_       | none                            | Title of modal select item                                                                  |
| **colorTheme**            | _string/color_ | #16a45f                         | Color for componet                                                                          |
| **isSelectSingle**        | _Bool_         | false                           | Selelect only one option                                                                    |
| **showSearchBox**         | _Bool_         | true                            | Show or hide search field                                                                   |
| **cancelButtonText**      | _string_       | Hủy                             | Cancel button text title                                                                    |
| **selectButtonText**      | _String_       | Chọn                            | Select button text title                                                                    |
| **searchPlaceHolderText** | _String_       | Nhập vào từ khóa                | Placeholder text for search field                                                           |
| **listEmptyTitle**        | _String_       | Không tìm thấy lựa chọn phù hợp | Title to show when there's no item to be render                                             |
| **defaultFontName**       | _String_       | none                            | Set custom font for all component                                                           |
| **selectedTitleStyle**    | _Object_       | none                            | Set custom style for display selected title text                                            |
| **buttonTextStyle**       | _Object_       | none                            | Set custom button text style                                                                |
| **buttonStyle**           | _Object_       | none                            | Set custom button style                                                                     |
| **imageComponent**          | _Function_     | none                            | Attach your preferred image component to this function.                           |
| **isRTL**           | _Bool_       | I18nManager.isRTL                            | Disable or enable RTL support                                                                     |

## Attaching an image component
Using `imageComponent` prop will allow you to pass an image component to each list item.
### 1- Add image property to your data 
Add an `image` property with a url to your image source, in your list of data.
```
const mockData = [
  { id: 1, name: "Saudi Arabia", checked: true, image: 'flag_saudi_arabia.png' }, // set default checked for render option item
  { id: 2, name: "Peru", image: 'flag_peru.png'  },
  { id: 3, name: "Costa Rica", image: 'flag_costa_rica.png'  }
]
```

### 2- Pass your chosen image component
Add it to `<Select2>` component as a prop (`imageComponent`).
```
imageComponent={(imageSrc) =>
    <Image
        style={{ width: 22, height: 22}
        source={{ uri: imageSrc }}
    />
}
```
![Image component](https://user-images.githubusercontent.com/4423561/71541394-24381880-2950-11ea-84aa-299593b79eef.gif)

**MIT Licensed**
