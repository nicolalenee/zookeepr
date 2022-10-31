# Zookeeper

## Description 
This fun-loving website allows a local zoo to track all of the animal friends and their caretakers in their loving enclosure! Zookeepers can log every animal and note all of the little things that make each individual animal unique as well as upload information about themselves. For zoos, keeping track of every person and animal that makes the zoo function so well can allow for more effecient placements. Users can also search and filter through certain characteristics to  view specific types of animals.

<img width="1123" alt="image" src="https://user-images.githubusercontent.com/86696492/199106892-ce502ed6-fdd7-4b05-838a-8778b7762f22.png">

<img width="1133" alt="image" src="https://user-images.githubusercontent.com/86696492/199108370-a1086870-63bc-43a5-9add-a92358b3f916.png">



## Installation
To run this application locally, Node.js must be installed on your machine.

## Technology
* Node.js
* Express.js

# Data Configuration
The data within this application is stored in JSON format. This choice was made due to simplistic nature and very small number of object types we need here. Therefore, routes call on functions that mutate and validate the data upon user entry. View the following snippet to add an animal to the existing array:
```javascript
function createNewAnimal(body, animalsArray) {
  const animal = body;
  animalsArray.push(animal);
  fs.writeFileSync(
    path.join(__dirname, '../data/animals.json'),
    JSON.stringify({ animals: animalsArray }, null, 2)
  );
  return animal;
};
```

Here, we have a function that takes the information that is entered in by our front end users and stored in the body of the request header. It pushes that information into the array by stringifying the JSON object then joins that information to the existing file.

When a user hits the API endpoint by submitting a form for a new animal, the former function is called. In this application, the routes follow REST API structure and can be seen as follows: 

```javascript
router.post('/animals', (req, res) => {
  // set id based on what the next index of the array will be
  req.body.id = animals.length.toString();

  // if any data in req.body is incorrect, send 400 error back
  if (!validateAnimal(req.body)) {
    res.status(400).send('The animal is not properly formatted.');
  } else {
    const animal = createNewAnimal(req.body, animals);
    res.json(animal);
  }
});
```

Here, we set up the route and determine the ID of the animal so that we can insert it in the proper index within the array. We validate the information that is submitted by the user to ensure that we have no missing data, then we call our function to update the animals array and the coinciding JSON file.



  ## Questions
[Repository](https://github.com/nicolalenee/zookeepr)   
[Deployment](https://cola-zookeepr.herokuapp.com/)



