wfastcgi.py provides a gateway between IIS's FastCGI support to Python's WSGI protocol.  It can be downloaded from our downloads section.

# Installing & Configuring

1. Download and install wfastcgi, it will install into C:\Python27\Scripts (or wherever your Python interpreter is installed).

2. Make sure IIS has FastCGI installed:
    
    ``
    start /wait %windir%\System32\\PkgMgr.exe /iu:IIS-CGI
    ``

3. Register the handler with IIS:

    ``
    %windir%\system32\inetsrv\appcmd set config /section:system.webServer/fastCGI "/+[fullPath='c:\Python27\python.exe', arguments='C:\Python27\Scripts\wfastcgi.py']"
    ``

# Using in an application

You can now use the handler in a web.config file, here's an example configured for a Django project:


    <appSettings>
        <add key="WSGI_HANDLER" value="DjangoProject.wsgi.application" />
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoProject.settings" />   
    </appSettings>
    <system.webServer>
        <handlers>
            <add name="Python_FastCGI"
                path="handler.fcgi"
                verb="*"
                modules="FastCgiModule"
                scriptProcessor="C:\Python27\python.exe|C:\Python27\Scripts\wfastcgi.py"
                resourceType="Either"
                requireAccess="Script" />
        </handlers>
        <rewrite>
            <rules>
                <rule name="Django Application" stopProcessing="true">
                    <match url="(.*)" ignoreCase="false" />
                    <action type="Rewrite" url="handler.fcgi/{R:1}" appendQueryString="true" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>

You can tweak the URL rewriting to include or exclude certain paths for serving static files or other requests from the same server.

# Options
Options are specified with an appSetting in your top-level web.config file as WSGI_HANDLER is shown in the example above.  

<table>
<tbody>
<tr>
<th>Option Name </th>
<th>Description </th>
</tr>
<tr>
<td>WSGI_HANDLER </td>
<td>Specifies the fully qualified handle name, such as &quot;mymodule.handler&quot; or &quot;mymodule.package.handler&quot;. The module name will be imported and the specified handler name will be accessed. If the handler name ends in &quot;()&quot; the handler
 will be called with no arguments. If the handler cannot be fetched or is None wfastcgi will exit and log the error if WSGI_LOG is set.
</td>
</tr>
<tr>
<td>WSGI_RESTART_FILE_REGEX </td>
<td>Specifies the regex for the filenames which if modified will cause wfastcgi to exit and be restarted. Defaults to &quot;.*((\.py)|(\.config))$&quot;.
</td>
</tr>
<tr>
<td>WSGI_LOG </td>
<td>Specifies the path to a log file of errors and important messages. </td>
</tr>
</tbody>
</table>