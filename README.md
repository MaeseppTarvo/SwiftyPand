# SwiftyPand
Easy expandable tableview cell

#Usage
*Create tableview with custom cell

*Insert 2 views into cell

*Set the Priority of the height constraint of second view to 999

*For the top view set all "Constants" to 0

*Inside your custom tableView cell class make constraint variable of the height constraint

```@IBOutlet weak var expandedHeightConstraint: NSLayoutConstraint!```

    var showDetails = false{
        didSet{
            expandedHeightConstraint.priority = showDetails ? 250 : 999
        }
    }
*Inside your tableview class add heightForRowAtIndexPath function and make variable ```var selectedIndex = -1```
  ```
  override func tableView(tableView: UITableView, heightForRowAtIndexPath indexPath: NSIndexPath) -> CGFloat {
    if(selectedIndex == indexPath.row){
      return 210
    }else{
      return 135
    }
  }
  ```
    
*Inside cellForRowAtIndexPath make it to expand
```
if (self.selectedIndex == indexPath.row){
                self.selectedIndex = -1
            }else{
                self.selectedIndex  = indexPath.row
            }
            
            self.productstable.beginUpdates()
            self.productstable.reloadRowsAtIndexPaths([indexPath], withRowAnimation: UITableViewRowAnimation.Automatic)
            self.productstable.endUpdates()
        }
```

Images for easier understanding about constraints

![alt tag](https://github.com/MaeseppTarvo/SwiftyPand/blob/master/Screen%20Shot%202016-08-23%20at%2014.26.47.png?raw=true)

![alt tag](https://github.com/MaeseppTarvo/SwiftyPand/blob/master/Screen%20Shot%202016-08-23%20at%2014.30.48.png?raw=true)

