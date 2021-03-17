# Decision Log Filters



You can filter the information on the decision log screen to more easily focus on different elements of the authorization decision. As you configure a filter \(by clicking the down arrow to access the related options\) and click **Apply**, the table is updated in real-time.

Where you leave the filter option as **Any**, this filter will not be a factor in what is displayed. Similarly, you can clear any filter by again pressing on the down arrow and selecting **Clear**.

Filtering the table can help you focus on and break down the entire process latency of the authorization request. You can use the **CLEAR ALL** button to clear all filters.

![Decision log filters](https://files.readme.io/294a7e6-filters-dl.PNG)

### Toolbar

Just above the decision logs table, on the right side, is the decision log toolbar. This contain:

* A **Refresh** option to ensure you have the most up-to-date information
* The **Show/Hide** filter toggle will show or hide the filter options bar above the table.

![](https://files.readme.io/e49581f-decisionlog-toolbar.PNG)

When you apply one or more filters to the decision logs table, the Show/Hide icon will display the number of filters currently set. As you clear the filters, the displayed number will automatically adjust to the current number of defined filters.

### Filters

The filters above the decision logs table includes the following:

| Filter name | Filter description |
| :--- | :--- |
| **Decision** | When filtering the table according to Decision, you can center part of the decision to find all decisions that contained those words. Note that the filter is not case-sensitive, but will only return results for complete words. For example, search for all results that contain - allow: true |
| _**Decision**_ ID | Using the Decision ID filter, you can easily locate the decision associated to that decision ID. Note that the decision ID is only visible once you click the &gt; arrow next to a decision. |
| **Timestamp \(UTC\)** | Filter decisions based on the date and time when the decision was made. You can enter a specific **Start** and **End** time, or you can use predefined filters \(for example, last-minute, 5 minutes, last hour, last week, last month, etc.\). |
| **Policy** | Filter the display according to which policy the decision was related. The list of currently defined policies will be displayed and you can select one, all or none. |
| **PEP \(Policy Enforcement Point\) Address** | Filter by the IP address of the PEP that will be tasked with enforcing the PDP's decision. |
| **Path** | Filter by policy path that represents the policy and rules that the request was evaluated by. |
| **Duration** | Filter by the total duration time of the decision-making process performed by the PDP. The time is calculated from the request arrival time to the time the PDP sends the decision to the PEP.  You can filter all the decisions based on duration by specifying a time range in msec from the minimum value to the maximum value. |

