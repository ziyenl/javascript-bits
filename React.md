
### React

- modular component
- Components are basic unit of organization of react app
___
### React Fragments

Instead of having a `<div>`, uses React.fragment

 
### Not wanting to display any React Component
Return null from a component is fine

Returning undefined (forgot return statement) will throw an error.

___

### Don't want to use index of array as key
It causes performance issue

___

### Vanilla Javascript takes a string for event, React takes a function
name of attribute is camel case in React.

**React**

    <button onClick={displayAlert}>Hello</button>
    <button onClick={()=>alert('Hello')}>Hello</button>

**Vanilla**

    <button onclick="displayAlert()">Hello</button>

___

### Three ways to style
1. **Use CSS**
import './<name>.css' with the classname defined in the css as well as the class of the html tag.

3. **Use Styled Components**


    npm install styled-components
    import styled from 'styled-components'
     
    const Wrapper = styled.div`
    border: 2px solid red;
    padding: 32px;
    `;
    
    <Wrapper></Wrapper>

3. **Use inline style**


    <p style={{color: 'red', fontSize: '96px'}}>Red Text</p>

___
 

### React Hooks

Easy to add state, side effects, and network requests

    [variable, setVariable]= useState(0)

React components will only re-render if the value of the props or hook (state) changes.

React only re-renders the components that are affected by the variable change.

___
**useEffect(arrow function)**

It is called when component is rendered and whenever the data component is updated.
 Returns another function when the component is unmount.
Be careful when changing state from inside useEffect.

    useEffect(()=> {
        console.log('useEffect function called');
        return () => console.log('Unmount');
      },[])

[] - indicates which item it will be affected. Empty array means it is only
called when component is first rendered.
if no array is called - it will be called each time component is rendered.

___

### <React.StrictMode>
Senses which component are using hooks and automatically renders it twice
to make sure we are not inadvertently putting side effects in (development mode)

___

### React Unidirectional Flow
Parent component pass props down to child component.
Child component cannot pass data to parent.


Hoisting the state - move the state to where it can be passed down to whereever the 
component needs.

___

### Common Reasons why you are facing problem
- not destructing in props incoming component
- not returning in brackets the component

___

### React Routing
    npm install react-router-dom
        <Router>
            <Link to="/counter">Go To Counter Page</Link>
            <Link to="/people-list">Go To People List Page</Link>
              <Routes>
              <Route path="/" exact element={<HomePage/>} />
              <Route path="/counter/:name"  element={<CounterButtonPage/>} />
              <Route path="/people-list" element={<PeopleListPage/>}/>
              </Routes>
        </Router>

___

### Link to Pages
Using anchor a tag will cause page to reload in the React App
You want smooth transition of pages.

     <Router>
            <Link to="/counter">Go To Counter Page</Link>
            <Link to="/people-list">Go To People List Page</Link>
             ...
     </Router>

___

### URL Parameters and Query Parameters
URL Parameters: Found as segments of URL Path.
Query Parameters: Found in a different part of URL. After a question mark at the end of the path.
?q=dog+cat&price=300

___

###useParams
Calling End:

    <Route path="/counter/:name"  element={<CounterButtonPage/>} />

Receiving End:

    import { useParams } from 'react-router-dom'
    
    const {name} = useParams();

___

### useLocations
Calling End:

    <Route path="/counter"  element={<CounterButtonPage/>} />

Receiving End:

    import { useLocation } from 'react-router-dom'
    const location = useLocation();
      const params = new URLSearchParams(location.search);
      const startingValue = params.get('startingValue')

___

### Switch has been replaced with Routes
Not specifying a path has been replaced with:

    <Route path="*" element={<NotFoundPage/>}/>

___

### Redirect has been replaced with **Navigate**
    import { Navigate} from 'react-router-dom'
    return isAuth? 
         (<h1>Reserved only for auth users</h1>):
         (<Navigate to='/'></Navigate>)

___

### Redirect Programmatically. useHistory replaced with **useNavigate**
    import { useNavigate} from 'react-router-dom'
    
    const navigate = useNavigate()
      navigate('/')

___

### Two main form methodologies
- Controlled - container component tracks the entire state of the all the inputs of the form
Values of inputs linked up one-to-one with state value of components.


    const [name, setName] = useState('')
    const [email, setEmail] = useState('');
    const [favoriteColor, setFavoriteColor] = useState('');
      
  
    <form>
      <h3>Please enter your information:</h3>
      <div>
        <input type="text"
        placeholder="Name" 
        value={name}
        onChange={(e)=>{setName(e.target.value)}}/>
      </div>
      <div>
        <input type="text" 
        placeholder="Email"
        value={email}
        onChange={(e)=>{setEmail(e.target.value)}}/>
      </div>
      <div>
        <input type="text" 
        placeholder="Favorite Color"
        value={favoriteColor}
        onChange={(e)=>{setFavoriteColor(e.target.value)}}/>
      </div>
      <button onClick={e=>{alert(`Your name is ${name}, 
      your email is ${email}, 
      your favourite color is ${favoriteColor}`)}}>Submit</button>
    </form>

- Uncontrolled
Uncontrolled form uses refs, which are specific reference to DOM elements (instead of 
states).
Leave to DOM to its own devices.
It uses reference instead of state.

    
    const nameInput = React.createRef();
    const emailInput = React.createRef();
    const favoriteColorInput = React.createRef();
    <form>
        <h3> Pleae enter your information: </h3>
        <div>
        <input type="text"
        ref={nameInput}
        placeholder="Name"/>
      </div>
      <div>
        <input type="text" 
        ref={emailInput}
        placeholder="Email"/>
      </div>
      <div>
        <input type="text" 
        ref={favoriteColorInput}
        placeholder="Favorite Color"/>
      </div>
      <button onClick={e => 
      {alert(`Your name is ${nameInput.current.value}. 
      Your email is ${emailInput.current.value}. 
      Your favorite color is ${favoriteColorInput.current.value}`);
      e.preventDefault();
      }}>Submit</button>
    </form>

 

### Navigation Bar


Other element of application that show up on all routes


    export const NavBar= ()=> {
     return (<ul>
        <li>
            <Link to="/">Home</Link>
        </li>
        <li>
            <Link to="/counter">Counter Button</Link>
        </li>
        <li>
            <Link to="/people-list">People List</Link>
        </li>
        <li>
               <Link to="/control">Controlled Form</Link>
           </li>
           <li>
               <Link to="/uncontrol">Uncontrolled Form</Link>
           </li>
     </ul>)
    }

TODO: Figure out sub-navigation nested routers

---
### Network Request

Fetch API

    const response = await fetch(`...`);
    const data = await response.json();

React hooks does not allow passing of asynchronous function to useEffect.
Hence, pass in regular and then do the async fetch inside

     useEffect(()=>{
            const fetchUser = async() => {
                const response = await fetch("https://randomuser.me/api")
                const data = await response.json()
                setUser(data.results[0]);
            }
            fetchUser();
        }, []);

---
### Children Prop vs. Name Prop
Children - any and all component that the tags of given component wrap
When a component wraps another component, it receives them in the children prop
automatically


### Class Based Components (Legacy)
No longer recommended, they have been replaced by functional components.

**Differences with Functional Components.**
1. It uses this.props instead of passing props in argument like Functional Components

2. We can't use react hooks in class based components.
It has state based variable and is used in lieu. So, no useState, useEffect etc.

3. It has several lifecycle methods for render, prop change. 
a. Class Constructor. Bind any function that wasn't written using arrow syntax and set intiial values.
  

      export class CounterButtonCBPage extends Component {
        state = {
          hideMessage: false,
          numberOfClicks: 0,
        }
      
        // function needs constructor if don't use arrow
        // set initial value of variables
        /**constructor() {
          super(props)
          this.increment = this.increment.bind(this);
        }
        increment () {
          this.setState({numberOfClicks: this.state.numberOfClicks + 1});
        }**/

      increment = () => {
        this.setState({numberOfClicks: this.state.numberOfClicks + 1});
      }
      render() {
        return (
            
        )
      }
    }

4. Arrow functions tend to replace need of constructor. See below equivalent.

     
    // function needs constructor if don't use arrow
        // set initial value of variables
        /**constructor() {
          super(props)
          this.increment = this.increment.bind(this);
          this.state = xxx
        }
        increment () {
          this.setState({numberOfClicks: this.state.numberOfClicks + 1});
        }**/

      increment = () => {
        this.setState({numberOfClicks: this.state.numberOfClicks + 1});
      }

5. componentDidMount()
