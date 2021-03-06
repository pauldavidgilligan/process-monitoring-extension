# AppDynamics Processes - Monitoring Extension

This extension works only with the standalone machine agent.

##Use Case

The AppDynamics Process extension observes active processes on a Linux or Windows machine and displays them in the AppDynamics Metric Browser.

The Processes extension retrieves the following metrics of each process:

-   CPU utilization in %
-   Memory utilization in MB
-   Memory utilization in %
-   Number of running instances. (If there are, for example, 3 Java processes running, this monitor will report them individually)


##Directory Structure

<table><tbody>
<tr>
<th align="left"> File/Folder </th>
<th align="left"> Description </th>
</tr>
<tr>
<td class='confluenceTd'> conf </td>
<td class='confluenceTd'> Contains the monitor.xml and properties.xml </td>
</tr>
<tr>
<td class='confluenceTd'> lib </td>
<td class='confluenceTd'> Contains third-party project references </td>
</tr>
<tr>
<td class='confluenceTd'> src </td>
<td class='confluenceTd'> Contains source code to the Process Monitoring Extension </td>
</tr>
<tr>
<td class='confluenceTd'> dist </td>
<td class='confluenceTd'> Only obtained when using ant. Run 'ant build' to get binaries. Run 'ant package' to get the distributable .zip file </td>
</tr>
<tr>
<td class='confluenceTd'> build.xml </td>
<td class='confluenceTd'> Ant build script to package the project (required only if changing Java code) </td>
</tr>
</tbody>
</table>

##Installation

1. Run 'ant package' from the process-monitoring-extension directory
2. Download the file ProcessMonitor.zip located in the 'dist' directory into \<machineagent install dir\>/monitors/
3. Unzip the downloaded file
4. In \<machineagent install dir\>/monitors/ProcessMonitor/, open monitor.xml and configure the path to the properties.xml.
5. Optional but recommended. Configure a custom metric path (in monitor.xml).
6. Optional. Open properties.xml and configure the filter values. NOTE: If the memory threshold is not specified in properties.xml, then a default value of 100MB will be used by the extension. This means that any processes below this threshold will not appear in the Metric Browser.
7. Restart the Machine Agent.

In the AppDynamics Metric Browser, look for: Application Infrastructure Performance  | \<Tier\> | Custom Metrics | \<Windows/Linux\> Processes
or your specified path under Application Infrastructure Performance  | \<Tier\> |.

NOTE: If there are multiple processes with the same name (i.e. 3 "java.exe" processes), they will be identified by their PID in the Metric Browser.

###XML files to modify
<ul>
<li>monitor.xml: This is used to execute the Java code which starts the extension. You might need to configure the path to the other xml file (see <a href="http://docs.appdynamics.com/display/ACE/Processes?sortBy=name#Processes-monitor.xml" target="_blank">monitor.xml</a> (requires login)).</li>
<li>properties.xml: This file enables you to filter out which metrics are going to be reported and displayed on the metric browser (see <a href="http://docs.appdynamics.com/display/ACE/Processes?sortBy=name#Processes-properties.xml" target="_blank">properties.xml</a> (requires login)).</li>
</ul>

**Note**: If you are running Windows,  make sure that the file 'csv.xsl' is in 'C:\Windows\System32' for 32bit or 'C:\Windows\SysWOW64' for 64bit OS versions (standard under Windows Server 2003).
If this file is not found, the process monitor will output an error to the log file (logs/machine-agent.log) .


##Custom Dashboard

![](http://appsphere.appdynamics.com/t5/image/serverpage/image-id/95i5C555106398901A2/image-size/original?v=mpbl-1&px=-1)

##Metric Browser

![](http://appsphere.appdynamics.com/t5/image/serverpage/image-id/93iED3BE531B3AE0FFC/image-size/original?v=mpbl-1&px=-1)

![](http://appsphere.appdynamics.com/t5/image/serverpage/image-id/97iCA9AA07958232EAD/image-size/original?v=mpbl-1&px=-1)



##Contributing

Always feel free to fork and contribute any changes directly via [GitHub](https://github.com/Appdynamics/process-monitoring-extension).

##Community

Find out more in the [AppSphere](http://appsphere.appdynamics.com/t5/Extensions/Process-Monitoring-Extension/idi-p/1069) community.

##Support

For any questions or feature request, please contact [AppDynamics Center of Excellence](mailto:ace-request@appdynamics.com).
