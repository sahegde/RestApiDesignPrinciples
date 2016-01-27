# RestApiDesignPrinciples

A very useful link on REST design principles
http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api

Use sub resourcing to model relationships
example - GET /tickets/123/messages

if the relation can existing independently that it makes sense to have an end point.
if not then try to make the relation as part of the output of the first resource itself.

What about actions that don't fit into the world of CRUD operations?

This is where things can get fuzzy. There are a number of approaches:

- Restructure the action to appear like a field of a resource. This works if the action doesn't take parameters. For example an activate action could be mapped to a boolean activated field and updated via a PATCH to the resource.
- Treat it like a sub-resource with RESTful principles. For example, GitHub's API lets you star a gist with PUT /gists/:id/star and unstar with DELETE /gists/:id/star.
- Sometimes you really have no way to map the action to a sensible RESTful structure. For example, a multi-resource search doesn't really make sense to be applied to a specific resource's endpoint. In this case, /search would make the most sense even though it isn't a resource. This is OK - just do what's right from the perspective of the API consumer and make sure it's documented clearly to avoid confusion.


- Use SSL everywhere
- provide very good documentation
- versioning is very important
- better the versioning should be in url and not the header
- 
Filtering: Use a unique query parameter for each field that implements filtering. For example, when requesting a list of tickets from the /tickets endpoint, you may want to limit these to only those in the open state. This could be accomplished with a request like GET /tickets?state=open. Here, state is a query parameter that implements a filter.

Sorting

GET /tickets?sort=-priority - Retrieves a list of tickets in descending order of priority
GET /tickets?sort=-priority,created_at - Retrieves a list of tickets in descending order of priority. Within a specific priority, older tickets are ordered first

Searching
GET /tickets?q=return&state=open&sort=-priority,created_at - Retrieve the highest priority open tickets mentioning the word 'return'

Limiting which fields are returned by the API
GET /tickets?fields=id,subject,customer_name,updated_at&state=open&sort=-updated_at

