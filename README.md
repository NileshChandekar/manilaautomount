### Intro

	* We considered multiple approaches for addressing mount automation. 
	* The thinking has come a long way since we originally considered the problem 2+ years ago, but we still don't have a "silver bullet" approach that works in a wide variety of application and has no drawbacks.


### Questions


	* We decided to evaluate the various approaches using the follow measurements:

		* Approach should allow for instantaneous/synchronous mounting?
    	* Approach should allow for persistent mounts that survive across reboots?
    	* Can the approach handle the case when the client is down at the time of attach/detach?
    	* What security considerations exist?
    	* What network considerations exist?
   	 	* Are there any external dependencies?
    	* Does the approach require Manila to store any state?
    	* Does the approach allow Manila to enable use cases that would be impossible without mount automation, such as automatically updating mounts in the event of a DR failover?
    	* How much effort is required to implement the approach?
    	* How resistant are users likely to be to the approach?
    	

	* The hardest thing about this feature, aside from the fact that there are no silver bullet solutions, is that the feature doesn't allow users to do anything that wasn't already possible. 
	* For the most part, this is about simplifying something which can be done already (with the exception of the DR use case, mentioned above).


### Approaches considered:

    * Agent - write a custom agent to solve the problem (also well understood and old idea)
    * Zeroconf-based advertisements
    * AutoFS - leverage autofs to solve the problem on UNIX
    * LDAP/AD - insert mount information into the directory service and let clients pull it from there
    * Cloud-Init - piggyback on cloudinit (a shippable demo is available for this that will be shown at the Liberty summit)
    * VirtFS - virtfs gives us the closest model to cinder, and attaches/detaches make significantly more sense in this context
    

### Pre-requisite 

	* Should good basic knowledge of Openstack and Manila 
	* Good knowledge of Automount
	* Should good knowladge on filesystem 
	* Good Python skill is also good. 

	    
