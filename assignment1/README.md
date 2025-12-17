# Assignment 1 — Build & Run a Personalized Web Server Container

## Files Used

```
index.html   # Static HTML page
Dockerfile   # Builds the Nginx-based image
README.md    # Instructions and explanation
```

---

## Build the Docker Image

The Docker image is built using the official **nginx:alpine** image.

```bash
docker build -t sabeeh-site .
```

---

## Run the Container

The container is run so that the website is accessible on **port 7070** of the host machine.

```bash
docker run -d --name sabeeh-web -p 7070:80 sabeeh-site
```

---

## Test the Website

### Using a Browser

Open the following URL in a browser:

```
http://localhost:7070
```

### Using curl

```bash
curl http://localhost:7070
```

---

## Stop and Remove the Container

After testing, stop and remove the container:

```bash
docker stop sabeeh-web
docker rm sabeeh-web
```

---

## Explanation of Approach

* A simple `index.html` file is created with my name, a heading, and a short description.
* The Dockerfile uses **Nginx** to serve the static HTML content.
* Port `80` inside the container is mapped to port `7070` on the host.
* The container is tested using both a web browser and the `curl` command.
* Finally, the container is stopped and removed.
