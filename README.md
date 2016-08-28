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

######26 Handling errors
propagate:
```
enum CusError: ErrorType{
  case Empty
  case TooShort(Int)
}
func manName(name: String) throws -> String{
  guard name.characters.count>0 else{throw CusError.Empty}
  guard name.character.count >2 else{
    throw CusError.TooShort(name.characters.count)}
  return String(name.characters.reverse())
  }
}
```
impl trycatch:
```
do{
  try manName("")
}catch CusError.Empty{
}catch CusError.TooSHort(let count){
}
```
using try?
```
let f = try? manName("")
```

handlers:
```
NSSetUncaughtExceptionHandler
Signal handler  (needs Objective-c bridge)
```
######34 General breakpoints
set bp: use  
cmd+ \


05:41  
rightclick a breakpoint ( in bp view) , move breakpoint to

######36 Conditional
snippets
```
func seedDatabase(){
  let bundle = NSBundle.mainBundle()
  let path = bundle.pathForResource("ke",ofType:"json")
  let data = NSData(contentOfFile:path!)
  let dateFor:NSDateFormatter =NSDateFormatter()
  dateFor.dateFormat = "yyyy-MM-dd'T'HH:mm:ssZ"
  do{
    let json = try NSJSONSerialization.JSONObjectWithData(data!, optionsL .AlliwFragments)
    if let items = json["items"] as ?[[String:AnyObject]]{
      for item in items{
        let ev: Event = NSEntityDescription.insertNewObjectForEntityForName("Event",inManagedObjectContext:managedObjectContext) as! Event
        ev.item = item["item"] as? String ==nil?"" :item["item"] as? String
        ev.timestamp = dataFor.dateFromString((item["timestamp"] as? String)!)==nil?NSDate():dataFor.dateFromString((item["timestamp"] as? String)!)
        
      }
    }
    try managedObjectContext.save()
}catch{

}
}
```
store code data store file
```
lazy var applicationDocumentDirectory:URL ={
  let urls = NSFileManager.defaultManager().URLsForDirectory(.DocumentDirectory, inDomains: .UserDomainMask)
  return urls[urls.count-1]
}()
```

managedobjectmodel
```
lazy var managedObjectModel:URL ={
  let modeURL = NSBundle.mainBundle().URLForResource("ke",withExtension:"")!
  return NSManagedObjectModel(contentsOfURL:modelURL)
}()
```
04:40  
debug fails, delete sqlite files in /CoreSimulator/Devices/uuid/data/Containers/Data/uuid/Documents.
use [simpholders](simpholders.com)

find -iname  # insensitive  
delete sqlite file
```
#! /bin/sh
find /Users/ke/Library/Developers/CoreSimulator/Devides/uuid/data/Containers/Data/Application -iname "App.sqlite" -exec rm -rf {}\;
```
