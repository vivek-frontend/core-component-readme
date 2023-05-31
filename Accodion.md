
# Accordion component

This is a simple accordion component that is used as HOC that also accepts props to track the changes made in an accordion element. 

## Props

| props           | Type     | Required |Default Value  |
| :--------       | :------- | :------- |:------------- |
| `className`     | `string` |    `no`  |    `" " `     |
| `isMultipleOpen`| `boolean`|    `no`  |    `false`    |
| `controlClass`  | `string` |    `no`  |    ` " "`     |
| `titleClass`    | `string` |    `no`  |    `" " `     |
| `contentClass`  | `string` |    `no`  |    ` " " `    |
| `Component`     | `HTMLElement`| `no` |   ` " " `     |
| `Title`         | `HTMLElement`| `no` |   ` " " `     |
| `isOpen`        | `boolean`|     `no` |    ` false`   |
| `setToggleValue`| `function`|    `no` |`(x:boolean) => {...}`|
| `accordionName` | `string` |     `no` |   `accordion` |


## Props Defination

- className 
  - accepted value -  `string`
  - this classname would be added to the accordion wrapper and  can be used to `customise the Accordion styles` if required
  - default value - ""
- titleClass 
  - accepted value -  `string`
  - this classname would be added to the accordion Title and can be used to `customise the Title styles` if required
  - default value - "" 
- contentClass 
  - accepted value -  `string`
  - this classname would be added to the accordion Content Wrapper and can be used to `customise the Content styles` if required
  - default value - ""
- controlClass 
  - accepted value -  `string`
  - this classname would be added to the accordion Input[checkbox/radion] and can be used to `customise the Input styles` if required
  - default value - ""  
- isMultipleOpen 
  - accepts value -  `boolean` 
  - this property would be decided that multiple/single 
  - default value - false accordion open at same time
- accordionName 
  - accepted value -  `string`
  - this classname would be added to the accordion Input in name attribute
  - default value - "accordion" 
- setToggleValue
  - accepted value -  `function`
  - description - a function which is called when toggle the accordion contain updated flag
  - default value - false 
- isOpen 
  - accepted value - `boolean`
  - description - controls whether the accordion section is open or closed.
  - default value - false


### The example below demonstrates how to render Accordion (1st way)

```js
// useState is manage toggle value 
 const [toggle ,setToggle] = useState(false);

 //Handler toggle value of isOpen 
  const toggleHandler = () =>{
    setToggle(!toggle)
  }

   <Accordion
      Title={() => <h2>This is accordion title</. h2>} // 
      isOpen={toggle} // true or false
      setToggleValue={toggleHandler}
    >
      <p>content</p>
      </Accordion>

```
### The example below demonstrates how to render Accordion (2st way)

```js

    const Title = () => {
      return <h2>This is the accordion title</h2>;
    };

    const Content = () => {
      return <p>This is the accordion content...</p>;
    };

    <Accordion
        Title={Title}
      >
        <Content />
        </Accordion>

```
### The example below demonstrates how to render Accordion

```js
    import Accordion from "./lib/Accordion";

    const Title = () => {
          return <h2>This is accordion title</h2>
    }
    const Content = () => {
          return <p>This is accordion contents This is accordion contents...</p>
    }

    const AccordionComponents = Accordion(Content ,Title);

    <AccordionComponents />
```

### Render HTML View

```html
<div class="className">
        <input type="checkbox" className="accordionControl" name="accrodion" />
        <div className="accordionHeader"><h2>This is accordion title</h2></div>
        <div className="accordionContent">
           <p>This is accordion contents This is accordion contents...</p>
        </div>
</div>
```

### Customise Accordion Styles

```js
    import Accordion from "./lib/Accordion";
    import styled from "@emotion/styled";

    const Title = () => {
           return <h2>This is accordion title</h2>
    }

    const Content = () => {
          return <p>This is accordion contents This is accordion contents...</p>
    }

    const AccordionWithStyled = styled(Accordion(Content ,Title))`
                                    font-size: 12px;
                                    line-height: 1.14;
                                    color: #9c9c9c;
                                `
    <AccordionWithStyled />
```