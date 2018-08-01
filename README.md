# Apache ErrorDocument Tests

## ErrorDocument
The ErrorDocument rule in an Apache config lets you set the response content for various error codes, such as
404, 500, and so on. 

If the ErrorDocument rule references an external URL (starting with "http(s)"), even if that is the same server
the Apache instance is serving up, then the response for an error code is actually a 302. 

## Running the test locally

### Build the container
`docker build -t <name> .`

### Run the container
`docker run -d --rm --name=apache-test -p 80:80 --mount type=bind,source="$(pwd)"/src/,target=/usr/local/apache2/htdocs/ <name>`

### Check localhost
http://localhost will return the default Ember application static HTML page with some extra requests that should 404.

The HTML referenced in the iframe will fail with a 302 that then redirects to a 200 that serves up the 404 page. Confusing, right?!

The JS file will respond with a 404 as expected. 