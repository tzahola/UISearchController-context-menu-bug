# UISearchController-context-menu-bug
Demonstration project for a bug with iOS's context menus (UIMenuController) when used in conjunction with UISearchController

*Update: seems to be fixed in iOS 13.0 beta*

## Summary

If you try to use long-press context menus (aka `UIMenuController`) on `UITableViewCell`s in conjuction with a `UISearchController`, you'll find that the context menu dismisses itself *the first time* you bring it up. Subsequent attempts to show the context menu will succeed.

Demonstration:

![demonstration](https://github.com/tzahola/UISearchController-context-menu-bug/raw/master/demonstration..gif)

## Steps to reproduce:

1. Clone this project
2. Run the app
3. Long-press one of the table rows and observe how the context menu shows up and immediately disappears. 
4. Long-press again one of the rows and observe the context menu showing up, but now it will correctly stay visible until you dismiss it. 

If you remove the line indicated below, you won't encounter the issue:

```
- (void)viewDidLoad {
    [super viewDidLoad];
    
    _searchController = [[UISearchController alloc] initWithSearchResultsController:nil];
    _searchController.searchResultsUpdater = self;
    self.navigationItem.searchController = _searchController; // <-- if you remove this line, the context menu will work correctly
}
```
