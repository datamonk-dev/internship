
---

## Let’s Try Docker for Real – A Hands-On Demo!

> **Haven’t installed Docker yet?**
> No worries — you can get it from the official site here:
> [Install Docker Desktop](https://docs.docker.com/get-docker/)
> It supports Windows, macOS, and Linux!

Once Docker is installed, open your terminal, and we’re ready to roll.

---

## Step 1: Pull an Image & Run It

Let’s start by running something *super simple* to make sure Docker’s working properly.

```bash
docker run hello-world
```

Here’s what happens behind the scenes:

* Docker checks if you already have the `hello-world` image.
* If not, it **downloads** it from Docker Hub.
* It **spins up** a container using that image.
* It prints a cheerful message saying Docker is working.

Boom — your first container is alive!

---

## Docker Workflow – What You’ll Actually Do

Now that we’ve run a basic image, let’s talk about the steps you’ll usually follow to **Dockerize your own app**.

---

### **Write a Dockerfile**

This is your app’s recipe — you’ll define how to package it in an image.

---

### **Build the Image**

```bash
docker build -t my-app .
```

This command reads your Dockerfile and creates a reusable image called `my-app`.

---

### **List Your Images**

```bash
docker images
```

See what images are on your system — like browsing your app pantry.

---

## Writing a Dockerfile – A Real Example

Let’s take a simple Python web app — maybe a tiny Flask app — and write a Dockerfile for it.

Here’s what a complete Dockerfile might look like:

```Dockerfile
FROM python:3.11
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python", "app.py"]
```

Let’s walk through it together — line by line. Don’t worry if it looks a bit mysterious at first; it’ll make sense in a moment!

---

### `FROM python:3.11`

This line tells Docker:

> “Hey, start with Python version 3.11 as the base image.”

Think of it as the foundation of your house — you’re saying, “I want a system that already has Python installed.”

Docker has many such base images available — for Python, Node.js, Java, and even tiny Linux distros like Alpine.

---

### `WORKDIR /app`

This sets the **working directory** inside the container.

It’s like saying:

> “Whenever I run commands or add files, do it from this folder: `/app`.”

If the folder doesn’t exist yet, Docker creates it for you. Simple!

---

### `COPY . .`

This line says:

> “Copy everything from the current folder on *my machine* into the `/app` folder in the container.”

So your app code, requirements.txt file, and everything else gets moved into the container.

The first `.` refers to your local folder.
The second `.` refers to the container’s working directory (which we set as `/app`).

---

### `RUN pip install -r requirements.txt`

Now we tell Docker:

> “Install the dependencies my app needs.”

We assume you have a `requirements.txt` file listing packages like Flask, requests, etc.
This line runs when the image is **built**, not when the container starts.

It’s like packing everything your app needs *before* you hit the road.

---

### `EXPOSE 5000`

This line declares the port your app will use.

If you're running a Flask app, it typically runs on port 5000.
This doesn’t actually open the port — it just tells Docker, “Heads up! My app uses this port.”

When you run the container, you still need to use `-p 5000:5000` to map it to your host system.

---

### `CMD ["python", "app.py"]`

This is the command Docker runs when the container **starts**.

It’s like saying:

> “When someone runs this image, launch the app by running `python app.py`.”

The syntax here is in array form (`["python", "app.py"]`) because it’s more precise and avoids issues on different operating systems.

---

## You’re Building It the Right Way

And that’s it! With just a few lines, you’ve:

* Picked a clean Python base
* Copied your code
* Installed dependencies
* Exposed a port
* Defined the command to run your app

The best part? You only write this once per app — and reuse it forever.

So go ahead, try building it:

```bash
docker build -t my-python-app .
docker run -p 5000:5000 my-python-app
```

And if all goes well, your app will be running in a container!

---

## Deep Breath — You’ve Got This

You now understand:

* How to pull and run containers
* The end-to-end Docker workflow
* And how to write your very first Dockerfile

If it still feels like a lot — don’t worry! You’ll repeat this workflow often, and each time it’ll become more familiar.

---

## Useful Links

* [Install Docker](https://docs.docker.com/get-docker/)
* [Docker Run Docs](https://docs.docker.com/engine/reference/commandline/run/)
* [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
* [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

---

## Try This: Docker Workflow Exercises

---

* **Run the Classic `hello-world` Container**
  Confirm your Docker setup works by running the built-in `hello-world` container.

* **Write a Dockerfile for a Simple Python App**
  Use the example provided to write your own Dockerfile for a basic Flask or CLI Python script.

* **Build and Tag Your Image**
  Build the image from your Dockerfile and give it a custom name like `my-first-app`.

* **Run Your App on a Specific Port**
  Run the container using `-p` to expose the correct port and make sure it’s accessible in the browser.

* **List Your Local Images**
  Check which Docker images are saved on your machine and inspect their sizes.

* **Inspect Running Containers**
  Use `docker ps` to see what's running — then try `docker logs` or `docker exec` to explore inside.

* **Stop and Clean Up**
  Stop a running container and remove it. Try also deleting an image with `docker rmi`.

---