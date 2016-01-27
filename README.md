# RestApiDesignPrinciples

A very useful link on REST design principles
http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api

Use sub resourcing to model relationships
example - GET /tickets/123/messages

if the relation can existing independently that it makes sense to have an end point.
if not then try to make the relation as part of the output of the first resource itself.
