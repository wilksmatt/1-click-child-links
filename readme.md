## Create Child Tasks ##

Azure DevOps offers team-specific work item templating as <a href="https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/work-item-template?view=azure-devops&tabs=browser" target="_blank">core functionality</a> with which you can quickly apply pre-populated values for your team's commonly used fields per work item type. **Create Child Tasks** is an *extension* to Azure DevOps, which allows you to create multiple Task work items as children with a single click. Each Task work item is based on a single pre-defined Task template.

The child Task work items created by this extension are based on the hierarchy of work item types defined in the process template (<a href="https://docs.microsoft.com/en-us/azure/devops/boards/work-items/guidance/agile-process-workflow?view=azure-devops" target="_blank">Agile</a>, <a href="https://docs.microsoft.com/en-us/azure/devops/boards/work-items/guidance/scrum-process-workflow?view=azure-devops" target="_blank">Scrum</a>, <a href="https://docs.microsoft.com/en-us/azure/devops/boards/work-items/guidance/cmmi-process-workflow?view=azure-devops" target="_blank">CMMI</a>). For example, if you're using a process inherited from the agile template with a custom requirement-level type called defect and 3 Task templates defined, using this extension on a User Story or Defect work item will generate three child Tasks; one for each defined template.

## How-To Guide ##

### Defining Task Templates ###

Azure DevOps offers team-specific work item templating as core functionality with which you can quickly apply pre-populated values for your team's commonly used fields per work item type. View Microsoft's documentation about <a href="https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/work-item-template" target="_blank">how to add and update work item templates</a>.

<img src="src/img/screen01.png" alt="Define team templates" />

## Creating Task Template Filter Rules ##

With this extension, it's possible to limit which parent work items apply to each Task template in one of two ways:

### Simplified ###

Put the list of applicable parent work item types in the child Task template's description field, like this:

```[Product Backlog Item,Defect]```

### Complex ###

Put a minified (single line) JSON string into the child Task template's description field, like this:

``` json
{
    "applywhen": [
    {
        "System.State": "Approved",
        "System.Tags" : ["Blah", "ClickMe"],
        "System.WorkItemType": "Product Backlog Item",
        "System.AreaPath": "Root\\Sub Path"
    },
    {
        "System.BoardColumn": "Testing",
        "System.BoardLane": "Off radar",
        "System.State": "Custom State",
        "System.Title": "Repeatable item",
        "System.WorkItemType": "Custom Type"
    }]
}
```

### Applying Child Tasks ###

Find and select the *Create Child Tasks* option on the toolbar menu of the parent work item (E.g. Product Backlog Item, User Story, Bug).

<img src="src/img/screen02.png" alt="1-Click Child-Links on work item form menu"/>

You should now have children associated with the open work item.

<img src="src/img/screen03.png" alt="Done"/>

## Credits ##

Clone from https://github.com/figueiredorui/1-click-child-links
