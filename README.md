#### psiosdbgxcode
######4 History
GDB: End Xcode 4.1  
LLDB: current (Low level debugger)

######6 Getting familiar
shift cmd O -> open quickly
######8 The Debug area
4:40  
second to last button  
toggle: View UI hierarchy, View process by Queue, View process by thread  

5:30  
create gpx file  
[here](http://gpx-poi.com)  
9:00
three bottons in bottom left side bar:  
show frames only has symbols  (on recommended)
show threads with debug symbols(default off)  

12:10  
po command in console
```
po cell.textLabel!.text
```

14:00 icon meaning  
L - local var A- argu S- static var R-registers E-Expression V-instance var and global var  

16:30  change summary type
```
type summary add UITableViewCell -s "${var%@}"
```

17:50
down bottom eye icon: quick look  

18:36 extend UITableViewCell,custimize quicklook message
UITableViewCellExt.swift
```
import Foundataion
import UIKit

extension UITableViewCell{
  func debugQuickLookObject()->AnyObject{
    return textLabel!.text!
  }
}
```
