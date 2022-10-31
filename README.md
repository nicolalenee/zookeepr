# Zookeeper

## Description 
This fun-loving website allows a local zoo to track all of the animal friends and their caretakers in their loving enclosure! Zookeepers can log every animal and note all of the little things that make each individual animal unique as well as upload information about themselves. For zoos, keeping track of every person and animal that makes the zoo function so well can allow for more effecient placements.


## Installation
To run this application locally, Node.Js must be installed on your machine.

# Configuration
The data within this application is stored in JSON format. Therefore, routes call on functions that mutate and validate the data upon entry. View the following snippet to add an animal to the array of animals within the JSON file.:
```javascript
function createNewAnimal(body, animalsArray) {
  const animal = body;
  animalsArray.push(animal);
  fs.writeFileSync(
    path.join(__dirname, '../data/animals.json'),
    JSON.stringify({ animals: animalsArray }, null, 2)
  );
  return animal;
}
```




  ## Questions
  GitHub ❤️ : [http://github.com/nicolalenee]
  Email 📧: [marblenicola@gmail.com]



