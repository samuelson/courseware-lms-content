!SLIDE[bg=_images/background.png] center inverse
<script type="text/javascript" src="file/_files/shared/timeline.js"></script>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<link rel="stylesheet" href="file/_files/shared/slides.css">

## Relationships

!SLIDE slide2
<script> 
audio("slide2")
timeline([2000,3000,4000,5000,6000,7000],"slide2")
</script>

# Resource

~~~DIV:time3 col-xs-6~~~
## Service
~~~ENDDIV~~~
~~~DIV:time5 col-xs-6~~~
## Service
~~~ENDDIV~~~
~~~DIV:container~~~
  ~~~DIV:col-xs-5~~~~~~DIV:parent~~~
      ![.time1.img1 file](_images/resource_file.png)
      ![.time2.img2 service](_images/resource_service.png)
      ![.time3.img3 package](_images/resource_package.png)
  ~~~ENDDIV~~~~~~ENDDIV~~~

  ~~~DIV:col-xs-5~~~~~~DIV:parent~~~
      ![.time4.img1 service](_images/resource_service.png)
      ![.time5.img2 package](_images/resource_package.png)
      ![.time6.img3 file](_images/resource_file.png)
    ~~~ENDDIV~~~
  ~~~ENDDIV~~~~~~ENDDIV~~~
~~~ENDDIV~~~
~~~DIV:time1 col-xs-3~~~
## File
~~~ENDDIV~~~
~~~DIV:time2 col-xs-3~~~
## Package
~~~ENDDIV~~~
~~~DIV:time6 col-xs-3~~~
## File
~~~ENDDIV~~~
~~~DIV:time4 col-xs-3~~~
## Package
~~~ENDDIV~~~

!SLIDE slide3
<script> 
audio("slide3")
timeline([17000],"slide3")
</script>

# A Package

    @@@ Puppet
    package { ‘openssh-server’:
      ensure => present,
      before => File[’/etc/ssh/sshd_config’],
    }



~~~DIV:time1 col-xs-1~~~~~~DIV:row~~~~~~DIV:col-xs-1~~~~~~ENDDIV~~~~~~DIV:col-xs-1~~~
[fa-long-arrow-up fa-5x]
~~~ENDDIV~~~~~~ENDDIV~~~~~~ENDDIV~~~

~~~DIV:time1 col-xs-12~~~
## Relationship metaparameter
~~~ENDDIV~~~

!SLIDE slide4
<script> 
audio("slide4")
timeline([1000,1000,11000,14000,15500],"slide4")
</script>

# Metaparameters

~~~DIV:time2 align-center big~~~
Metaparameters
~~~ENDDIV~~~
~~~DIV:time1 align-center big~~~
4
~~~ENDDIV~~~

~~~DIV:time3 align-center~~~
## Resource reference (or array of references)
~~~ENDDIV~~~

~~~DIV:time4 align-center~~~
[fa-long-arrow-down fa-5x]
~~~ENDDIV~~~

~~~DIV:time5 align-center~~~
## One or more target resources
~~~ENDDIV~~~

!SLIDE slide5
<script> 
audio("slide5")
timeline([3500,6500,19500,25500],"slide5")
</script>

# Relationship Metaparameters

~~~DIV:row~~~
~~~DIV:time1 col-xs-2~~~
## `before`
~~~ENDDIV~~~

~~~DIV:time3 col-xs-offset-1 col-xs-10~~~
## Causes a resource to be applied before the target resource.
~~~ENDDIV~~~
~~~ENDDIV~~~

~~~DIV:row~~~
~~~DIV:time2 col-xs-2~~~
## `require`
~~~ENDDIV~~~

~~~DIV:time4 col-xs-offset-1  col-xs-10~~~
## Causes a resource to be applied after the target resource.
~~~ENDDIV~~~
~~~ENDDIV~~~

!SLIDE slide6
<script> 
audio("slide6")
timeline([250,750,10000,11000],"slide6")
</script>


# Relationship Metaparameters

~~~DIV:row~~~
~~~DIV:time1 col-xs-2~~~
## `notify`
~~~ENDDIV~~~

~~~DIV:time2 col-xs-offset-1 col-xs-10~~~
## Causes a resource to be applied before the target resource. The target resource will refresh if the notifying resource changes.
~~~ENDDIV~~~
~~~ENDDIV~~~

~~~DIV:row~~~
~~~DIV:time3 col-xs-2~~~
## `subscribe`
~~~ENDDIV~~~

~~~DIV:time4 col-xs-offset-1  col-xs-10~~~
## Causes a resource to be applied after the target resource. The target resource will refresh if the target resource changes.
~~~ENDDIV~~~
~~~ENDDIV~~~

!SLIDE slide7
<script> 
audio("slide7")
timeline([2500,3500,4000],"slide7")
</script>


# Requirement

.huge.align-center.time1 2 Resources

~~~DIV:time2 align-center~~~
[fa-long-arrow-down fa-5x]
~~~ENDDIV~~~

.time3.align-center.huge Order Matters

!SLIDE slide8
<script> 
audio("slide8")
timeline([2000,5000,5250],"slide8")
</script>

# Requirement

.huge.align-center 2 Options

~~~DIV:time1 col-xs-3 col-xs-offset-1~~~
## `before`
~~~ENDDIV~~~

~~~DIV:time2 col-xs-3 col-xs-offset-1~~~
[fa-long-arrow-right fa-5x]
~~~ENDDIV~~~

~~~DIV:time3 col-xs-3 col-xs-offset-1~~~
## `require`
~~~ENDDIV~~~

!SLIDE slide9
<script> 
audio("slide9")
timeline([5000,9000],"slide9")
</script>

# Requirement

## before

    @@@ Puppet
    package { 'openssh-server':
      ensure => present,
      before => File['/etc/ssh/sshd_config'],
    }


~~~DIV:time1 col-xs-1~~~
~~~DIV:row~~~
~~~DIV:col-xs-1~~~
~~~ENDDIV~~~
~~~DIV:col-xs-1~~~
[fa-long-arrow-up fa-5x]
## Metaparameter
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~DIV:time2 col-xs-offset-3 col-xs-1~~~
~~~DIV:row~~~
[fa-long-arrow-up fa-5x]
## Target resource
~~~ENDDIV~~~
~~~ENDDIV~~~




!SLIDE slide10
<script> 
audio("slide10")
timeline([9000,17250],"slide10")
</script>

# Requirement

## require

    @@@ Puppet
    file { '/etc/ssh/sshd_config':
      ensure  => file,
      mode    => 600,
      source  => 'puppet:///modules/sshd/sshd_config',
      require => Package['openssh-server'],
    }

~~~DIV:time1 col-xs-1~~~
~~~DIV:row~~~
~~~DIV:col-xs-1~~~
~~~ENDDIV~~~
~~~DIV:col-xs-1~~~
[fa-long-arrow-up fa-5x]
## Metaparameter
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~DIV:time2 col-xs-offset-3 col-xs-1~~~
~~~DIV:row~~~
[fa-long-arrow-up fa-5x]
## Target resource
~~~ENDDIV~~~
~~~ENDDIV~~~



!SLIDE slide11
<script> 
audio("slide11")
timeline([8000,14000],"slide11")
</script>

# Ordering Arrows (Chaining Arrows)

.align-center.huge `->`

    @@@ Puppet
    Package['openssh-server'] -> File['/etc/ssh/sshd_config']

~~~DIV:time1~~~

* The resource on the left to be applied before the resource on the right.

~~~ENDDIV~~~

~~~DIV:time2~~~

* Written with a hyphen and a greater-than sign.

~~~ENDDIV~~~

!SLIDE slide12
<script> 
audio("slide12")
timeline([6500,14750],"slide12")
</script>

# With refresh

## notify

    @@@ Puppet
    file { '/etc/ssh/sshd_config':
      ensure  => file,
      mode    => 600,
      source  =>'puppet:///modules/sshd/sshd_config',
      notify  => Service['sshd'],
    }

~~~DIV:time1 col-xs-1~~~
~~~DIV:row~~~
~~~DIV:col-xs-1~~~
~~~ENDDIV~~~
~~~DIV:col-xs-1~~~
[fa-long-arrow-up fa-5x]
## Metaparameter
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~DIV:time2 col-xs-offset-2 col-xs-1~~~
~~~DIV:row~~~
[fa-long-arrow-up fa-5x]
## Target resource
~~~ENDDIV~~~
~~~ENDDIV~~~

!SLIDE slide13
<script> 
audio("slide13")
timeline([750,6750],"slide13")
</script>

# With refresh

## subscribe

    @@@ Puppet
    service { 'sshd':
      ensure    => running,
      enable    => true,
      subscribe => File['/etc/ssh/sshd_config'],
    }

~~~DIV:time1 col-xs-1~~~
~~~DIV:row~~~
~~~DIV:col-xs-1~~~
~~~ENDDIV~~~
~~~DIV:col-xs-1~~~
[fa-long-arrow-up fa-5x]
## Metaparameter
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~ENDDIV~~~
~~~DIV:time2 col-xs-offset-2 col-xs-1~~~
~~~DIV:row~~~
[fa-long-arrow-up fa-5x]
## Target resource
~~~ENDDIV~~~
~~~ENDDIV~~~

!SLIDE slide14
<script> 
audio("slide14")
timeline([9000,13000],"slide14")
</script>

# Notification arrow (Chaining Arrows)

.align-center.huge `~>`

    @@@ Puppet
    File['/etc/ntp.conf'] ~> Service['ntpd']

~~~DIV:time1~~~

* Written with a tilde and a greater-than sign.

~~~ENDDIV~~~
~~~DIV:time2~~~

* Causes the resource on the left to be applied first, and sends a refresh event to the resource on the right if the left resource changes.

~~~ENDDIV~~~

!SLIDE slide15
<script> 
audio("slide15")
timeline([7750,13500,21000,25000,31000,39000],"slide15")
</script>

# In Summary:  Metaparameters

~~~DIV:col-xs-5 col-xs-offset-1~~~

.big Before

~~~DIV:time1 col-xs-offset-1~~~

## `before`

~~~ENDDIV~~~
~~~DIV:time3 col-xs-offset-1~~~

## `notify`\*

~~~ENDDIV~~~
~~~DIV:time4 col-xs-offset-5~~~
\* With refresh
~~~ENDDIV~~~

~~~ENDDIV~~~

~~~DIV:col-xs-5 col-xs-offset-1~~~

.big After

~~~DIV:time2 col-xs-offset-1~~~

## `require`

~~~ENDDIV~~~
~~~DIV:time5 col-xs-offset-1~~~

## `subscribe`\*

~~~ENDDIV~~~
~~~DIV:time6 col-xs-offset-5~~~
\* With refresh
~~~ENDDIV~~~
~~~ENDDIV~~~



!SLIDE[bg=_images/background.png] center inverse slide16
<script> 
audio("slide16")
</script>

## Thanks for participating in relationships