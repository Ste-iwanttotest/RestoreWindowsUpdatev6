# Server configuration
1. Download required files

2. Install Requestly

3. Create a redirect rule:

   When the URL contains https://www.update.microsoft.com/v6/ClientWebService/client.asmx
  
   Redirect to https://fe2.update.microsoft.com/v6/ClientWebService/client.asmx

4. Create a redirect rule:

   When the URL contains https://www.update.microsoft.com/v6/UpdateRegulationService/UpdateRegulation.asmx

   Redirect to https://fe2.update.microsoft.com/v6/UpdateRegulationService/UpdateRegulation.asmx

5. Create a redirect rule:

   When the URL contains https://fe2.update.microsoft.com/v11/3/legacy/windowsupdate/selfupdate/wuident.cab

   Filter: only GET requests

   Redirect to https://web.archive.org/web/20070110011725/http://update.microsoft.com:80/v6/windowsupdate/SelfUpdate/wuident.cab

6. Create a Modify Headers rule:

   When the URL contains /wuident.cab

   Add response headers:

   Content-Length: 7427

   Last-Modified: Fri, 20 Oct 2006 02:00:03 GMT

7. Unzip ProxHTTPSProxy and open config.xml

8. Under the [PROXY ...] section add:

   [PROXY 127.0.0.1:port]

   www.update.microsoft.com

   fe2.update.microsoft.com

   web.archive.org

9. In the [Bypass SSL] section add:

   *.microsoft.com

   *.archive.org
