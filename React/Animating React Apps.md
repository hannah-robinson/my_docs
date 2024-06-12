# Animating React Apps

# CSS Animation
```css
.challenge-item-details-icon {
  display: inline-block;
  font-size: 0.85rem;
  margin-left: 0.25rem;
  transition: transform 0.3s ease-out; /* This is the property that animates the transform in the other rule. It should always go in the "base" rule that is always applied. The transformation goes in the rule that is turned on and off. We could also use `all` instead of `transform`. The number is the speed and the last bit is the acceleration style */
}

.challenge-item-details.expanded .challenge-item-details-icon {
  transform: rotate(180deg);
}
```
The component receives `isExanded` as a prop. So change this 
`<div className="challenge-item-details">`
to this
`<div className={`challenge-item-details ${isExpanded ? 'expanded' : ''}`}>`
to make the class dynamic


With a modal, if it's not open, so it's not in the DOM, we can't add a transition because there is no initial value to transition from. But we can still animate it by using a CSS animation and defining `@keyframes`


```css
.modal {
  top: 10%;
  border-radius: 6px;
  padding: 1.5rem;
  width: 30rem;
  max-width: 90%;
  z-index: 10;
  animation: slide-up-fade-in 0.3s ease-out forwards; /* forwards means keep the end-state once the animation is done */
}

@keyframes slide-up-fade-in {
  0% {
    transform: translateY(30px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}
```

## Limitations of CSS animation
You can animate the appearance of items, like the modal above, but you can't animate the disappearance with just CSS. Also, some complex animations may be possible with just CSS but would be difficult to do that way. And animations done another way, like [[Using Framer Motion with React]] can also look more natural, better obeying physics.


# Using Framer Motion with React
Framer Motion package is built to give *high performance* animations.

`npm i framer-motion`

`import { motion } from 'framer-motion';`

and then change
`<div id="box" />`
to
 `<motion.div id="box" animate={{x: x, y: y, rotate: rotate}} transition={{duration: 0.3, type: 'spring'}} />`
because this is JS we can shorten `{x: x, y: y, rotate: rotate}` to `{x, y, rotate}`
We have access to these props because we added `motion.` They take an object. In this case we are animating the position along the x axis and the y axis and rotating it. We have states set up for the variable when they change the object will be rendered in its new position.

```js
const [x, setX] = useState(0)
const [y, setY] = useState(0)
const [rotate, setXRotate] = useState(0)
```

