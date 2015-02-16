Description
===========
This gem allows one to control a DirecTV Set Top Box (STB or receiver).  This works with the current implication of the "External Device" control system.  DirecTV could change or even disable this method at any time without notice.

# Requirements

+ net/http
+ json
+ External Device set to Allow on DTV Box (Menu -> Settings -> Whole-Home -> External Device - All set to 'Allow')

# Install

Use rubygems to install the dtvcontroller gem:

```
$ gem install dtvcontroller
```
	
# Example Usage

#### Initialize:

```
irb(main):001:0> require "dtvcontroller"
=> true
irb(main):002:0> controller = Dtvcontroller.new("192.168.1.100")
=> #<Dtvcontroller:0x000000028ab450 @ip="192.168.1.100">
```

#### Get current channel:

Movie Example:

```
irb(main):003:0> control.get_channel
=> "529: SEDGHD - The Lost World: Jurassic Park"
```

Show Example:

```
irb(main):004:0> control.get_channel
=> "298: CNHD - Family Guy: Peters Tale"
```

#### Sending a remote key:

```
irb(main):005:0> a = "chanup" # <~ (see "Remote Keys" below for full list)
=> "chanup"
irb(main):006:0> controller.send_key(a)
=> {:msg=>"OK."}
```

#### Remote Keys:

+ `:power`
+ `:poweron`
+ `:poweroff`
+ `:format`
+ `:pause`
+ `:rew`
+ `:replay`
+ `:stop`
+ `:advance`
+ `:ffwd`
+ `:record`
+ `:play`
+ `:guide`
+ `:active`
+ `:list`
+ `:exit`
+ `:back`
+ `:menu`
+ `:info`
+ `:up`
+ `:down`
+ `:left`
+ `:right`
+ `:select`
+ `:red`
+ `:green`
+ `:yellow`
+ `:blue`
+ `:chanup`
+ `:chandown`
+ `:prev`
+ `:0-9`
+ `:dash`
+ `:enter`

#### Getting information from sysinfo:

```
irb(main):007:0> a = "accessCardId" # <~ (see "Sysinfo Commands" below for full list)
=> "accessCardId"
irb(main):007:0> controller.get_sysinfo(a)
=> "0123-4567-8901"
```

#### Sysinfo Commands:

+ `:access_card_id # <~ equivalent to "accessCardId"`
+ `:receiver_id # <~ equivalent to "receiverId"`
+ `:stb_software_version # <~ equivalent to "stbSoftwareVersion"`
+ `:version # <~ equivalent to "version"`
