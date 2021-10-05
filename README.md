# [![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%238D19FF&multiline=true&lines=Welcome+All+React+JS++developers!!!)](https://github.com/dhanar98/common-reactjs-errors-and-solutions)

## I would like to all the developers who are facing issues in your react js project if you have the solution to any issue kindly mention the issue and solution. contribute everyone to help our developer problems

## **Instructions:**

**1. fork this repository**

**2. create a branch name with your username and number of errors and solutions**
   **Example : dhanar98_1error_2solutions.**

**3. update the error title in the Errors list Table**

**4. add the error title, reason and solutions with proper code or image (gif, png, jpg).**

**5. create a pull request without merge conflict**

**6. once 1-50 errors list is completed create another markdown file for another 50 errors(create a table with anchor links).**

**7. contribute everyone to make this repo bigger community.**


#### Error List Table

|S. NO  | Erros List  |
|---------|---------|
|1     | [1. TypeError: Cannot read property 'map' of undefined in React](#1-typeerror-cannot-read-property-map-of-undefined-in-react)|
|2     |  [2. ReferenceError: localStorage is not defined in React](#2-referenceerror-localstorage-is-not-defined-in-react)       |
|3     |     [3. Warning: Each child in a list should have a unique "key" prop  in React](#3-warning-each-child-in-a-list-should-have-a-unique-key-prop-in-react)    |
|4     |   [4. Error: Port 3000 is already in use in React](#4-error-port-3000-is-already-in-use-in-react)      |
|5     |  [5. Warning: Prop id did not match. Server: "recharts25-clip" Client: "recharts1-clip" in recharts](#5-warning-prop-id-did-not-match-server-recharts25-clip-client-recharts1-clip-in-recharts)   |
|6     |     [6 . Module not found: Can't resolve 'module name' in React](#6--module-not-found-cant-resolve-module-name-in-react)    |
|7     |         |
|8     |         |
|9     |         |
|10     |         |
|11     |         |
|12     |         |
|13     |         |
|14     |         |
|15     |         |
|16     |         |
|17     |         |
|18     |         |
|19     |         |
|20     |         |
|21     |         |
|22     |         |
|23     |         |
|24     |         |
|25     |         |
|26     |         |
|27     |         |
|28     |         |
|29     |         |
|30     |         |
|31     |         |
|32     |         |
|33     |         |
|34     |         |
|35     |         |
|36     |         |
|37     |         |
|38     |         |
|39     |         |
|40     |         |
|41     |         |
|42     |         |
|43     |         |
|44     |         |
|45     |         |
|46     |         |
|47     |         |
|48     |         |
|49     |         |
|50     |         |

## 1. TypeError: Cannot read property 'map' of undefined in React

First of all, we try to understand why this error happens?


![code.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632680631926/nV5l4AtjY.png)

From the start, We initialize the users variable in a **useState** as an Empty value.
So the **users.map** Initially called a map function **undefined.map**. This is what the issue
at the starting of a useState Initialization.

### Solution for this Problems:


**Solution 1:**
Set the state value as Empty Array.

```javascript
const [users, setUsers] = useState([]);
``` 

**Solution 2:**

Check the *users* array is empty or not.
```javascript
	return (
		<div className="common-reactjs-errors">
			<ul>
				{users && users.map((user,index) => {
					return (
						<Fragment key={index}> //console error fix
							<li>{user.id}</li>
							<li>{user.name}</li>
						</Fragment>
					);
				})}
			</ul>
		</div>
	);
``` 

**Solution 3:**

Checking the *users* array is empty or not using ** [Optional Chaining Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator#relationship_with_the_optional_chaining_operator_) **
```javascript
	return (
		<div className="common-reactjs-errors">
			<ul>
				{users?.map((user,index) => {
					return (
						<Fragment key={index}>
							<li>{user.id}</li>
							<li>{user.name}</li>
						</Fragment>
					);
				})}
			</ul>
		</div>
	);
``` 

## 2. ReferenceError: localStorage is not defined in React

**Reason:**

The *localStorage* is a window object in a browser. when you regenerate a page in 
React JS *localStorage* is not defined.because it's a browser-only feature.


**Solution:**

This one line will help you solve this error.

```javascript
const var_name_what_you_want =typeof window !== 'undefined' ?localStorage.getItem('cookie_name'):null;
``` 

## 3. Warning: Each child in a list should have a unique "key" prop  in React

Keys Only differentiate the array data.

> This is how my warning code looks:

```javascript
	return (
		<div className="common-reactjs-errors">
			<ul>
				{users?.map((user) => {
					return (
						<>
							<li>{user.id}</li>
							<li>{user.name}</li>
						</>
					);
				})}
			</ul>
		</div>
	);
``` 

**Solution 1:**

Returning Multiple Elements in a component, we need to add ** [Fragment](https://reactjs.org/docs/fragments.html) ** in our empty parent tag.

**Note:**
Fragments let you group a list of children 
without adding extra nodes to the DOM.


```javascript
import {Fragment } from "react";
``` 

```javascript
	return (
		<div className="common-reactjs-errors">
			<ul>
				{users?.map((user,index) => {
					return (
						<Fragment key={index}>
							<li>{user.id}</li>
							<li>{user.name}</li>
						</Fragment>
					);
				})}
			</ul>
		</div>
	);
``` 

**Solution 2:**

If it is a Single return element add the unique value as key or index.


```javascript
	return (
		<div className="common-reactjs-errors">
			<ul>
				{users?.map((user) => {
					return (
						<li key={user.id}>{user.name}</li>
					);
				})}
			</ul>
		</div>
	);
``` 
## 4. Error: Port 3000 is already in use in React
**Reason:**

This error only Happens Once you forgot to stop the server or 
the port runs a different application.

**Solution:**


```bash
//Kill The Port
lsof -ti:3000 | xargs kill -9
``` 
``` bash
//Run The Project
npm run start
``` 
**Note:💡[PROTIP]**

> If You are Running a Next.JS app run your application different port without
any configuration using this command.


```bash
npx next -p 4_DIGIT_NUMBER
E.X : npx next -p 1998
``` 
## 5. Warning: Prop id did not match. Server: "recharts25-clip" Client: "recharts1-clip" in recharts

This warning error occurs in the console. while load a recharts graph this error happened.

**[console warning]**
**Reason:**

The recharts graph data while running the page server-side rendering is failed. that's why it's happened.

**Solution:**

 Set a state for the graph once the document is ready the graph data will be shown.

```javascript
 //set graph chart props data once document is ready state
  const [graph, setGraph] = useState(false);
``` 

This is how I load the props data in graph
```javascript
 useEffect(() => {
  setGraph(true);
 }, [])

{graph &&
(
    <LineChart width={750} height={450} data={props.data}>
     <CartesianGrid stroke="#EFECEC" />
      <XAxis />
      <YAxis/>
      <Legend/>
      <Line/>
     </LineChart>
) }

``` 
## 6 . Module not found: Can't resolve 'module name' in React
### This Error Happens 2 Ways:

 1.The Particular module is missing in the **node_modules folder**


 **Solution:**
 Remove package-lock.json and run the commands
```bash
npm install
npm start
``` 
This will solve this issue.




2. The Particular Component Module Missing in the particular Location:
  
**Solution:**
 Set a Correct Path for the component module.

*This Path Intellisense Vscode Extension is useful for me to avoid mismatching path errors in the projects.*

[![PathIntellisense](https://img.shields.io/badge/PathIntellisense_EXTENSION-4285F4?style=for-the-badge&logo=Files&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
