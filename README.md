fuse-jaxrs
==========

1) mvn clean install
2) startup Fuse 6.1
3) run the following commands in Fuse:

----
config:edit org.apache.cxf.osgi
config:propset org.apache.cxf.servlet.hide-service-list-page true
config:propset org.apache.cxf.servlet.context /rest
config:propset org.apache.cxf.servlet.service-list-path /_svcs
config:update
features:addurl mvn:org.overlord.test/fuse-jaxrs-dist/1.0.0-SNAPSHOT/xml/features ; features:install -v fuse-jaxrs
----

4) open a browser
5) Try navigating to the following two URLs:

http://localhost:8181/cxf/fuse-jaxrs-hello/hello/apis       <== will work!
http://localhost:8181/cxf/fuse-jaxrs-hello/hello/services   <== will NOT work (list of deployed services shown instead of my endpoint return value)

6) Restart Fuse
7) Try navigating to the following two URLs:

http://localhost:8181/rest/fuse-jaxrs-hello/hello/apis       <== will work!
http://localhost:8181/rest/fuse-jaxrs-hello/hello/services   <== will STILL NOT work (list of deployed services shown instead of my endpoint return value)
http://localhost:8181/rest/go/to/hell/and/die/services       <== will show the list of services
