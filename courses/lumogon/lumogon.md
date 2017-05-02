!SLIDE[bg=_images/background.png] center inverse
<script type="text/javascript" src="file/_files/shared/timeline.js"></script>

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css" integrity="sha384-rwoIResjU2yc3z8GV/NPeZWAv56rSmLldC3R/AZzGRnGxQQKnKkoFVhFQhNUwEyJ" crossorigin="anonymous">
<link rel="stylesheet" href="file/_files/shared/slides.css">
<link rel="stylesheet" href="file/_files/shared/atelier-cave-light.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/tether/1.4.0/js/tether.min.js" integrity="sha384-DztdAPBWPRXSA/3eYEEUWrWCy7G5KFbe8fFjk5JAIxUYHKkDx6Qin1DkWx51bBrb" crossorigin="anonymous"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js" integrity="sha384-vBWWzlZJ8ea9aCX4pEW3rVHjgjt7zpkNpZk+02D9phzyeVkE+jo0ieGizqPLForn" crossorigin="anonymous"></script>


## Introduction to Lumogon 

!SLIDE slide1
<script> 
audio("slide1")
timeline([1000,2000,3000,4000],"slide1")
</script>

# Lumogon

## Lumogon is a tool for inspecting, reporting on, and analyizing your container applications.

<ul>
<li>

## How Lumogon works

</li>
<li>

## How to install Lumogon

</li>
<li>

## Basic usage

</li>

<!-- 
Lumogon is an open source tool maintained by Puppet, for inspecting, reporting on, and analyizing your container applications.
In this course you'll learn how Lumogon works, how to install it, and some basic usage.
-->

!SLIDE slide2
<script> 
audio("slide2")
timeline([1000,2000,3000,4000],"slide2")
</script>

# Why Lumogon?

<div class="container">
<div class="row">
<div class="time1 col">

![Container](_images/container.svg)

</div>
<div class="time2 col offset-1">

![Several containers](_images/containers.svg)

</div>
</div>
<div class="row">
<div class="time3 col">

![Container with a question mark](_images/container_question_mark.svg)

</div>
<div class="time4 col offset-1">

![Container with exclaimation point](_images/container_exclaimation_point.svg)

</div>
</div>
</div>

<!--
Containerization provides a revolutionary way to package and ship software by ensuring a consistent environment from development through production.
Unfortunately, along with this benefit comes a serious drawback. Because containers are treated as a black box, it's very hard to find out what's inside.
This makes auditing really difficult and means you're never quite sure that you're infrastructure is secure when the next security vulerabilty is discovered.
-->

!SLIDE slide3
<script> 
audio("slide3")
timeline([1000,2000,3000,4000],"slide3")
</script>

# Why Lumogon? 

<div class="container">
<div class="row">
<div class="col time1">

![Look inside your containers](_images/container_look_inside.svg)

</div>
</div>
<div class="row">
<div class="col">
<ul>
<li class="time2">

## Information about the container itself

</li>
<li class="time3">

## What's running inside it

</li>
<li class="time4">

## Packages installed 

</li>
</ul>
</div>
</div>
</div>

<!--
Lumogon solves this problem by letting you look inside your containers and expose as much information as possible.
You can expose not only information about the container itself but also get insight into what's running inside it.
Lumogon also gives you insight into things like packages installed within a container even if they aren't running.
-->

!SLIDE slide4
<script> 
audio("slide4")
timeline([1000,2000,3000,4000,5000,6000],"slide4")
</script>

# Getting started

<div class="container">
<div class="row">
<div class="col">

![Docker logo](_images/docker.svg)

</div>
<div class="col">
<div class="row time1">

`docker pull puppet/lumogon`

</div>
</div>
<div class="row">
<div class="col time2">
<code>
docker run<span class="time3"> --rm</span><span class="time4"> -v /var/run/docker.sock:/var/run/docker.sock</span><span class="time5"> puppet/lumogon</span><span class="time6"> scan container_name</span>
</div>
</div>
</div>
<!--
Lumogon is easy to install because it's packaged and shipped as a Docker container.
First you'll need docker installed and properly configured, for more information on that go to docker.com.
Once that's done, just run `docker pull puppet/lumogon` to download the latest image.
To use Lumogon, you'll need to use docker run. Let's walk through constructing that command.
First, type `docker run`. We want to remove the container after it's done so we'll add `--rm`.
Lumogon needs to have access to the docker socket on the host, so we'll use `-v` to map a volume and then
"/var/run/docker.sock:/var/run/docker.sock" to map the system docker socket to the same location on the container.
That's all the options we need, so next we can add the name of the images `puppet/lumogon`.
Finally, pass in the command "scan" and the name of the container to be scanned.

`docker run --rm  -v /var/run/docker.sock:/var/run/docker.sock puppet/lumogon scan name-of-container`

-->

!SLIDE slide5
<script> 
audio("slide5")
</script>

# Lumogon output

    @@@ Shell
    docker run --rm  -v /var/run/docker.sock:/var/run/docker.sock puppet/lumogon scan name-of-container | jq .

.break

<!--
Lumogon returns output in JSON format, which is very readable by machines but can be difficult for humans.
You might want to save the results to a file to make them easier to format and read.
For this example, we'll use the `jq` utility, which is available for most major operating systems.

Passing the results into `jq .` does some nice syntax highlighting and formatting to make JSON readable.
`jq` offers some pretty advanced parsing and query options, to learn more visit: stedolan.github.io/jq
-->

!SLIDE slide6
<script> 
audio("slide6")
</script>


# Summary

<div class="container">
<div class="col-2">
<div class="row time1">

![Container with a question mark](_images/container_question_mark.svg)

</div>
<div class="row time2">

![Puppet logo](_images/puppet_logo.svg)

</div>
<div class="col">
<div class="row time3">

`docker pull puppet/lumogon`

</div>
<div class="row">
<code>
<span class="time4">docker run --rm  -v /var/run/docker.sock:/var/run/docker.sock puppet/lumogon scan name-of-container</span><span class="time5"> | jq .</span>
</code>
</div>
</div>
</div>

<!--
In summary, it's hard to find much information about what's actually going on inside containers.
Lumogon is an open source project, maintained by Puppet, that solves this problem by providing detailed information about your containers.
You can install Lumogon with a single docker command `docker pull puppet/lumogon`, and run it with a docker run command.
Lumogon outputs JSON, so you might want to use an external tool like `jq` to make it more human readable.
-->

!SLIDE[bg=_images/background.png] center inverse

## Thanks for participating in Introduction to Lumogon