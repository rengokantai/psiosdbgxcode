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
Extensions/UITableViewCellExt.swift
```
import Foundataion
import UIKit

extension UITableViewCell{
  func debugQuickLookObject()->AnyObject{
    return textLabel!.text!
  }
}
```
######10 The view debugger
2:28
select a view, right click: Focus on UIView

######16 Tabs and behavior
00:51
cmd+t  enable tab
03:20  
preferences->behaviors->ruuning section->starts->show tab named (debug) in active window
######17 code commenting
MARK mark a section of methods  
format  
```
// MARK: - abc
```
FIXME 
```
// FIXME: 
```
TODO  

Editor->Add build phase->Add run script

######22 NSException vs NSError
NSException: Can not be caught by swift  
NSError: Can be caught by swift
######23 Predefined Exception types
NSRangeException  
NSInvlidArgumentException  
NSInternalInconsistencyException  
NSObjectInaccessibleException //trying to access another object on a diff thread without permission


######24 signals
SIGABRT (EXE_CRASH)  
Abnormal termination  
SIGSEGV (EXC_BAD_ACCESS)  
Invalid emeory access. Address exists but you do not have access  
SIGBUS (EXC_BAD_ACCESS)  
Addess does not exist or access method is invalid  
SIGFPE (EXC_ARITHMETIC)  
Floating point exception  
SIGILL (EXC_BAD_INSTRUCTION)
Invalid Instruction.  
SIGINT - interactive attention  
SIGTERM - termination
