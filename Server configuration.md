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

6.
