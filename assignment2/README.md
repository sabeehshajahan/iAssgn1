# Assignment 2 — Create & Run Two Containers That Communicate

## Steps and Commands Used

### 1. Create a custom Docker network

```bash
docker network create webnet
```

### 2. Pull hashicorp/http-echo

```bash
docker pull hashicorp/http-echo
```

### 3. Run the API container

```bash
docker run -d --name api --network webnet hashicorp/http-echo -text="Hello from API"
```

### 4. Run the Nginx container on the same network (port exposed to host)

```bash
docker run -d --name web --network webnet -p 8080:80 web-nginx
```

### 5. Update the Nginx static page (`index.html`) to fetch `/api`

### 6. Created nginx.conf

### 7. Test connectivity from the web container

```bash
docker exec -it web curl http://api:5678
```

Expected output:

```
Hello from API
```

---

## Verification

* Browser: `http://localhost:8080` → click **Call API** button, response should show `Hello from API`.
* Inside container: `docker exec -it web curl http://api:5678` returns `Hello from API`.

---

## Explanation of Approach

* Created a **custom network (`webnet`)** to allow containers to communicate using container names.
* Deployed **API container** using a prebuilt lightweight HTTP echo image.
* Deployed **web container (Nginx)** on the same network and exposed a host port.
* Updated the static HTML page to call the API via `/api`
* Verified communication both **inside the container** and from the browser.
* This approach demonstrates **container-to-container networking** and **reverse proxy via Nginx**.
