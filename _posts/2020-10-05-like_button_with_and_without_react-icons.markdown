---
layout: post
title:      "Like button with and  without  react-icons"
date:       2020-10-05 15:01:02 -0400
permalink:  like_button_with_and_without_react-icons
---


Before I found out about react-icons, I added a like feature to my React application in a, I would say, pure React traditional way:
First I created a new component:

```
import React, { Component } from 'react'

class LikeButton extends Component {
    render(){
      return(
          <div>

          </div>
      )
    }
}

export default LikeButton
```

Then I defined a state:

` 
state={ likesCount: 0 }
`

I wanted to set my like button as a heart and if I don’t have any likes to display an empty heart and with the first like the heart will be a full one. Also I wanted to show how many likes I  have. For that I defined a function:

```
displayHeart=()=>{
    {if(this.state.likesCount === 0){
    return <button onClick={this.handleLikeClick}>♡ {this.state.likesCount}</button>}
      else{
      return <button onClick={this.handleLikeClick}>♥ {this.state.likesCount}</button>}}
  }
	
	```

and then render this function :

```
render(){
      return(
          <div>
            {this.displayHeart()}

          </div>
      )
    }
		
```

handleLikeClick function will handle what will happen with each click, changing the state:

```
handleLikeClick=(e)=>{
    e.preventDefault();
    let newLikeClick = this.state.likesCount+1
    this.setState({
      likesCount: newLikeClick
    })
  }
```

Putting everything together your LikeButton component should look like this:

```
import React, { Component } from 'react'

class LikeButton extends Component {
    state={ likesCount: 0 }

    displayHeart=()=>{
        {if(this.state.likesCount === 0){
        return <button onClick={this.handleLikeClick}>♡ {this.state.likesCount}</button>}
          else{
          return <button onClick={this.handleLikeClick}>♥ {this.state.likesCount}</button>}}
      }

    handleLikeClick=(e)=>{
    e.preventDefault();
    let newLikeClick = this.state.likesCount+1
    this.setState({
        likesCount: newLikeClick
    })
    }
    

    render(){
      return(
          <div>
            {this.displayHeart()}
          </div>
      )
    }
}

export default LikeButton
```

The beauty of React is that now you can import this component every where you want.

After implementing this version I came across ‘react-icons’.

Here are the steps I took:
First I installed react_icons:

```
npm install react-icons --save
```

 then I imported the Heart icon:

```
import {FaHeart} from 'react-icons/fa'
```

The state declaration and handleOnClick function will stay the same. I’ve changed just the display of the heart witch now is imported from react-icons and added an  input of radio type:

```
import React, { Component } from 'react'
import {FaHeart} from 'react-icons/fa'

class LikeButtonReactIcons extends Component {
    state={ likesCount: 0 }

    handleLikeClick=(e)=>{
    e.preventDefault();
    let newLikeClick = this.state.likesCount+1
    this.setState({
        likesCount: newLikeClick
      })
    }
  
    render(){
      return(
          <div>
            <label>
                <input type="radio" onClick={this.handleLikeClick}/>
                <FaHeart
                 color = {this.state.likesCount==0 ? "black" : "orange"}
                 size = {18}
                />  {this.state.likesCount}</label>
          </div>
      )
    }
}
export default LikeButtonReactIcons

```

Don’t forget to hide the radio button in the App.css  so just the heart will be visible:

```
input[type ="radio"] {
  display: none;
}

```







