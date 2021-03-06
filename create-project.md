# Creating a Pangolin test project
For a new project which does not have existing sanity tests, follow the following instructions:

1. In the project’s solution in Visual Studio, create new *Unit Test* project called *Tests*

2. Create folder Uploadable.Files at the root of project and copy all files that are required in the uploader control, then set “Build Action” to “Embedded Resource” from “Properties”  for each of them.

3. Add latest version of Pangolin nuget

4. Create your first unit test by right clicking on a folder or project, from "Add" submenu click "Unit Test" or "Pangolin Unit Test". If select "Pangolin Unit Test" the following pattern will be created and ready to write your code, otherwise if select "Unit Test" manually add below pattern.

   ```c#
   using Pangolin;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   
   namespace UnitTestProject9
   {
       [TestClass]
       public class TestCaseName : UITest
       {
           [TestMethod]
           public override void RunTest()
           {
               //YOUR CODE
           }
       }
   }
   ```

   

   

5. Add app.config file to your project and add the following key-value pairs.

   ```xaml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <configSections>
       <sectionGroup name="localSettings" type="System.Configuration.AppSettingsSection">
         <section name="localConfigs" type="System.Configuration.AppSettingsSection" />
       </sectionGroup>
       <sectionGroup name="batchRunnerSettings" type="System.Configuration.AppSettingsSection">
         <section name="batchConfigs" type="System.Configuration.AppSettingsSection" />
         <section name="serviceConfigs" type="System.Configuration.AppSettingsSection" />
         <section name="dnsConfigs" type="System.Configuration.AppSettingsSection" />
       </sectionGroup>
     </configSections>
     <appSettings>
     </appSettings>
     <localSettings>
       <localConfigs>
         <add key="AppBaseUrl" value="http://localhost" />
         <add key="PangolinAppId" value="A9D67AB8-C9AF-4C85-A343-599B29DDB63C" />
         <add key="Download.Url" value="c:\download" />
         <add key="Headless" value="false" />
         <add key="EnableSnapshot" value="false" />
         <add key="AppPublishPath" value="APP_DIRECTORY_PATH" />
         <add key="ConnectionStringKey" value="" />
         <add key="DataProviderType" value="" />
       </localConfigs>
     </localSettings>
     <batchRunnerSettings>
       <batchConfigs>
         <add key="PangolinServer" value="http://pangolin.geeksltd.co.uk" />
         <add key="PangolinPublisherPath" value="C:\Projects\Pangolin.Publisher" />
         <add key="WebConfigPath" value="" />
       </batchConfigs>
       <serviceConfigs>
       </serviceConfigs>
       <dnsConfigs>
       </dnsConfigs>
     </batchRunnerSettings>
   </configuration>
   ```

   

   - AppBaseUrl: local URL of web application for running test cases, e.g. "http://localhost" or "http://localhost:8081"
   - AppPublishPath: it's path of published files on local IIS or source code, for instance "C:\Source Code\Website" is where the source code is and it's used for publishing files to cloud servers.
   - PangolinAppId: It should be a GUID that indicates application's id. It's possible to track running test cases on Pangolin Test Explorer VS extension.
   - PangolinServer: URL of server where orchestration app is hosted and store test case in database and is unique per organization. e.g. "http://pangolin.geeksltd.co.uk" is Geeks current server.
   - Download.Url: local path for storing downloaded files of Browser. e.g. "c:\download"
   - Headless: when the Headless is enabled, Unit tests will be run without showing the Chrome browser, to enable this feature and hide chrome while the unit test is running, set it to true
   - PangolinPublisherPath: set local path of publisher app in order to publish source code files from "AppPublishPath" value and test cases to Pangolin server. e.g. "C:\Projects\Pangolin.Publisher"



For existing Sanity projects, app.config added to project automatically and key-value pairs set to default value when converting by Sanity to Pangolin application. 