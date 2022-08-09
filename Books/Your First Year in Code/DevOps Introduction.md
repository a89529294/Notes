- The *Cloud*: another company's computer.
	- Microsfot *Azure*, Amazon *AWS*, Google *Cloud*
- *Problems* when deploying to the *cloud*
	- different library verions between the machines.
	- different operating system between the machines.
- *Docker* and *Containerization*
	- You enclose *everything* you need the software to run in a container.
	- The *container* can be thought of as a tiny *operating system*.
	- When it comes to Docker, we distinguish between a *container* and the *file* that runs inside of it with the terms “*Docker container*” and “*Docker image*”
	1. Create a container using your preferred operating system.
	2. Include the source code of our app in the container.
	3. Include the libraries our application needs, along with any other piece of software our app relies on.
	4. Configure the container so that when it is accessed, the app starts automatically.
	5. Test the application thoroughly from inside the container.
	6. Once happy, send it to the customer(s). You are now confident that it will work on their side too, regardless of the operating system they use.”
- *Provisioning*
	- it means to set up the infrastructure needed for an application to work. This work is often automated and done in the cloud.
	- if someone wants to provision a test environment, they probably have to allocate some server space in order to put the containers inside and run them.
- *Continous Integration* & *Continous Delivery*
	- Some of the most well-know tools are *Jenkins*, *Travis*, and *bamboo*.
	1. You create a new feature requested by a customer.
	2. Your code gets reviewed and tested by members of your team.
	3. You add your changes to the code that will be delivered to the customer (the “release branch,” as devs call it).
	4. An automated process notices what you did and starts doing various things with the new version of the app, like trying to compile it, run any automated tests, and (you guessed it) prepare your Docker image. This is the “Continuous Integration” step.
	5. If everything works, the process sends this image to the customer’s servers. This is the “Continuous Delivery” step.”




