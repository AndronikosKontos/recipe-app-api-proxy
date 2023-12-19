# Recipe App API Proxy

NGINX proxy app for the recipe app API. The purpose of the proxy server is to handle the requests for the static files and redirect everything else to the Django application.

### Architecture

'default.conf.tpl' contains the configuration of the NGINX server and defines how to handle the requests to /static and the rest.

'entrypoint.sh' sets the environmental variables to the template configuration file and copies it to the specific location. Afterwards, it starts the server with the daemon off.

'Dockerfile' includes the instructions on how to build the docker image that will be pushed to AWS ECR.

### Environment Variables

 * `LISTEN_PORT` - Port to listen on (default: `8000`)
 * `APP_HOST` - Hostname of the app to forward requests to (default: `app`)
 * `APP_PORT` - Port of the app to forward requests to (default: `9000`)
