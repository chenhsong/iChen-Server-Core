iChen® Server 4.0 Configuration File Reference
==============================================

File Name: `iChenServer.config`  
Location: Same as server executable  
Last Edited: 2019-12-20


Format
------

~~~xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <appSettings>
            :
        <add key="key" value="value" />
            :
    </appSettings>
</configuration>
~~~


System Settings
---------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`IP`|unsigned short integer|none|4.0|For systems with multiple network adaptors, this allows binding the iChen® Server to a particular network adaptor by specifying its IP address.|
|`StandAlone`|`true` or `false`|`true`|4.2|If `true`, the iChen® Server is operating as a single instance. If `false`, the iChen® Server instance is operating as part of a cluster.|
|`DatabaseEnable`|`true` or `false`|`true`|4.2|If `false`, the configuration database is disabled and the iChen® Server operators in an online-only mode.|
|`DatabaseVersion`|unsigned short integer|0|4.0|Version of the configuration database. This is for backward-compatibility purposes.|
|`DatabaseSchema`|string|none|4.0|Schema in the configuration database to use, for database systems that require it (e.g. SQL Server for non-`dbo` schemas).|
|`DataStore`|string|none|4.0|Connection name for the external archive database (if any).|
|`JobModesFile`|string|`./assets/iChenServerJobModes.json`|4.0|Path to a text file containing the text names of the list of job-mnodes from `ID01` to `ID15`.|
|`iChenWeb_ServerLogs_Path`|string|`./logs`|4.0|Path to the directory/folder containing server logs.|


Controller Settings
-------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`RecvAliveCounter`|unsigned integer|20|4.0|Number of seconds to wait to time-out a controller connection when `ALIVE` messages are not received.|
|`Controller_Connection_Timeout`|unsigned float|30.0|4.1|Number of minutes to time-out a controller when no _heartbeat_'s are received. A timed-out controller is assumed to be off-line.|
|`Controller_Mappings_Path`|string|`./assets`|4.2|Path to the directory/folder containing the necessary address/variable mapping tables for different controller types.|
|`Track_CycleData`|`true` or `false`|`false`|4.2|If `true`. a unique ID will be generated for each cycle data record, allowing tracking.|


Controller Serial Number Mappings
---------------------------------

* A configuration file can have more than one controller serial number mapping.

|Key|Value|iChen® Server Version|
|---|:---:|:-------------------:|
|Controller serial number|Regular expression matching a controller address. For TCP/IP connections, it should be the IP address plus port number in the format `xxx.xxx.xxx.xxx:ppp`. For serial port connections, it should be `COM`_x_ (Windows) or `tty`_xxx_ (Linux).|4.0|
|Actual controller serial number|New serial number to use|4.2|


Serial Port Listeners
---------------------

* A configuration file can have more than one serial port listener settings.

|Key|Value|iChen® Server Version|
|---|:---:|:-------------------:|
|Serial port name. Should be `COM`_x_ (Windows) or `tty`_xxx_ (Linux).|Serial port settings in the format _baud_`,`_parity_`,`_bits_`,`_stop_ (e.g. `9600,n,8,1` for 9,600 baud, no parity, 8-bit data, 1 stop bit).|4.0|


iChen® Protocol Settings
------------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`Port`|unsigned integer|34954|4.0|Port number to listen for the iChen® protocol.|
|`DefaultControllerTimeZone`|-12.0 to 12.0|none|4.2|All controllers connected via the iChen® protocol are assumed to be this number of hours offset from the system's time-zone, unless individually specified in the configuration database.|
|`SendAliveCounter`|unsigned integer|10|4.0|Number of seconds to wait to send out each `ALIVE` message to each connected controller.|
|`RestrictMoldsToJobCards`|`true` or `false`|`false`|4.0|If `true`, mold lists provided are restricted to molds allocated under the current job-card. If `false`, all molds are retrieved regardless of the current job-card. This is usually set to `true` when job-card control is used.|
|`AutoLoginLevel`|0-10|none|4.0|When set, a controller will automatically login to a standard user with the specified authorization level when first connected. If missing, a controller will logout of all users when first connected.|


SMP (Simple Message Protocol) Settings
--------------------------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`SMP_Port`|unsigned short integer|none|4.2|Port number to listen for the SMP (Simple Message Protocol), usually 34958. If missing, then SMP is disabled.|


Open Protocol® Settings
-----------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`Terminal_Ws_Port`|unsigned short integer|5788|4.0|Port number of the Open Protocol® WebSocket server.|


Web/REST Server Settings
------------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`iChenWeb_Enable`|`true` or `false`|`true`|4.2|If `false`, the web server is disabled.|
|`iChenWeb_Port`|unsigned short integer|5757|4.0|Port number of the web server.|
|`iChenWeb_WWW`|string|`./www`|4.0|Path to the root of the web server contents.|
|`iChenWeb_TerminalConfigFile`|string|`./terminal/config/default.js`|4.0|Path, relative to that of `iChenWeb_WWW`, to the terminal configuration file.|
|`iChenWeb_Timeout`|unsigned float|15.0|4.0|Number of minutes to time-out a web server login when idle.|
|`Https_Certificate_File`|string|none|4.0|HTTPS certificate file.|
|`Https_Certificate_Hash`|string|none|4.0|HTTPS security hash.|


Azure Table Storage Settings
----------------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`CloudStore_Account`|string|none|4.0|Azure Table Storage account name.|
|`CloudStore_Key`|string|none|4.0|Azure Table Storage access key.|
|`CloudStore_Signature`|string|none|4.0|Azure Table Storage SAS token, if no access key is provided.|
|`CloudStore_UseHttps"`|`true` or `false`|`true`|4.0|Use HTTPS instead of HTTP to access Azure Table Storage.|
|`CloudStore_CycleData_BatchSize"`|unsigned short integer|same as `CloudStore_BatchSize`|4.2|Upload cycle data records to Azure Table Storage in this batch size. Set this to 1 if cycle data records need to be available immediately.|
|`CloudStore_BatchSize"`|unsigned short integer|5|4.2|Upload other records to Azure Table Storage in this batch size.|


Shared Cache Settings
---------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`KeepSettings`|`true` or `false`|`true`|4.0|If `true`, mold data settings are kept as part of the shared cache information. This is usually set to `false` for cloud-based shared caches to reduce per-device storage usage.|
|`KeepCycleData`|`true` or `false`|`true`|4.2|If `true`, the last set of cycle data values are kept as part of the shared cache information. This is usually set to `false` for cloud-based shared caches to reduce per-device storage usage.|
|`CloudCache_Connection`|string|none|4.0|Connection string to a cloud Redis cache for use as a shared cache.|


Azure IOT Hub Settings
----------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`Broadcast_Messages`|`true` or `false`|`false`|4.1|Broadcast Open Protocol® messages to the Azure IOT Hub.|
|`Broadcast_Interval`|unsigned integer|0|4.2|Number of milliseconds to wait after broadcast each Open Protocol® message to the Azure IOT Hub. This is to avoid hitting throttle limits.|
|`IoTHub_Server_Connection`|string|none|4.1|Connection string to an Azure IOT Hub with `server` authorization.|
|`IoTHub_Device_Connection`|string|none|4.1|If `IoTHub_Server_Connection` is not set, connection string to a device twin on an Azure IOT Hub shared cache. The marker `{0}` will be replaced by the controller's serial number.|


Azure Event Hub Settings
------------------------

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`EventHub_Connection`|string|none|4.1|Connection string to an Azure Event Hub to read broadcast Open Protocol® messages.|
|`EventHub_Group`|string|none|4.1|Consumer group of the Azure Event Hub reader.|
|`EventHub_Storage_Connection`|string|none|4.1|Connection string to an Azure Blob Storage for use with the Event Hub Processor.|
|`EventHub_Storage_Container`|string|none|4.1|Name of the container in an Azure Blob Storage for use with the Event Hub Processor.|


OPC UA Settings
---------------

* Note: OPC UA is a charged feature.

|Key|Value|Default if missing|iChen® Server Version|Description|
|---|:---:|:----------------:|:-------------------:|-----------|
|`OpcUa_Key`|string|none|4.0|Authorization key for the OPC UA feature.|
|`OpcUa_Tcp_Port`|unsigned short integer|5789|4.0|Port number for the TCP/IP protocol.|
|`OpcUa_Http_Port`|unsigned short integer|5789|4.0|Port number for the HTTP protocol.|
|`OpcUa_Https_Port`|unsigned short integer|5789|4.0|Port number for the HTTPS protocol.|
