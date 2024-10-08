## Docker project 1:Creating a Container from a Pulled Image
Objective: Pull the official Nginx image from Docker Hub and run it as a container.

# Steps:
Pull the Nginx Image:

docker pull nginx

![img-1](<../../folder1/Screenshot from 2024-10-07 15-16-52.png>)
#    1. Run the Nginx Container:

docker run --name my-nginx -d -p 5000:80 nginx
![img-2](<Screenshot from 2024-10-07 15-17-57.png>)
#    2. Verify the Container is Running:
        ◦ --name my-nginx: Assigns a name to the container.
        ◦ -d: Runs the container in detached mode.
        ◦ -p 5000:80: Maps port 5000 on your host to port 80 in the container.

docker ps
![img-3](<Screenshot from 2024-10-07 15-18-23.png>)
#    3. Check at browser
        ◦ Visit http://localhost:8080 in your browser. You should see the Nginx welcome page.
![img-4](<Screenshot from 2024-10-07 15-18-53.png>)
## Modifying the Container and Creating a New Image
Objective: Modify the running Nginx container to serve a custom HTML page and create a new image from this modified container.
Steps:
Access the Running Container:

docker exec -it my-nginx /bin/bash

#    1. Create a Custom HTML Page:

echo "<html><body><h1>Hello from Docker!</h1></body></html>" > /usr/share/nginx/html/index.html
![img-5](<Screenshot from 2024-10-07 15-19-33.png>)
#    2. Exit the Container:

exit

#    3. Commit the Changes to Create a New Image:

docker commit my-nginx custom-nginx
![img-7](<Screenshot from 2024-10-07 15-20-06.png>)
#    4. Run a Container from the New Image:

docker run --name my-custom-nginx -d -p 8081:80 custom-nginx
![img-8](<Screenshot from 2024-10-07 15-20-41.png>) 
#    5. Verify the New Container:
        ◦ Visit http://localhost:5000 in your browser. You should see your custom HTML page.

![img-9](<Screenshot from 2024-10-07 15-21-26.png>)
![img-10](<Screenshot from 2024-10-07 15-21-53.png>)

