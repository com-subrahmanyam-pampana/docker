Docker "Hello, World" Example
This folder contains a Dockerfile to build a very simple Docker image—one which contains a text file with the text "Hello, World"!—

# Building the Docker container
1.
docker build .
The command "docker build ." is used to build a Docker image from a Dockerfile located in the current directory.The docker buil command reads instructions from a Dockerfile which is a script containing a series of commands to assemble an image.

Context: The . in docker build . specifies the build context, which is the current directory. The context includes the Dockerfile and any files or directories referenced by it. Docker sends the contents of this context to the Docker daemon to build the image.

2.You can check the created image by running "docker image ls"
REPOSITORY     IMAGEID         TAG          CREATED
<none>        bc8ccfe50705     <none>        3 min ago
3.To run the container
You typically don’t run a container directly; instead, you start a container from an image.

docker  run -it  bc8ccfe50705 cat /test.txt
where bc8ccfe50705 is the image id that you build
You should see the text "Hello, World!"

The -it option in the docker run command is a combination of two flags that enhance the way you interact with a Docker container:
Flags Breakdown
-i (Interactive): This flag keeps the standard input (stdin) open for the container. It allows you to interact with the container's process, especially useful for running interactive applications or shell sessions inside the container.
-t (TTY): This flag allocates a pseudo-TTY (teletypewriter) for the container. It provides a terminal interface, making it possible to have a command-line environment that supports text formatting and interaction, which is useful for applications that require terminal features.
# Adding tag:
If you list the available images "docker image ls",you will see the all the images. It is very dificult for you to identify the image you created.While building an image, you can add a tag to your image 

docker build -t my-hello-world .

Now if you list the images  you can identify your image with tag name
REPOSITORY           TAG          IMAGEID
my-hello-world       latest        bc8ccfe50705


Now you can run the app with command 
docker run -it my-hello-world cat /test.txt