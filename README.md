# Tomcat Extension for Custom Runtime Loading #

Users can deploy custom run times on tomcat with this extension. 
As an example we can run jaggery application using this extension.

Follow below steps to run jaggery web apps on tomcat.

 1. Open the server.xml file (stored in the &lt;Tomcat_HOME&gt;/conf directory).
 
 2. Add the following under the server tag:
    `<Listener className="org.wso2.appserver.configuration.listeners.ServerConfigurationLoader"/>`
    
 3. Open the context.xml file (stored in the &lt;Tomcat_HOME&gt;/conf directory).
 
 4. Add the following under the Context tag:
    `<Listener className="org.wso2.appserver.configuration.listeners.ContextConfigurationLoader"/>`
    
 5. Add the below lines under the Context tag:
    `<Loader className="org.wso2.appserver.webapp.loader.AppServerWebappLoader"  
    loaderClass="org.wso2.appserver.webapp.loader.AppServerWebappClassLoader"/>  
    <!--for jaggery app deployment-->
     <Listener className="org.jaggeryjs.jaggery.tomcat.listener.JaggeryAppListener" />`
  
 6. Copy &lt;project_root&gt;/modules/custom-run-time-loader/target/custom-runtime-loader-1.0.0-SNAPSHOT-fat.jar 
    to &lt;Tomcat_HOME&gt;/lib folder.
     
 7. Copy &lt;project_root&gt;/modules/custom-run-time-loader/src/main/Resources/jaggery/org.jaggeryjs.jaggery.tomcat.listener-0.13.0.jar to 
    &lt;Tomcat_HOME&gt;/lib folder.
    
 8. Copy &lt;project_root&gt;/modules/custom-run-time-loader/src/main/Resources/runtimes folder to &lt;Tomcat_HOME&gt;/lib folder.
 
 9. Copy &lt;project_root&gt;/modules/custom-run-time-loader/src/main/Resources/wso2 folder to &lt;Tomcat_HOME&gt;/conf folder.
 
 10. Copy &lt;project_root&gt;/samples/jaggerySamples/target/coffeeshop.war to &lt;Tomcat_HOME&gt;/webapps folder.
 
 Now start the server and you should be able to access the application by going to 
 
    http://localhost:8080/coffeeshop