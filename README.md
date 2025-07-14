🧾 JavaScript Helper Methods and ES6+ Concepts – Documentation
🔁 Array Iteration Helpers
1. forEach
Purpose: Iterates over each item in an array, performing an operation on each.

Example:


var posts = [
  { id: 23, title: 'Daily JS News' },
  { id: 52, title: 'Code Refactor City' },
  { id: 105, title: 'The Brightest Ruby' }
];

posts.forEach(function(post) {
    savePost(post);
});
Use Case - Calculating Area:


var images = [
  { height: 10, width: 30 },
  { height: 20, width: 90 },
  { height: 54, width: 32 }
];
var areas = [];

images.forEach(image => {
  areas.push(image.height * image.width);
});
2. map
Purpose: Transforms each element of an array and returns a new array.

Example:


var trips = [
  { distance: 34, time: 10 },
  { distance: 90, time: 50 },
  { distance: 59, time: 25 }
];

var speeds = trips.map(trip => trip.distance / trip.time);
Use Case - Extract Property:


var images = [
  { height: '34px', width: '39px' },
  { height: '54px', width: '19px' },
  { height: '83px', width: '75px' },
];

var heights = images.map(image => image.height);
Custom Pluck Function:


function pluck(array, property) {
    const result = array.map(item => item[property]).filter(Boolean);
    return result.length > 0 ? result : ['no property found'];
}
3. filter
Purpose: Returns a new array with elements that match a condition.

Example:


var numbers = [15, 25, 35, 45, 55, 65, 75, 85, 95];
var filteredNumbers = numbers.filter(number => number > 50);
Use Case - Filter by Multiple Properties:


var products = [
  { name: 'cucumber', type: 'vegetable', quantity: 0, price: 1 },
  { name: 'banana', type: 'fruit', quantity: 10, price: 15 },
  { name: 'celery', type: 'vegetable', quantity: 30, price: 13 },
  { name: 'orange', type: 'fruit', quantity: 3, price: 5 }
];

var filteredProducts = products.filter(product =>
  product.type === 'vegetable' && product.quantity > 0 && product.price > 10
);
Use Case - Filter Comments by Post ID:


function commentForPost(post, comments) {
  return comments.filter(comment => comment.postId === post.id);
}
4. find
Purpose: Returns the first element that matches a condition.

Example:


let users = [
  { name: 'John' },
  { name: 'James' },
  { name: 'Jones' }
];

let user = users.find(user => user.name === 'James');
Use Case - Find Post for a Comment:


function postForComment(posts, comment) {
  return posts.find(post => post.id === comment.postId);
}
Custom findWhere Function:

function findWhere(array, criteria){
  const property = Object.keys(criteria)[0];
  const value = criteria[property];

  return array.find(element => element[property] === value);
}

5. every & some
Purpose:

every: Checks if all elements match a condition.

some: Checks if at least one element matches a condition.

Example:

var computers = [
  { name: 'Apple', ram: 24 },
  { name: 'Compaq', ram: 12 },
  { name: 'Lenovo', ram: 4 },
  { name: 'Acer', ram: 32 }
];

computers.every(computer => computer.ram > 16); // false
computers.some(computer => computer.ram > 16); // true

6. reduce
Purpose: Applies a function to each item and accumulates a result.

Example - Color Extraction:

var primaryColors = [
  { color: 'red' },
  { color: 'green' },
  { color: 'blue' }
];

var result = primaryColors.reduce((prev, color) => {
  prev.push(color.color);
  return prev;
}, []);

Use Case - Balanced Parentheses Checker:

function balanceParens(string) {
  return !string.split("").reduce((count, char) => {
    if (count < 0) return count;
    if (char === "(") return ++count;
    if (char === ")") return --count;
    return count;
  }, 0);
}

Use Case - Desk Count:

var desks = [
  { type: 'sitting' },
  { type: 'standing' },
  { type: 'sitting' },
  { type: 'sitting' },
  { type: 'standing' }
];

var deskTypes = desks.reduce((acc, desk) => {
  if (desk.type === 'sitting') acc.sitting++;
  else if (desk.type === 'standing') acc.standing++;
  return acc;
}, { sitting: 0, standing: 0 });

🧠 ES6+ Features

🔹 let and const
let: block-scoped, reassignable.

const: block-scoped, not reassignable.

Example:

const statuses = [
  { code: 'OK', response: 'Request successful' },
  { code: 'FAILED', response: 'There was an error' },
  { code: 'PENDING', response: 'Still pending' }
];

let message = '';
const currentCode = 'OK';

for (let i = 0; i < statuses.length; i++) {
  if (statuses[i].code === currentCode) {
    message = statuses[i].response;
  }
}

🔹 Arrow Functions
Syntax Sugar for anonymous functions and more predictable this.

Example:

const team = {
  members: ['Jane', 'Bill'],
  teamName: 'Super Squad',
  teamSummary() {
    return this.members.map(member => `${member} is on team ${this.teamName}`);
  }
};

🔹 Enhanced Object Literals
Shorthand for defining object properties and methods.

Example:

function createBookShop(inventory) {
  return {
    inventory,
    inventoryValue() {
      return this.inventory.reduce((total, book) => total + book.price, 0);
    },
    priceForTitle(title) {
      return this.inventory.find(book => book.title === title).price;
    }
  };
}

🔹 Default Function Arguments
Assign default values to function parameters.

Example:

function makeAjaxRequest(url, method = 'GET') {
  return method;
}

Dynamic Default:
function User(id) {
  this.id = id;
}

function generateId() {
  return Math.random() * 99999;
}

function createAdminUser(user = new User(generateId())) {
  user.Admin = true;
  return user;
}

✅ Summary Table
Method	Purpose
forEach()	Loop over array without returning value
map()	Transform array, return new array
filter()	Return array elements matching condition
find()	Return first element matching condition
every()	Return true if all elements match
some()	Return true if at least one matches
reduce()	Reduce array to a single value
