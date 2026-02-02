# Scroll-to-mapped-Components-CORRECTLY-in-React---Mapping-react-refs

- https://www.youtube.com/watch?v=vIA10kmNXwU
- https://raw.githubusercontent.com/RodrigoMvs123/Scroll-to-mapped-Components-CORRECTLY-in-React---Mapping-react-refs/main/README.md
- https://github.com/RodrigoMvs123/Scroll-to-mapped-Components-CORRECTLY-in-React---Mapping-react-refs/blame/main/README.md

**App.js**

```javascript
import { useState, useEffect, createRef } from 'react'
import Card from './Components/Card'
const App = () => {
    const cardIds = [0,1,2,3]
    const [unClickedCardIds, setUnClickedCardIds] = useState(cardId)
   const refs = cardIds.reduce((acc, value) => {
        acc[value] = createRef()
        return acc
   }, {})
   })
        console.log(refs)
    useEffect(() => {
        if (unClickedCardIds.length> 0 && (unClickedCardIds.length < cardIds.length)) {
        // scroll to highest unClickedCardIds
       const highestId = Math.min(...unClickedCardIds)
       console.log('highest', highest)
       refs[highestId].current.scrollIntoView({
           behavior: "smooth"
       })
        }
    }, [unClickedCardIds, cardIds.length, refs])
    return (
        <div>
            <header></header>
            {cardIds.map(cardId => (
                <Card
                     key={cardId}
                     cardId={cardId}
                     unClickedCardIds={unClickedCardIds}
                     setUnclickedCardIds={setUnclickedCardIds}
                     ref={refs[cardId]}
                
            />
            ))}
        </div>
    )
}
export default App
```

**Card.js**

```javascript
import { forawedRef } from 'react'
const Card = ({cardId, unClickedCardIds, setUnClickedCardIds}, ref) => {
    const handleClick = () => {
        setUnClickedCardIds(unClickedCardIds.filter(id => id !==cardId))
    }
    return (
        <article ref={ref} className="card" onClick={handleClick}>
            {cardId}
        </article>
    )
}       
export default forwardRef(Card) 
```

**Index.css**

```css
header {
    height: 500px;
    
}
.card {
    height: 1200px;
    width: 600px;
    background-color: red;
    margin: 20px;
    color: white;
    font-size: 50px;
    text-aligh: center;
    
}
```

**Index.js**

```javascript
import React from 'react'
import ReactDOM from 'react-dom/client'
import './index.css'
import App from './App'
const root = ReactDOM.createRoot(document.getElementById(('root'))
root.render(
    <React.StrictMode>
        <App/>
</React.StrictMode>
)
```
