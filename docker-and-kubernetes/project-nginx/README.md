### Project-Customizing NGINX
- Project Overview:
    1. Run a container based on the NGINX image, using the specific tag 1.27.0
    2. Get an interactive shell runnig inside of the container
    3. Install the text editor ```vim```
    4. Modify the ```index.html``` from the NGINX server to deliver custom content

- Step-by-Step
```bash
docker pull nginx:1.27.0
docker run -d -p 80:80 --name web_server nginx:1.27.0
curl http:localhost
docker exec -t web_server sh
apt-get install vim
cat /user/share/nginx/html/index.html
```
- I'm using the Vscode extensions to change the html

- Project summary, limitations, and next steps:
    - **Limitations:** 
        - We ran many commands manually, and this is definitely not a scalable approach. If our container dies, and we need to recreate it, then we need to run all these commands again. There is a lot of room for error.
        - We edited files within the container, but if that container disappears, we lose all the changes we made. Containers' storage is, by definition, ephemeral, so we have to have a better way of handling persistent storage.
        - The commands we run are not written anywhere.
    