# Doc for the Lightning Components Inspector Chrome plugin

The Lightning Components Inspector allows you to view and navigate the component tree for a component, inspect attributes of components, and investigate the component performance. 

# Installation
TODO: ask Skip where to point people for installation. Available on Chrome Web Store?

# Usage

1. Navigate to a Lightning app. For this doc, we're using the doc reference app at /auradocs/reference.app
2. Launch the Chrome Dev Tools (More tools > Developer tools).

You should see a Lightning tab in the dev tools.

There are a number of of sub tabs available to inspect different aspects of your app.

TODO: brief one-liner explanation for each tab or link to each section below
- Component Tree
- Performance
- Transactions
- Event Log
- Actions
- Storage
- ADS
- Definitions TODO - move this one up in the list and add details
- RLB

## Component Tree Tab
This tab shows the component markup including the tree of nested components.

![Component Tree Tab](componentTree.png)

### Collapse or Expand Markup
You can expand or collapse the markup by clicking on the triangles at the start of each line. By default, the tree shows four levels of nested markup.

![Component Tree Tab](componentTreeExpand.png)

### Refresh the Data
The component tree is expensive to serialize, and doesn't respond to component updates. You need to manually update the tree when necessary by scrolling to the top of the panel and clicking the *Refresh* button.

![Component Tree Tab](componentTreeRefresh.png)

### See More Details for a Node
Double click a node to bring up a sidebar with more details for that selected node.

![Component Tree Tab](componentTreeDetails.png)

The sidebar contains the following information:

- *HTML Elements*  The count of HTML elements for the component (including children components).
- *body* The body of your overall component is complex, but this shows you the body of your component, and the bodies of all the components you extended. The resulting body is the composition of those bodies.
- *Supers* Shows you all the super components and their value providers. A component shares its attributes among all its supers so each level doesn't have its own set of attributes. There is just one attribute value at the concrete level, but each level of extension has its own body.

### Get a Reference to a Component in the Console

Double clicking on a component in the Component Tree or details sidebar generates a reference to that component in the console in the variable $auraTemp.

## Performance Tab

This tab shows a flame graph of the creation time for your Lightning components. Longer and deeper portions of the graph are where you should look for potential performance bottlenecks.

![Performance Tab](performanceGraph.png)

### Record Performance Data
Press the Record button to gather performance data. 

TODO: click around while gathering data?

Press the Record button again to stop gathering performance data.

TODO: does the flame graph show now.

TODO: what does Collect Marks do? Does it show the flame graph while you continue to record?

### See More Performance Details for a Component
Hover over a component in the flame graph to see more detailed information about that component in the bottom-left corner.

TODO: i couldn't get this hover functionality to work

TODO: image

### Narrow the Timeline
Drag on the timeline to select a period of time to focus on.

## Transactions Tab
Some apps delivered by Salesforce include transaction markers that enable you to see fine-grained metrics for actions within those transactions. You can't create your own transactions at this time.

The list of transactions includes counts of actions and XHRs (server-side requests) executed while the transaction was open. The list includes actions/XHRs fired by other events or handlers while the transaction was open. An XHR can include a batch of more than one server-side actions. 

TODO: I presume "transactions" are related to the MetricsService? MetricsService isn't officially exposed to customers so we should explain what we mean by transaction but shouldn't explicitly mention the MetricsService. I think this tab will only be useful for one.app as customers can't create their own transaction right now.

![Transactions Tab](transactions.png)

### See More Transaction Details
Click the ID of a transaction to see more data in the Console.

![Transaction Details](transactionDetails.png)

## Event Log Tab

This tab shows all the events fired. 

TODO: need more details on how to populate the panel. I couldn't see any data using Record.

TODO: add image

### Filtering the List of Events
By default, both application and component events are shown. You can hide or show both types of events by toggling the <em>App Events</em> and <Comp Events</em> buttons.

Enter a search string in the <em>Filter</em> field to match any substring.

Invert the filter by starting the search string with <code>!</code>. For example, <em>!aura</em> returns all events that are not in the <code>aura</code> namespace.

### Show Unhandled Events
Show events that are fired but are not handled. Unhandled events aren't listed by default but can be useful to see during development. 

### View Graph of Events
Expand an event to see more details. Click the <em>Toggle Grid</em> button to generate a network graph showing the events fired before and after this event, as well as the components handling those events.

The graph is color coded.

+ <em>Black</em>: the current event
+ <em>Maroon</em>: the controller action
+ <em>Blue</em>: the event fired

## Actions Tab

This tab shows the server-side actions executed. Actions are recorded by default and the list automatically refreshes when the page refreshes.

TODO: add image

### Filtering the List of Actions
Toggle the buttons related to the different action states to filter the list.

TODO: Storable is internal only as customers can set storable.

Enter a search string in the <em>Filter</em> field to match any substring.

Invert the filter by starting the search string with <code>!</code>. For example, <em>!serviceComponent://</em> returns all actions that are not related to service components.

## Storage Tab

TODO: The storage service is an open source feature and not available for Lightning components. Should this tab be exposed? If so, what should we say about "actions" and "ComponentDefRegistry"?

## ADS Tab

TODO: is this relevant for Lightning components? If so, what should we say about it?

## RLB Tab

TODO: I see the message:  "Error": "No force:recordLayoutBroker components yet created". What is force:recordLayoutBroker and what do users need to know about it?


