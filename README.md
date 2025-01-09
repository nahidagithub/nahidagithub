## API Testing  👋


**nahidagithub/nahidagithub** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Rest Booking API Testing with Postman Newman
This project demonstrates API testing using Postman, providing a collection of tests to validate
various endpoints of the API.
Features
• Tests for GET, POST, PUT, DELETE requests
• Collection of tests covering different API endpoints
• Environment setup for easy switching between environments
• Pre-request scripts for data setup
• Test scripts for assertions and validations
API Documentation:
https://documenter.getpostman.com/view/38968395/2sAYBUDCWC

##Technology used:

• Postman
• Newman
##Prerequisite:

• Node Js
• Newman
• Newman Html Report Library
##Installation

1. Postman: If you haven't already, https://www.postman.com/downloads/
2. Import the Postman collection:
1. Open Postman.
2. Click on the Import button.
3. Select the file from the repository.
3. Import the Postman environment:
1. In Postman, click on the gear icon in the top right corner.
2. Select Import and choose the file.
4. Newman and Report Installation Process:
1. Newman Install Command: npm install -g newman
5. Newman Html Report Install Command:
1. npm install -g newman-reporter-htmlextra
 Usage
1. Select Environment:
o In Postman, select the appropriate environment (e.g., Development, Production) from
the top-right dropdown.
2. Run Collection:
o Select the imported collection from the Collections sidebar.
o Click on the Runner button to open the collection runner.
o Select the desired environment.
o Click Start Test to run the collection.
3. View Results:
o Once the tests are complete, view the results in the Runner tab.
o Detailed test results can be viewed for each request.
4. Testing
5. Test Case Scenarios:
6. 1. Create New Booking
7. Request URL: https://restful-booker.herokuapp.com/booking/
Request Method: POST
Pre-request Script:


var firstName=pm.variables.replaceIn("{{$randomFirstName}}")
console.log(firstName)
pm.environment.set("Firstname",firstName)
let lastname=pm.variables.replaceIn("{{$randomLastName}}")
console.log(lastname)
pm.environment.set("LastName",lastname)
const moment=require("moment")
const today=moment()
var checkIn=today.add(3,'d').format("YYYY-MM-DD")
pm.environment.set("CheckIn",checkIn)
var checkOut=today.add(2,'m').format("YYYY-MM-DD")
pm.environment.set("CheckOut",checkOut)
let totalPrice=pm.variables.replaceIn("{{$randomInt}}")
pm.environment.set("TotalPrice",totalPrice)
var booLean=pm.variables.replaceIn("{{$randomBoolean}}")
pm.environment.set("BooLean",booLean)
Request Body:
{
"firstname" : "{{Firstname}}",
"lastname" : "{{LastName}}",
"totalprice" : {{TotalPrice}},
"depositpaid" : {{BooLean}},
"bookingdates" : {
"checkin" : "{{CheckIn}}",
"checkout" : "{{CheckOut}}"
},
"additionalneeds" : "Breakfast"
}
Response Body:
{
"bookingid": 5594,
"booking": {
"firstname": "Francisco",
"lastname": "Walter",
"totalprice": 813,
"depositpaid": false,
"bookingdates": {
"checkin": "2024-12-08",
"checkout": "2024-12-08"
},
"additionalneeds": "Breakfast"
}
}
2. Get Booking Details By ID
Request URL: https://restful-booker.herokuapp.com/booking/bookingid
Request Method: GET
Response Body:
{
"firstname": "Francisco",
"lastname": "Walter",
"totalprice": 813,
"depositpaid": false,
"bookingdates": {
"checkin": "2024-12-08",
"checkout": "2024-12-08"
},
"additionalneeds": "Breakfast"
}
3.Create A Token For Authentication.
Request URL: https://restful-booker.herokuapp.com/auth
Request Method: POST
Pre-request Script: None
Request Body:
{
 "username": "admin",
 "password": "password123"
}
Response Body:
{
 "token": "06eb798bf6f2caa"
}
4. Update the Booking Details
Request URL:https://restful-booker.herokuapp.com/booking/bookingid
Request Method: PUT
Pre-request Script:
var firstName=pm.variables.replaceIn("{{$randomFirstName}}")
console.log(firstName)
pm.environment.set("updated_Firstname",firstName)
let lastname=pm.variables.replaceIn("{{$randomLastName}}")
console.log(lastname)
pm.environment.set("updated_LastName",lastname)
const moment=require("moment")
const today=moment()
var checkIn=today.add(3,'d').format("YYYY-MM-DD")
pm.environment.set("updated_CheckIn",checkIn)
var checkOut=today.add(2,'m').format("YYYY-MM-DD")
pm.environment.set("updated_CheckOut",checkOut)
let totalPrice=pm.variables.replaceIn("{{$randomInt}}")
pm.environment.set("updated_TotalPrice",totalPrice)
var booLean=pm.variables.replaceIn("{{$randomBoolean}}")
pm.environment.set("updated_BooLean",booLean)
Request Body:
{
"firstname" : "{{updated_Firstname}}",
"lastname" : "{{updated_LastName}}",
"totalprice" : {{updated_TotalPrice}},
"depositpaid" : {{updated_BooLean}},
"bookingdates" : {
"checkin" : "{{updated_CheckIn}}",
"checkout" : "{{updated_CheckOut}}"
},
"additionalneeds" : "Breakfast"
}
Response Body:
{
"firstname": "Roma",
"lastname": "Mosciski",
"totalprice": 159,
"depositpaid": false,
"bookingdates": {
"checkin": "2024-11-27",
"checkout": "2024-11-27"
},
"additionalneeds": "Breakfast"
}
5. Delete Booking Record
Request URL: https://restful-booker.herokuapp.com/booking/bookingid
Request Method: DELETE
Response Body: None

Run Command:
• Run Command for Console:
newman run 28_Batch.postman_collection.json -e 28-
Batch.postman_environment.json
• Run Command for Report:
newman run 28_Batch.postman_collection.json -e 28-
Batch.postman_environment.json -r cli,htmlextra
Newman Report Summary:
![image](https://github.com/user-attachments/assets/abed20a8-a07b-4aeb-a790-74f63594e6bd)



