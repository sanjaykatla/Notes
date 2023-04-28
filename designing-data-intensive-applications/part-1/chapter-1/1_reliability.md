# Reliability

    System continue to work correctly even in the face of adversity
    (hardware or software fault, human errors)

For software
* The software performs the function that the use is expected
* It can tolerate the user making mistakes or using the 
software in an unexpected way
* Its performance is good enough for the required use case,
under the expected load, and volume
* The system prevents any unauthorized operations.


### Fault-tolerance
The things that can go wrong are called faults, and systems
that anticipate the faults and can cope up with them are called
fault-tolerance or resilient

### Fault vs Failure
A fault is usually defined as one component of the system 
deviating from its spec.

Failure is when the system as a whole stops providing the required
services to the user.

### Tolerating Faults vs Preventing Faults
* Generally Tolerating Faults is preferred.
* There are cases prevention is better than cure, because no
cure exists. This is the case if its the matter of security

### Hardware Faults
* Hard disk crashes
* Ram becomes faulty
* Power grid has a blackout
* Someone unplugs the wrong network cable

#### Hard Disk
* Hard disk are reported as having a mean time to failure
  (MTTF) of about 10 to 50 years.
* Thus, on a storage of 10,000 disks, we should expect on average
one disk to die per day.

#### Solutions
* Add redundancy to to individual hardware components in order to
reduce the failure rate of the system
* Disks may setup in a RAID configuration
* Server may have dual power source, and hot swappable cpus
* Datacenters may have batteries and diesel generators for backup power

### Software Errors

* A software bug that cause every instance of an application server 
to crash when given a particular bad input.
  * Consider a leap second on June 30, 2012, that caused many
  application to hand due a bug in the linux kernel
* A runaway process that uses up some shared resource - CPU, 
RAM, Disk, NW
* A service that system depends on that slows down, becomes
unresponsive, or start returning corrupted responses.
* Cascading failures

### Human Errors
* Design system that minimizes the opportunity of an error
* Provide sandbox env to practise and experiment
* Test thoroughly at all levels
* Allow quick recovery 
