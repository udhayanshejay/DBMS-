// MongoDB
// Show current database
db

// Show all databases
show dbs

// Create or switch to a database
use myFirstDatabase

// Create a collection "restaurants"
db.createCollection("restaurants")

// Create a collection "movies"
db.createCollection("movies")

// Insert one document into restaurants
db.restaurants.insertOne({
  address: {
    building: "1007",
    coord: [-73.856077, 40.848447],
    street: "Morris Park Ave",
    zipcode: "10462"
  },
  borough: "Bronx",
  cuisine: "Bakery",
  grades: [
    {date: new Date("2014-03-03"), grade: "A", score: 2},
    {date: new Date("2013-09-11"), grade: "A", score: 6}
  ],
  name: "Morris Park Bake Shop",
  restaurant_id: "30075445"
})

// Insert one document into movies
db.movies.insertOne({
  title: "The Great Train Robbery",
  plot: "A group of bandits stage a brazen train hold-up, ...",
  genres: ["Short", "Western"],
  runtime: 11,
  cast: ["A.C. Abadie", "Gilbert M. Broncho Billy Anderson", "George Barnes", "Justus D. Barnes"],
  released: ISODate("1903-12-01T00:00:00Z"),
  directors: ["Edwin S. Porter"],
  rated: "TV-G",
  awards: { wins: 1, nominations: 0 },
  imdb: { rating: 7.4, votes: 9847 },
  countries: ["USA"]
})


-- Query For Restaurants Collection
// 1. Restaurants except American and Chinese cuisine or name begins with 'Wil'
db.restaurants.find({
  $or: [
    {cuisine: { $nin: ["American", "Chinese"] }},
    {name: /^Wil/}
  ]
}, {restaurant_id:1, name:1, borough:1, cuisine:1})

// 2. Restaurants with grade 'A' and score 11 on specific date
db.restaurants.find({
  grades: {
    $elemMatch: {
      grade: "A",
      score: 11,
      date: ISODate("2014-08-11T00:00:00Z")
    }
  }
}, {restaurant_id:1, name:1, grades:1})

// 3. Where 2nd element of grades array is grade 'A' score 9 on date
db.restaurants.find({
  "grades.1.grade": "A",
  "grades.1.score": 9,
  "grades.1.date": ISODate("2014-08-11T00:00:00Z")
}, {restaurant_id:1, name:1, grades:1})

// 4. Restaurants where 2nd coords element between 42 and 52
db.restaurants.find({
  "address.coord.1": { $gt: 42, $lte: 52 }
}, {restaurant_id:1, name:1, address:1, "address.coord":1})

// 5. Arrange restaurant names ascending
db.restaurants.find().sort({name: 1})

// 6. Arrange restaurant names descending
db.restaurants.find().sort({name: -1})

// 7. Cuisine ascending, borough descending
db.restaurants.find().sort({cuisine: 1, borough: -1})

// 8. Addresses that contain street
db.restaurants.find({"address.street": {$exists: true}})

// 9. coord field value is Double (assume coord is array of Double)
db.restaurants.find({"address.coord": {$type: "double"}})

// 10. Restaurants with grades score % 7 = 0
db.restaurants.find({
  "grades.score": { $mod: [7, 0] }
}, {restaurant_id:1, name:1, grades:1})

// 11. Restaurants with 'mon' in name
db.restaurants.find({
  name: /mon/i
}, {name:1, borough:1, "address.coord":1, cuisine:1})

// 12. Restaurants with name starts 'Mad'
db.restaurants.find({
  name: /^Mad/
}, {name:1, borough:1, "address.coord":1, cuisine:1})

// 13. At least one grade score < 5
db.restaurants.find({
  "grades.score": {$lt: 5}
})

// 14. Same as above, in Manhattan
db.restaurants.find({
  "grades.score": {$lt: 5},
  borough: "Manhattan"
})

// 15. <5 score, Manhattan or Brooklyn
db.restaurants.find({
  "grades.score": {$lt: 5},
  borough: {$in: ["Manhattan", "Brooklyn"]}
})

// 16. <5 score, Manhattan/Brooklyn, not American
db.restaurants.find({
  "grades.score": {$lt: 5},
  borough: {$in: ["Manhattan", "Brooklyn"]},
  cuisine: {$ne: "American"}
})

// 17. <5, Manhattan/Brooklyn, not American or Chinese
db.restaurants.find({
  "grades.score": {$lt: 5},
  borough: {$in: ["Manhattan", "Brooklyn"]},
  cuisine: {$nin: ["American", "Chinese"]}
})

// 18. Grade with score 2 AND grade with score 6
db.restaurants.find({
  "grades.score": 2,
  "grades.score": 6
})

// 19. As above, in Manhattan
db.restaurants.find({
  "grades.score": 2,
  "grades.score": 6,
  borough: "Manhattan"
})

// 20. 2 or 6, Manhattan/Brooklyn
db.restaurants.find({
  "grades.score": {$in: [2,6]},
  borough: {$in: ["Manhattan", "Brooklyn"]}
})

// 21. 2 or 6, Manhattan/Brooklyn, not American
db.restaurants.find({
  "grades.score": {$in: [2,6]},
  borough: {$in: ["Manhattan", "Brooklyn"]},
  cuisine: {$ne: "American"}
})

// 22. 2 or 6, Manhattan/Brooklyn, not American or Chinese
db.restaurants.find({
  "grades.score": {$in: [2,6]},
  borough: {$in: ["Manhattan", "Brooklyn"]},
  cuisine: {$nin: ["American", "Chinese"]}
})

// 23. Grade score 2 OR 6
db.restaurants.find({
  "grades.score": {$in: [2,6]}
})


-- Query For Movies Collection
// 1. Movies released in 1893
db.movies.find({
  year: 1893
})

// 2. Movies with runtime > 120
db.movies.find({
  runtime: {$gt: 120}
})

// 3. Movies with 'Short' genre
db.movies.find({
  genres: "Short"
})

// 4. Movies directed by 'William K.L. Dickson'
db.movies.find({
  directors: "William K.L. Dickson"
})

// 6. Movies released in USA
db.movies.find({
  countries: "USA"
})

// 7. Movies rated as 'UNRATED'
db.movies.find({
  rated: "UNRATED"
})

// 8. Movies with imdb votes > 1000
db.movies.find({
  "imdb.votes": {$gt: 1000}
})

// 9. IMDb rating > 7
db.movies.find({
  "imdb.rating": {$gt: 7}
})

// 10. Viewer rating > 4 on Tomatoes
db.movies.find({
  "tomatoes.viewer.rating": {$gt: 4}
})

// 11. Movies that received an award
db.movies.find({
  "awards.nominations": {$gt: 0}
})

// 12. Movies with at least one nomination, return key details
db.movies.find({
  "awards.nominations": {$gte: 1}
}, {
  title:1, languages:1, released:1, directors:1, writers:1, awards:1, year:1, genres:1, runtime:1, cast:1, countries:1
})

// 13. Movies with cast including Charles Kayser
db.movies.find({
  cast: "Charles Kayser"
}, {
  title:1, languages:1, released:1, directors:1, writers:1, awards:1, year:1, genres:1, runtime:1, cast:1, countries:1
})

// 14. Released on May 9, 1893
db.movies.find({
  released: ISODate("1893-05-09T00:00:00Z")
}, {
  title:1, languages:1, released:1, directors:1, writers:1, countries:1
})

// 14. Movies with a word 'scene' in title
db.movies.find({
  title: /scene/i
}, {
  title:1, languages:1, released:1, directors:1, writers:1, countries:1
})
