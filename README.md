irma_web_relay
==============

The `irma_web_relay` application allows our IRMA webservice to communicate with virutal card readers (for example `irma_android_cardproxy`). The webbrowser (running the IRMA webservice) and the virtual card-reader communicate via the relay (in fact, the both connect to the relay). This allows them to communicate even when a direction connection is not possible due to firewalls etc.

Building
--------

To build the war for this java web-application simply run

    gradle assemble

you can find the resulting `.war` in `build/libs`.

Running
-------

To run a local instance of the relay, for example in conjunction with the `irma_web_service`, simply call

    gradle appRun

Using tomcat
------------

The relay uses long-polling. To enable this, the tomcat instance needs to use a special connector. In particular, make sure you specify

        <Connector connectionTimeout="20000" port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol" redirectPort="8443"/>

in your instance's server.xml.

If you are using eclipse to run the application, this file is located in `<WORKSPACE>/Servers/Tomcat v6.0 Server at localhost-config/`. Simply find the port 8080 connector line and change it the above. This makes Eclipse unhappy, so go to the Navigator Pane, selects Servers, select the above directory, and hit refresh.
