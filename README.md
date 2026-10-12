# Assignment #4: Application Containerization

This is a simple Node.js web application designed for learning Docker containerization concepts.

## Application Overview

This application is a basic Express.js web server that:
- Serves a static HTML page at the root (`/`)
- Provides an API status endpoint at `/api/status`
- Includes a health check endpoint at `/health`
- Runs on port 3000 by default (configurable via PORT environment variable)

## What's Included

- **app.js**: Main application server file
- **package.json**: Node.js dependencies and project configuration
- **public/index.html**: Static HTML page that confirms successful containerization
- **public/style.css**: Styling for the web page

## Running Without Docker (for reference only)

If you wanted to run this application directly (not required for assignment):
```bash
npm install
npm start
```

## Your Docker Assignment

**DO NOT MODIFY THE APPLICATION CODE**

Your task is to containerize this existing application using Docker. You need to:

1. Create a `Dockerfile` that properly containerizes this Node.js application
2. Build a Docker image from your Dockerfile
3. Run a container from your image
4. Verify the application works by accessing it in your browser

## Starting the Application

- To build the docker image run the command:

```bash

```

- To run your docker container in port 3000 run the command:

```bash

```

## Reflection Question
**Answer the following question in the space below**: How does containerization with Docker differ from using virtual machines, and why might a development team choose Docker containers over VMs for deploying applications like the one you just containerized?
## Reflection Question

The main difference is what gets virtualized. A virtual machine pretends to be a whole computer. Each VM runs its own full operating system on top of a hypervisor, so it's big (usually gigabytes) and takes a while to boot. A Docker container is much lighter. It shares the host computer's kernel and only packs up the app and the stuff it needs to run, so it's usually just megabytes and starts in a couple of seconds.

For an app like this Node project, I think a team would pick Docker for a few reasons:

- **It runs the same everywhere.** The Node version and dependencies are baked into the image, so you don't get the "it works on my machine" problem.
- **It's cheaper to run.** Containers use less memory and disk, so you can fit more of them on one server.
- **It's fast.** Starting, stopping, and redeploying takes seconds, which makes testing a lot easier.
- **It's easy to share and scale.** Anyone can build the same image from the Dockerfile, and you can run extra copies if the app gets more traffic.

I saw this myself. I got the app running at localhost:3000 without installing Node on my computer, because Node was already inside the container. Getting Docker set up on Windows also taught me that it relies on a lightweight virtual machine layer (WSL 2) under the hood, but the containers themselves stay small and quick.

## Application Requirements for Docker

Your Dockerfile should ensure:
- The application has Node.js runtime available
- All application files are copied into the container
- Dependencies are installed (`npm install`)
- Port 3000 is exposed
- The application starts with `npm start`
- The container can be accessed from your host machine

## Verification

When your Docker container is running correctly:
- Navigate to `http://localhost:3000` (or whatever port you mapped)
- You should see a success page confirming containerization worked
- The `/api/status` endpoint should return JSON status information

## Troubleshooting Tips

- Make sure your port mapping is correct in the `docker run` command
- Check that all files are copied into the container
- Verify Node.js dependencies are installed in the container
- Use `docker logs <container-name>` to see application output

## File Structure Expected
```
docker-assignment/
├── Dockerfile          # You create this
├── app.js              # Provided
├── package.json        # Provided
├── public/             # Provided
│   ├── index.html      # Provided
│   └── style.css       # Provided
└── README.md           # This file
```

Good luck with your Docker containerization!