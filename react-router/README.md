# Install
```npm install react-router-dom```


## index.js
```
import {BrowserRouter} from "react-router-dom";
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
    <React.StrictMode>
      <App />
    </React.StrictMode>
  </BrowserRouter>
);```

## App.js
```import {Routes, Route} from "react-router-dom"
function App() {
  return (
    <div className="App">   
      <header>
        <Navbar />
      </header>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/:slug" element={<Post />} />
        <Route path="*" element={<Post />} />
      </Routes>
    </div>
  )   
}
export default App```

## Navbar
```import {Link} from "react-router-dom"
export default function Navbar() {
    return (
        <nav className="navbar navbar-dark bg-dark">
            <a className="navbar-brand" href="/">REACT DEV</a>
            <div className="navbar-collapse">
                <ul className="navbar-nav">
                    <li className="nav-item"><Link to="/">Home</Link></li>
                    <li className="nav-item"><Link to="/about">A propos</Link></li>
                    <li className="nav-item"><Link to="/:slug">Slug</Link></li>
                </ul>
            </div>
        </nav>
    )
}```


