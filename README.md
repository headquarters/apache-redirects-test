`docker build -t <name> .`

`docker run -d --name=apache -p 80:80 --mount type=bind,source="$(pwd)"/src/,target=/usr/local/apache2/htdocs/ <name>`
