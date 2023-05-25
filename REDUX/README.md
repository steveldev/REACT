# Install
``npm i -s redux react-redux @reduxjs/toolkit @redux-devtools/extension``

## index.js
``
//...
import {Provider} from "react-redux"
import {configureStore} from "@reduxjs/toolkit"
import rootReducer from './reducers'

const store = configureStore({
  reducer: rootReducer,
  devTools: true
})

  <Provider store={store}>
     <App />
  </Provider>
``

## ./src/reducers/index.js
``
import {combineReducers} from "redux"
import postReducer from "./post.reducer"
export default combineReducers({
    postReducer
})
``

## ./src/reducers/post.reducer.js
``const initialState = {}
export default function postReducer(state = initialState, action) {
    switch(action.type) {
        case "GET_POSTS":
            return action.payload
        default:
            return state
    }
}``
  
## ./src/actions/post.action.js
export const GET_POSTS = "GET_POSTS"
export const getPosts = () => {
    return (dispatch) => {
        fetch("https://jsonplaceholder.typicode.com/posts")
        .then(response => {
          return response.json()
        })
        .then(data => {
            dispatch({ type: GET_POSTS, payload: data})
        })
    }
}

## App.js
return
<div className="posts">
   {posts.map(post => (  
      <h1>{post.title}</h1>
      <div className="post-content">{post.body}</div>
  ))}
</div>
