Description
============
This gem allows one to control a DirecTV STB (receiver).  This works with the current implication of the "External Device" control system.  DirecTV could change or even disable this method at any time without notice.

Requirements
============

+ net/http
+ json
+ External Device set to Allow on DTV Box (Menu -> Settings -> Whole-Home -> External Device - All set to 'Allow')

Install
=======

	gem install dtvcontroller
	
Example Usage
=============
(If timeout, returns "Can't Connect")

Initialize:
-----------

	control = Dtvcontroller.new("192.168.1.100")

Get current channel:
--------------------

Movie Example:

	puts control.get_channel => 529: SEDGHD - The Lost World: Jurassic Park 
	
Show Example:

	puts control.get_channel => 298: CNHD - Family Guy: Peters Tale

Sending a remote key:
---------------------

	a = "ch_up" (see "Command List" for full list of commands)
	control.send_key(a) => nil (If timeout, returns "Can't Connect")

Getting information from systeminfo:
------------------------------------

	a = "accessCardId" (see "Command List" for full list of commands)
	b = control.get_sysinfo(a)
	puts b => 0918-7948-2357 (If timeout, returns "Can't Connect")

Command List
=============
Remote Keys:
------------
+ power
+ poweron
+ poweroff
+ format
+ pause
+ rew
+ replay
+ stop
+ advance
+ ffwd
+ record
+ play
+ guide
+ active
+ list
+ exit
+ back
+ menu
+ info
+ up
+ down
+ left
+ right
+ select
+ red
+ green
+ yellow
+ blue
+ ch_up
+ ch_dn
+ prev
+ 0-9
+ dash (or '-')
+ enter

sysinfo commands:
-----------------
(case sensitive)

+ accessCardId 
+ receiverId
+ stbSoftwareVersion
+ version
