# javascript
Learning files for Javascript
\\ For Each Helper \\

function handlePosts() {
    var posts = [
      { id: 23, title: 'Daily JS News' },
      { id: 52, title: 'Code Refactor City' },
      { id: 105, title: 'The Brightest Ruby' }
    ];
    
    // for (var i = 0; i < posts.length; i++) {
    //   savePost(posts[i]);
    // }
    posts.forEach(function(post){
        savePost(post);
    });
}
--------------------------------------------------------------------
\\Foreach Helper\\

Qn) The array below contains an array of objects, each of which is a representation of an image.  Using the forEach helper, calculate the area of each image and store it in a new array called 'areas'.  The area of an image can be calculated as 'image.height * image.width'.

Sol)
var images = [
  { height: 10, width: 30 },
  { height: 20, width: 90 },
  { height: 54, width: 32 }
];
var areas = [];

function area(height,width) {
    var result = height*width;
    areas.push(result);
}
images.forEach((image)=>{area(image.height,image.width)})

--------------------------------------------------------------------
\\Map Helper\\

var images = [
  { height: '34px', width: '39px' },
  { height: '54px', width: '19px' },
  { height: '83px', width: '75px' },
];

var heights = [];

images.map(function Pluck(image){
    return heights.push(image.height);
})
--------------------------------------------------------------------
Qn) Using map, create a new array that contains the distance / time value from each trip.  In other words, the new array should contain the (distance / time) value.  Assign the result to the variable 'speeds'.
var trips = [
  { distance: 34, time: 10 },
  { distance: 90, time: 50 },
  { distance: 59, time: 25 }
];

const newArr = trips.map(function(trip){
    return (trip.distance/trip.time)
    
});

var speeds = newArr;
--------------------------------------------------------------------
Qn) Really Hard - Implementing 'Pluck'
This is a hard one!
Implement a 'pluck' function.  Pluck should accept an array and a string representing a property name and return an  array containing that property from each object. 

Example: 

var paints = [ { color: 'red' }, { color: 'blue' }, { color: 'yellow' }];
pluck(paints, 'color'); // returns ['red', 'yellow', 'blue'];

Hint:

Remember that you can access a property on an object by using square bracket notation. For example...

var person = { name: 'Bill' };
person['name'] // returns 'Bill'

sol) 
let FilterArray = [];

function pluck(array, property) {
    FilterArray = [];

    array.forEach(function(item) {
        if (item.hasOwnProperty(property)) {
            FilterArray.push(item[property]);
        }
    });

    // If no items have the property, return 'no property found'
    if (FilterArray.length === 0) {
        FilterArray.push('no property found');
    }

    return FilterArray;
}


--------------------------------------------------------------------
\\Filter Helper\\ :

var numbers = [15, 25, 35, 45, 55, 65, 75, 85, 95];

var filteredNumbers;

filteredNumbers = numbers.filter(function(number){
    return number > 50;
})

--------------------------------------------------------------------
var products = [
  {name : 'cucumber', type: 'vegetable'},
  {name : 'banana', type: 'fruit'},
  {name : 'celery', type: 'vegetable'},
  {name : 'orange', type: 'fruit'},
];

var filteredProducts = []

for (var i = 0; i < products.length; i++){
	if(products[i].type === 'fruit') {
  	filteredProducts.push(products[i]);
  }
}

filteredProducts;

products.filter(function(product){
 	return product.type === 'vegetable';
 });
--------------------------------------------------------------------

var products = [
  {name : 'cucumber', type: 'vegetable', quantity: 0, price: 1},
  {name : 'banana', type: 'fruit', quantity: 10, price: 15},
  {name : 'celery', type: 'vegetable', quantity: 30, price: 13},
  {name : 'orange', type: 'fruit', quantity: 3, price: 5},
];

var filteredProducts = []

products.filter(function(product){
	return product.type === 'vegetable' 
  && product.quantity > 0 
  && product.price > 10
});

--------------------------------------------------------------------
var post = { id:4, title: 'New Post'};

var comments = [
  {postId: 4, content: 'awesome post'},
  {postId: 3, content: 'it is ok post'},
  {postId: 4, content: 'neat post'},
];

function commentForPost(post, comments) {
 return comments.filter(function(comment){
 	return comment.postId === post.id;
 });
}
commentForPost(post, comments);

--------------------------------------------------------------------
find helper ---

 let users = [
   {name:'John'},
   {name:'James'},
   {name:'Jones'},
 ];

let user;

users.find((user)=>{
	return user.name === 'James';
});

user;

--------------------------------------------------------------------


function Car(model){
	this.model = model;
}

var cars = [
	new Car('Buick'),
	new Car('Camaro'),
	new Car('Focus'),
];

cars.find(function(car) {
	return car.model === 'Focus';
});

--------------------------------------------------------------------

var posts = [
  {id: 1, title: 'New Post'},
  {id: 2, title: 'Old Post'},
];

var comment = {postId: 1, content: 'Great post'};

function postForComment(posts, comment) {
  return posts.find(function(post) {
    return post.id === comment.postId;
  });
}

postForComment(posts,comment)
--------------------------------------------------------------------
Really Challenging: Custom findWhere Helper
This is a tough one!  The most common find operation is to an object that has a given property.  Rather than writing out a full function every time, it would be great if we has a shorthand syntax to find an object like this:
findWhere(ladders, { height: '20 feet' });
The object { ladders: '20 feet' } should be used as the search criteria - we would want to find a ladder whose 'height' property was '20 feet';


Your goal: Write a 'findWhere' function that achieves this shorthand approach.  'findWhere' should return the found object.

In summary:

var ladders = [
  { id: 1, height: 20 },
  { id: 3, height: 25 }
];

findWhere(ladders, { height: 25 }); // result: { id:3, height: 25 }

Hint: the hard part of this is figuring out the name of the proeprty on the criteria.  You can use Object.keys(criteria)[0] to figure out the name of the property on the object.  For example, Object.keys({ height: '20 feet' }) would return 'height'.  You could then check to see if a given element in the array had a property equal to the criteria's value with something like element[property] === criteria[property].

function findWhere(array, criteria){
  const property = Object.keys(criteria)[0];
  const value = criteria[property];

    return array.find((element)=> {
        return element[property] ===value;
    });
}
--------------------------------------------------------------------
\Every helper\

var computers = [
  {name:'Apple',ram: 24},
  {name:'Compaq',ram: 12},
  {name:'Lenovo',ram: 4},
  {name:'Acer',ram: 32},
];

var allCan = true;
var someCan = false;


for (var i=0; i<computers.length; i++){
	var computer = computers[i];
  
  if (computer.ram < 16){
  	allCan = false;
  }
  else{
  	someCan = true;
  }
}

"+_+"
allCan
someCan
"+_+"

computers.every((computer)=>{
	return computer.ram > 16;
});

\Some Helper\
computers.some((computer)=>{
	return computer.ram > 16;
});

--------------------------------------------------------------------
\Reduce Helper\

var primaryColors = [
  {color: 'red'},
  {color: 'green'},
  {color: 'blue'},
];

primaryColors.reduce((prev,primaryColor)=>{
	prev.push(primaryColor.color);
  
  return prev;
}, []); 

// OP: ["red","green","blue"]
--------------------------------------------------------------------

function balanceParens(string){
	return !string.split("").reduce((prev, char) =>
  {
    if(prev < 0) return prev;
    if(char === "(") return ++prev;
    if(char === ")") return --prev;
    return prev;
  }, 0);
}

balanceParens(`(())(())()()`);  //true
balanceParens(`(())((((`);  //false
--------------------------------------------------------------------
\Reduce Hard\


var desks = [
  { type: 'sitting' },
  { type: 'standing' },
  { type: 'sitting' },
  { type: 'sitting' },
  { type: 'standing' }
];

var deskTypes = desks.reduce(function(acc, desk) {
    // Check the type of the desk and increment the corresponding count
    if (desk.type === 'sitting') {
        acc.sitting += 1;
    } else if (desk.type === 'standing') {
        acc.standing += 1;
    }
    // Return the accumulator object
    return acc;
}, { sitting: 0, standing: 0 });

--------------------------------------------------------------------
\\ let and const \\
const statuses = [ 
  { code: 'OK', response: 'Request successful' },
  { code: 'FAILED', response: 'There was an error with your request' },
  { code: 'PENDING', response: 'Your request is still pending' }
];
let message = ''; // 'message' will be reassigned
const currentCode = 'OK';

for (let i = 0; i < statuses.length; i++) { // 'i' is block-scoped and will not be reassigned outside the loop
  if (statuses[i].code === currentCode) {
    message = statuses[i].response; // 'message' is reassigned here
  }
}

--------------------------------------------------------------------

\\Arrow fn\\

const team = {
	members: ['Jane','Bill'],
  teamName: 'Super Squad',
  teamSummary : function() {
  	return this.members.map((member)=>{
    	return `${member} is on team ${this.teamName}`;
    });
  }
};

team.teamSummary();
--------------------------------------------------------------------

\\Enhanced Object Literals\\

function createBookShop(inventory){
  return {
  	inventory,    //inventory: inventory,
    inventoryValue() { //inventoryValue: function()
    	return this.inventory.reduce((total,book) => total + book.price, 0);
    },
    priceForTitle(title) { //CAN REMOVE FUNCTION AND DIRECTLY USE PROPERTY AS A FUNCTION
    	return this.inventory.find(book => book.title === title).price;
    }
  };	
}

const inventory = [
  {title: 'Harry Potter', price: 10},
  {title: 'Shrek 1', price: 15},
  {title: 'Shrek 2', price: 20},
];

const bookshop = createBookShop(inventory);

bookshop.inventoryValue();
bookshop.priceForTitle('Harry Potter');

--------------------------------------------------------------------

\\DEFAULT FUNCTION ARGUENTS\\

function makeAjaxRequest(url, method = 'GET', data = []){
	//logic to make the request
  url,
  method
  return method
}

makeAjaxRequest('google.com')
makeAjaxRequest('google.com', 'POST')

--------------------------------------------------------------------
default fn arguments:

function User(id){
	this.id = id;
}

function generateId(){
	return Math.random() * 99999;
}

function createAdminUser(user = new User(generateId())){
	user.Admin = true;
  return user
}

createAdminUser(new User(generateId()));
--------------------------------------------------------------------

