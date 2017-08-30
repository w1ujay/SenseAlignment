# SenseAlignment
Align IP addresses within Sense

The variable per site would be the PS server address.
The json query needs password to PS input.

==========
Read the following file;
C:\Windows\System32\config\systemprofile\AppData\Roaming\VDG Security\SenseVideoManager\settings\devices\001.Device\Device.ini

==========
Retreive the following line from within Device.ini;
CameraName=100-101

==========
Take the first integer before the '-' to run a query against ParkServer, like this;
http://10.153.0.5/v2/bays.json?id=100&select=sensor.extended_properties.ip_address
                                  ^^^Variable
The result is;
     [
{
"sensor": {
"extended_properties": {
"ip_address": "10.153.0.198"
}
}
}
]

==========
Then take the result from the json above and write it back to to Device.ini file on this line and format;
CameraAddress=10.153.0.198

==========

-There can be hundreds of the \###.Device\Device.ini folders per server, and there can be many servers.
CCreek has ~170 streams per server and 10 servers.

-The .ini can be edited live, to commit the IP address if new, A change must be made in the user's view of any layout, then change off of screen so there is a prompt to save.  Nothing has to be changed, the appearance of the message seems to be enough to make the changes.


