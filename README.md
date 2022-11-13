# AppyHigh Technology_nodejs

##  : Cab Booking Management APIs and Database Integration Assignment 

### Discription of developed Assignmnet

- Tech Stack
  1) Nodejs
  2) ExpressJs
  3) MongoDB

- Packages Used 
  1) JWT(jasonWebToken) for creation of token used for Authentication and Authorization

- Database Collections
  1) Rider Colletion _ [Details of Riders(users)]
```yaml
   first_name: {
          type: String,
          required: true,
          trim: true
        },
    last_name: {
          type: String,
          required: true,
          trim: true
        },
    email: {
            type: String,
            required: true,
            unique: true,
            trim: true
          },
    username: {
          type: String,
          unique: true,
          required: true,
          lowercase: true,
          trim: true
        },
    phone: {
          type: Number,
          required: true,
          unique: true,
          minlength: 10,
          maxlength: 10,
          trim: true
        },
    password: {
          type: String,
          required: true,
          trim: true
        },
    }, { timestamps: true }); 

```
  2) Driver Collection _  [Details of drivers]
```yaml
    first_name: {
          type: String,
          required: true,
          trim: true
        },
    last_name: {
          type: String,
          required: true,
          trim: true
        },
    cab_name: {
          type: String,
          required: true,
          trim: true
        },
    cab_number: {
          type: String,
          required: true,
          trim: true
        },
    email: {
            type: String,
            required: true,
            unique: true,
            trim: true
          },
    phone: {
          type: Number,
          required: true,
          unique: true,
          minlength: 10,
          maxlength: 10,
          trim: true
        },
    password: {
          type: String,
          required: true,
          trim: true
        },
    }, { timestamps: true });
```
  3) DriverActivity Collection _  [here we had connected with the Driver collection]
```yaml
    Propertyid: {
        type: ObjectId,
        ref: "property"
    },
    Cropname: {
        type: String,
        trim: true
      },
    Cropcyclestage: {
        type: String,
        trim: true
    },
},{timestamps: true})
```
  4) Booking Collection _  [here we had connected with the rider collection and driver collection]
```yaml
    riderid: {
        type: ObjectId,
        ref: 'rider',
        required: true,
        unique: true
    },
    driverid: {
        type: ObjectId,
        ref: 'driver',
        required: true,
        unique: true
    },
    location:{
          type:{type: String},
          coordinates:[]
      },
    fare: {
        type: Number,
        trim: true
    },
    riderStatus: {
        type: Boolean,
        default: false,
    },
    fromlocation:{
        type:{type: String},
        coordinates:[]
    },
    tolocation:{
        type:{type: String},
        coordinates:[]
    },
}, { timestamps: true })

  bookingSchema.index({location:"2dsphere"});
  bookingSchema.index({fromlocation:"2dsphere"});
  bookingSchema.index({tolocation:"2dsphere"});
```

## Features 

- Type 
  1) There will two type of group one is Rider and other is Driver 
  2) Drivers can register their cab in the application
  3) Riders can registers own details in the application
  4) Riders and Drivers both are registers own location
  5) Riders search cab under 5km after registers own location and booking the cab
  4) Drivers view the riders location and pickup the rider and drop the rider location
  7) Taxi/cab fare should be calculated based on the distance between the pickup and drop point 
    -we set the fare (Rs. 20 per KM rate) 
  5) We can do CRUD operations for All [Riders and Drivers]
 
## Routes

### Rider Routes
-  POST '/rlogin'
   1) Used for login the rider by there Email and Password

- POST '/rider'
  1) Used for creating the Rider details

- GET '/getnearestcab'
  1) Used for fetching all the nearest cab



### Driver Routes
- POST '/dlogin'
  1) Used for login the driver by there Email and Password

- POST '/driver'
  1) used for creating the driver details
  Used for fetching all the properties and inside property we saw to each organization and crop



### DriverActivity Routes
- POST '/createactivity'
  1) Used for creating of DriverActivity details and inside we pushed driverId

- PUT '/updateActivity'
  1) Used for updating the DriverActivity

  ### Booking Routes
- POST '/createBook'
  1) Used for creating of Booking details and inside we pushed riderId and driverId

- GET '/viewBooking'
  1) Used for view The bookings

