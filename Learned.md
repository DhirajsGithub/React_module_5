# How React Really Work

### React --> A JavaScript library foor building user interfaces

### React DOM --> Interface to the web

### components --> props(data from parent component and vice versa), state(internal data), context(component-wide data)
<hr>

## Re-evaluating Components !== Re-Rendering the DOM 
* Components --> Re-evaluated whenever props, state or context changes, React executes component functions
* Real Dom --> Changes to the real DOM are only made for differences between evaluations
* Parent Component re-evaluate  ==> Child Componnet re-evaluate
  
<hr>

### Preventing Unnecessarily Re-Evaluations
export React.memo(componentName)
React.memo works as if the value of pre prop and new props does not change then the child component won't be re-evaluated. 
Of course, React.memo can be a great tool if you have a huge component tree with a lot of child components. And on a high level in the component tree, you can avoid unnecessary re-render cycles for the entire branch of the component tree.

NOTE: React.memo() works fine with primitive data types but as we compoare non-primitive with every re-evaluation in parent it will fail
<hr>

## useCallback() hook :
Use Callback is a hook that allows us to basically store a function across component executions. So it allows us to tell React that we wanna save a function and that this function should not be recreated with every execution.
Likewise useEffect it also need second arg as dependecies, any surrounding state which is used inside useCallback() must be passed as dependencies.
useCallback(()=>{},[])

<hr>

### useState hook schedules the state tho be updated, hence better we use functional form of setState 

<hr>

### useMemo() hook :
 useMemo, as a first argument, wants a function That is, however, not a function that will be memorized Instead, that function should return what you want to store,
 const demo = useMemo(()=>{return something that you want to store}, [dependecies to change the store ]). use You essentially wanna memorize data if it would be performance-intensive

