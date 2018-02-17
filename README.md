# React Native bottom up panel

# Description

This component is a dynamic height and position view. It has a startHeight property that determines the section of the
view that will be showed (generally the toggle button or header).
 
The component has a view with absolute positioning, the position and height of the view is handled by React Native Animations, using linear interpolation between the start and end position defined.
 
* The component has two main parts:
    - header: a transparent view with height = startHeight and an Icon that will be rotated 180 degrees every time that the panel open/close
    - content: a transparent view to put the content.
 
* Why are both components transparent?
       Because there are scenarios when you want to show the background of the main view with some opacity. So
      you have to set the right background for your content and header components.
 
* Why there is no zIndex handling?
       Because the height of the view is dynamic, it starts from the bottom and then covers to topEnd property, so
       the view only covers the part that is visible.


# Usage

**Just add the index.js file wherever you want in your project and import it from your component**

```

import React, {Component} from 'react';
import { Dimensions, FlatList,  Text, View } from 'react-native';
import {Ionicons} from '@expo/vector-icons'; 
import BottomUpPanel from "path/to/index.js";



const {height} = Dimensions.get('window');
const DATA= ["Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component","Some component"];


class SomeComponent extends Component {

   render = ()=>
       <BottomUpPanel
                      content={this.renderBottomUpPanelContent}
                      icon={this.renderBottomUpPanelIcon}
                      topEnd={height-height*0.8}
                      startHeight={80}
                      headerText={"List of items"}
                      headerTextStyle={{color:"white", fontSize: 15}}
                      bottomUpSlideBtn={{display: 'flex',
                                       alignSelf: 'flex-start',
                                       backgroundColor: 'black',
                                       alignItems: 'center',
                                       borderTopColor: 'grey',
                                       borderTopWidth: 5}}
      </BottomUpPanel>

   
                
                
  renderBottomUpPanelContent = () =>
          <View>
               <FlatList style={{ backgroundColor: 'black', opacity: 0.7, flex:1}}
                    data={DATA}
                    renderItem={({item}) =>
                        <Text style={{color:'white', padding:20}}>{item}</Text>}/>
          </View>
          
  renderBottomUpPanelIcon = () =>
        <Ionicons name={"ios-arrow-up"} style={{color:"white"}} size={30}/>        
          
}
```
# Props

- **topEnd**: distance from top of the screen
 - **startHeight**: part of the hidden view that will be visible
 - **content**: function that renders the panel content inside a scroll view
 - **icon**: function that renders the panel slide icon that will be rotated
 - **headerText**: text that is visible at top of the panel
 - **headerTextStyle**: style applied to that text
 - **bottomUpSlideBtn**: style applied to the toggle button
 
 # Demo
 
 ![Alt Text](https://im5.ezgif.com/tmp/ezgif-5-ac705ab625.gif)


# Inspired by: 
  https://github.com/rationalappdev/react-native-bottom-drawer


 

 
