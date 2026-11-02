# Pattern Experiment Tasks

## I.) Error Report Pattern
You want to log in to an API with the goal to retrieve an access token for it.
As a result, you get back the following HTTP response:

**Pattern version:**

<img src="./images/Error Report Pattern.png" alt="HTTP/1.1 401 response" style="height: 150px; width:300px;"/>

**Without the pattern:**

<img src="./images/NON Error Report.png" alt="NON HTTP/1.1 401 response" style="height: 120px; width:300px;"/>

What does this response mean?

1. The request took too long to complete.
2. Your user does not have the necessary privileges for this resource.
3. You used invalid authentication credentials to access the resource. [CORRECT for both]
4. The resource could not be found.
5. The payload of the request is too large.


## II.) Error Report Pattern 2
You receive the task to register many people at your company for an upcoming workshop.
To automate the process, you do not use the web interface, but write a small script to interact with their API.

During registration, you get the following response back for one colleague:

**Pattern version:**

<img src="./images/Error Report Pattern2.png" alt="ER2" style="height: 200px; width:400px;"/>

**Without the pattern:**

<img src="./images/NON Error Report2.png" alt="NON ER2" style="height: 200px; width:400px;"/>

You also have access to an API documentation, which explain some of the custom error codes:

<img src="./images/ER Documentation.png" alt="94,95,96,97" style="height: 100px; width:400px;"/>

What does this response mean?

1. The 'birthday' field exceeded the maximum length.
2. The 'name' field contained forbidden characters.
3. The 'name' field exceeded the maximum length.
4. The 'birthday' field was not filled out.
5. The 'birthday' field contained invalid input. [CORRECT for both]

## III.) Request Bundle Pattern
You are responsible for the customer management at a retail store.
To obtain information about customers, you communicate directly with an API that provides customer data from a database.
The API offers the following resource to retrieve the details of a customer by ID:

`GET https://my-retail-store.com/customers/$id`

**Pattern version:**

Additionally, it allows you to fetch multiple customers at once by using comma-separated IDs:

`GET https://my-retail-store.com/customers/$id1,$id2,...`

**Without the pattern:**

...no additional info...

Describe how you would request the information of the four customers with the IDs `5`, `9`, `13`, and `24`.
Use the given example syntax for your answer. (free-text)

Pattern answer: `GET https://my-retail-store.com/customers/5,9,13,24`<br>
Without pattern answer:
  - `GET https://my-retail-store.com/customers/5`
  - `GET https://my-retail-store.com/customers/9`
  - `GET https://my-retail-store.com/customers/13`
  - `GET https://my-retail-store.com/customers/24`


## IV.) Request Bundle Pattern 2
You are responsible for the management of articles at a grocery warehouse.
The warehouse API offers the following resource to delete an article with the respective item ID:

`DELETE https://my-grocery.com/products/$id`

**Pattern version:**

Additionally, the API allows you to delete multiple items at once by using comma-separated IDs:

`DELETE https://my-grocery.com/products/$id1,$id2,...`

**Without the pattern:**

...no additional info...

Describe how you would delete the four articles with the IDs `12`, `16`, `27`, and `35`.
Use the given example syntax for your answer. (free-text)

Pattern answer: `DELETE https://my-grocery.com/products/12,16,27,35`<br>
Without pattern answer:
  - `DELETE https://my-grocery.com/products/12`
  - `DELETE https://my-grocery.com/products/16`
  - `DELETE https://my-grocery.com/products/27`
  - `DELETE https://my-grocery.com/products/35`

## V.) Wish List Pattern
You are working at a university and frequently need to access student information via an API.
An example student object looks like this:

<img src="./images/Wish List.png" alt="Example student object" style="height: 150px; width:270px;"/>

For a follow-up API request, a student object is required with the following attributes **only**:

`studentName`, `birthday`, and `postalCode`.

**Pattern version:**

You can retrieve a customized student object with this resource and syntax: 

`const student = GET https://my-university.org:8080/students/$id?fields=attribute1,attribute2,...`

**Without the pattern:**

You can retrieve and refine a student object with this resource and syntax: 

```
const response = GET https://my-university.org:8080/students/$id
const student = {
  attribute1: response.attribute1,
  ...
}
```

Using the described syntax, formulate the necessary request and potential follow-up actions to retrieve the described object for the student with ID `20`. (free-text)

Pattern answer: `const student = GET https://my-university.org:8080/students/20?fields=studentName,birthday,postalCode`<br>
Without pattern answer:
```
const response = GET https://my-university.org:8080/students/20
const student = {
  studentName: response.studentName,
  birthday: response.birthday,
  postalCode: response.postalCode
}
```
## VI.) Wish List Pattern 2
You are using the API of an online calendar service.
An example of an HTTP response for a single calendar entry looks like this:

<img src="./images/Wish Template.png" alt="W-Template" style="height: 400px; width:300px;"/>

For a follow-up API request, an entry object is required with **only** the following attributes **only**:

`title`, `attendees`, and `status`.

**Pattern version:**

You can retrieve a customized entry object with this resource and syntax: 

`const entry = GET https://my-calendar.io:8080/entries/$id?fields=attribute1,attribute2,...`

**Without the pattern:**

You can retrieve and refine an entry object with this resource and syntax: 

```
const response = GET https://my-calendar.io:8080/entries/$id
const entry = {
  attribute1: response.attribute1,
  ...
}
```

Using the described syntax, formulate the necessary request and potential follow-up actions to retrieve the described object for the entry with ID `167`. (free-text)

Pattern answer: `const entry = GET https://my-calendar.io:8080/entries/167?fields=title,attendees,status`<br>
Without pattern answer:
```
const response = GET https://my-calendar.io:8080/entries/167
const entry = {
  title: response.title,
  attendees: response.attendees,
  status: response.status
}
```


## VII.) API Gateway Pattern

**Pattern version:**

In a distributed system, we have three clients that communicate with an *API Gateway*.
This *API Gateway* is connected to four services providing functionality.
All three clients are using each of the four services.

<img src="./images/API Gateway.PNG" alt="API" style="height: 400px; width:450px;"/>

**Without the pattern:**

In a distributed system, we have three clients that communicate with four services providing functionality.
All three clients are using each of the four services.

<img src="./images/NON API Gateway.png" alt="NON API" style="height: 400px; width:350px;"/>

To extend the available computing resources, *Service 3* is moved to another machine with a different IP address, which changes its endpoint.
Name **all** components from the diagram that have to be changed as a result of this migration. 

(free-text)
- Pattern answer: API Gateway
- Without pattern answer: Client 1, Client 2, Client 3


## VIII.) API Gateway Pattern 2

**Pattern version:**

In a distributed system, we have three clients that communicate with an *API Gateway*.
This *API Gateway* is connected to four services, providing functionality.
All three clients are using each of the four services.

<img src="./images/API Gateway2.png" alt="API2" style="height: 400px; width:450px;"/>

**Without the pattern:**

In a distributed system, we have three clients that communicate with four services, providing functionality.
All three clients are using each of the four services.

<img src="./images/NON API Gateway2.png" alt="NON API2" style="height: 400px; width:320px;"/>

Due to a company site consolidation, *MainService* is moved to another machine in a new data center, which changes its IP address and endpoint.
Name **all** components from the diagram that have to be changed as a result of this migration. 

(free-text)
- Pattern answer: API Gateway
- Without pattern answer: Web App 1, Mobile App 1, Mobile App 2

## IX.) Parameter Tree Pattern
You retrieve the details of the module "Software Engineering 1" from the university API.
The response looks as follows:

**Pattern version:**

<img src="./images/Parameter Tree.PNG" alt="PT" style="height: 900px; width:350px;"/>

**Without the pattern:**

<img src="./images/NON Parameter Tree.png" alt="NON PT" style="height: 700px; width:350px;"/>

How many "Computer Science" students are registered for the module "Software Engineering 1"?

(free-text)
Four. [CORRECT for both]


## X.) Parameter Tree Pattern 2
You use a cinema API to retrieve all movies that will be screened in your hometown tomorrow.
The response looks as follows:

**Pattern version:**

<img src="./images/Parameter Tree2.png" alt="PT2" style="height: 800px; width:330px;"/>

**Without the pattern:**

<img src="./images/NON Parameter Tree2.png" alt="NON PT2" style="height: 700px; width:350px;"/>

How many movies of the category "thriller" can you choose from?

(free-text)
Two [CORRECT for both]


## XI.) Metadata Element Pattern
You use the search resource of the API of a video streaming platform with the query "Microservice API".
As a result, you get the following response:

**Pattern version:**

<img src="./images/Metadata Element.png" alt="ME" style="height: 700px; width:750px;"/>

**Without the pattern:**

<img src="./images/NON Metadata Element.png" alt="NME" style="height: 600px; width:750px;"/>

How did the API sort the retrieved videos?

1. The videos are sorted in ascending order regarding the published date. 
2. The videos are sorted in ascending order regarding the number of views.
3. The videos are sorted in descending order regarding the length.
4. The videos are sorted in descending order regarding the number of views.
5. The videos are sorted in descending order regarding the published date. [CORRECT for both]

## XII.) Metadata Element Pattern 2
You use the search resource of the API of a shopping platform with the query "Coffee".
As a result, you get the following response:

**Pattern version:**

<img src="./images/Metadata Element2.png" alt="ME2" style="height: 550px; width:600px;"/>

**Without the pattern:**

<img src="./images/NON Metadata Element2.png" alt="NME2" style="height: 550px; width:600px;"/>

How did the API sort the retrieved products?

1. The products are sorted in ascending order regarding the shipping costs. [CORRECT for both]
2. The products are sorted in ascending order regarding the rating.
3. The products are sorted in descending order regarding the rating.
4. The products are sorted in descending order regarding the title.
5. The products are sorted in descending order regarding the base price.
