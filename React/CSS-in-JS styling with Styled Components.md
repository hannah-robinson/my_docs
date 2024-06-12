---
date created: 2024-06-12
last updated: 2024-06-12
programming language: css
library or framework: react
programme: 
platform: 
tags:
---
⬆ [[Styling React Apps - Static and Dynamic Styling]]

`npm i styled-components`

In the component's JSX file
`import {styled} from 'styled-components'`
This give you a JS object called `styled`

` styled.div`` `
tagged template - a regular JS feature (not React specific or specific to Styled Components)
It's like a function which receives this template literal as an input. Template literals can be multiline. You add all the styles you want inside the back ticks. You can use standard CSS without camelCase.

e.g. you could replace this
`<div className="controls"></div>`

with

```jsx
const ControlContainer = styled.div`
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
`
const Label = styled.label`
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: ${(props) => props.$invalid ? '#f87171' : '#6b7280'};
  //or
  color: ${({$invalid}) => $invalid ? '#f87171' : '#6b7280'};
`

const Input = styled.input`
  width: 100%;
  padding: 0.75rem 1rem;
  line-height: 1.5;
  background-color: ${({$invalid}) => $invalid ? '#fed2d2' : '#d1d5db'};
  color: ${({$invalid}) => $invalid ? '#f44444' : '#374151'};
  border: 1px solid ${({$invalid}) => $invalid ? '#f73f3f' : 'transparent'};
  border-radius: 0.25rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
`
<ControlContainer>
  <Label $invalid={emailNotValid}>
    <Input type="email" $invalid={emailNotValid} onChange={() => {}}/>
  </Label>
</ControlContainer>

```

This will give you a React component that is automatically a div with those styles applied to it, and internally also uses the special children prop so that it can be wrapped around other content and so that it forwards any props you've added like `className={} type="email" onChange={}`. If you want to use it in other files too, you could move it to a separate file.

It's possible to combine styled components with other approaches to CSS like CSS modules but typically you'd go for one approach for whole app. You can set styles conditionally like in the label and input e.g.s above. The style components allows you to use the props (in this case the `$invalid` prop) in a function that its `label` and `input` functions execute.

You need to be careful not to clash with built in prop names e.g. `invalid`, so a common convention is to prefix props that will only be used by styled components with `$` e.g. `$invalid`

## Pros
- Quick and easy to add
- Can continue thinking in React (configurable style functions)
- Styles scoped to components, so avoids clashes
- Avoids duplication - the little wrapper components can be reused
- Keeps styles close to the JSX code, but not inside of JSX code

## Cons 
- No clear separation of React and CSS code
- Lots of small files (not necessarily a bad thing though components and reusage is a core idea in React)

## Nesting styles
Change styles that were `header x` in CSS to `& x` and nest them as below.

```jsx
import logo from '../assets/logo.png';
import styled from 'styled-components';

const StyledHeader = styled.header`
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 2rem;
  margin-bottom: 2rem;

  & img {
    object-fit: contain;
    margin-bottom: 2rem;
    width: 11rem;
    height: 11rem;
  }
  
  & h1 {
    font-size: 1.5rem;
    font-weight: 600;
    letter-spacing: 0.4em;
    text-align: center;
    text-transform: uppercase;
    color: #9a3412;
    font-family: 'Pacifico', cursive;
    margin: 0;
  }
  
  & p {
    text-align: center;
    color: #a39191;
    margin: 0;
  }
  
  @media (min-width: 768px) {
    & {
      margin-bottom: 4rem;
    }

    // or
    // margin-bottom: 4rem;
    
    & h1 {
      font-size: 2.25rem;
    }
  }
`;

export default function Header() {
  return (
    <StyledHeader>
      <img src={logo} alt="A canvas" />
      <h1>ReactArt</h1>
      <p>A community of artists and art-lovers.</p>
    </StyledHeader>
  );
}

```

## Targeting pseudo selector

Use `&:hover` with no whitespace. If you use whitespace you are targeting children of `&`

```jsx
const Button = styled.button`
  cursor: pointer;
  background: none;
  line-height: inherit;

  &:hover {
    background-color: #f0920e;
  }
`;
```

## Splitting files for Styled Components
If you are just using the component in the one place it's fine to leave it in that file. If you are going to reuse them across the app, then creating new files for them is a good idea. 
So styling could be one factor in our decision about when to split something into a new component or file.

e.g. create a `Button.jsx` file. `import styled from 'styled-components';` in that file. Export the component as you usually would, and then in the file where you want to use it:
`import Button from './Button.jsx'`

With a combination that always goes together e.g. `label` and `input` you can out them in the same file.

e.g. create an `Input.jsx` file. 
```jsx
import styled from 'styled-components';

const Label = styled.label`
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: ${(props) => props.$invalid ? '#f87171' : '#6b7280'};
  //or
  color: ${({$invalid}) => $invalid ? '#f87171' : '#6b7280'};
`

const Input = styled.input`
  width: 100%;
  padding: 0.75rem 1rem;
  line-height: 1.5;
  background-color: ${({$invalid}) => $invalid ? '#fed2d2' : '#d1d5db'};
  color: ${({$invalid}) => $invalid ? '#f44444' : '#374151'};
  border: 1px solid ${({$invalid}) => $invalid ? '#f73f3f' : 'transparent'};
  border-radius: 0.25rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
`

export default function CustomInput({label, $invalid, ...props}) {
  return <p>
    <Label $invalid={invalid}>{label}</Label>
    <Input $invalid={invalid} {...props}/>
  </p>
}
```
In the `CustomInput` component `label` and `invalid` are named props, the others will be forwarded as part of `...props`

```jsx
<ControlContainer>
  <CustomInput 
    label="Email"
    $invalid={emailNotValid}
    type="email"
    onChange={(event) => handleInputChange('email', event.target.value)}/>
  <CustomInput 
    label="Password"
    $invalid={passwordNotValid}
    type="password"
    onChange={(event) =>handleInputChange('password', event.target.value)}/>
</ControlContainer>
```


---
🏷 Tags: #🌱

🖇 Related links:
