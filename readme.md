## What is Containerisation?
Containerization involves building self-sufficient software packages that perform consistently, regardless of the machines they run on.

Basically taking the snapshot of a machine, the filesystem and letting you use and deploy it as a construct.

## Images vs Containers
A Docker **image** behaves like a template from which consistent containers can be created. If Docker was a traditional virtual machine, the image could be likened to the ISO file used to install your VM. 
This isn't a robust comparison, **Docker differs from VMs** in terms of both concept and implementation, but it's a useful starting point nonetheless.

Images define the initial filesystem state of new containers. They bundle your application's source code and its dependencies into a self-contained package that' ready to use with a container runtime. Within the image, filesystem content is represented as multiple independent layers.

## Example

1. We have a file called `index.js`
2. To create a **container** from it: 
   1. Creating an image using `docker build .` 

- the `docker build .` command helps you to take this `index.js` file and **describe** what all do I need along with the file and create an image from it.

### What is an image?
- It contains the `index.js` file.
- It also contains that this is an image which should have `node.js` in it.
- This is an image which should have a filesystem in it.
- It should **expose** a certain PORT.



- **Containers** are when you actually run code locally.
`docker run <image_id>`

- You only create an image once.

## Volumes

1. Used for persisting data across starts
2. Specifically useful for things like databases

### How? 
- `docker volume create <volume_database>`
- `docker run -v volume_database:/data/db -p 27017:27017 mongo`


## Networks
Networks are used to connect one container to another container to give them logical
binding.

### How?
- `docker network create my_custom_network`
- `docker run -p 3000:3000 --name backend --network my_custom_network <image_tag>`

- `docker run -v volume_database:/data/db`
   `--name mongo`
   `--network my_custom_network`
   `-p 27017:27017`
   `mongo`