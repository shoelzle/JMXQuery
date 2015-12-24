Java class to provide command line access to JMX.

Usage: jmxquery [-url] [-proc] [-username] [-password] [-metrics] [-list] [-incjvm] [-json] [-help]

options are:

-help 
	Prints this page
	
-url 
	JMX URL, for example: "service:jmx:rmi:///jndi/rmi://localhost:1616/jmxrmi"

-proc
        (*) Local JVM Process name to connect to via JMX, for example: "org.netbean.Main"
	
-username
	jmx username
	
-password 
	jmx password

-metrics
        List of metrics to fetch in following format: {metric}={mBeanName}/{attribute}/{attributeKey};
        For example: "jvm.memory.heap.used=java.lang:type=Memory/HeapMemoryUsage/used"
        {attributeKey} is optional and only used for Composite metric types. Use semi-colon to
        separate metrics.
    
-list [listType] [query]
        Will list out the following depending on listType given:

            jvms: (*) Will list all local JVMs with their JMX connection URLs or null if none
            mbeans: Will show full JMX tree with all mbeans and their attributes
                    This option requires the [query] parameter to filter. Use *:* to list everything

- incjvm
        Will add all standard JVM metrics to the -metrics query if used under java.lang domain
        Useful utility function to add JVM metrics quickly and also for testing connections if
        used by itself

-json
        Will output everything in JSON format, otherwise will be human readable text. Useful
        for passing output to scripts.

(*) NOTE: These methods require JDK 1.6 or above installed and for the Jar to be run via the JDK
    so that it can use the tools.jar libraries for listing local JVMs
