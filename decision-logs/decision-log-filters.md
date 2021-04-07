# Decision Log Filters

You can filter the information on the decision log screen to more easily focus on different elements of the authorization decision. As you configure a filter \(by clicking the down arrow to access the related options\) and click **Apply**, the table is updated in real-time.

Where you leave the filter option as **Any**, this filter will not be a factor in what is displayed. Similarly, you can clear any filter by again pressing on the down arrow and selecting **Clear**.

Filtering the table can help you focus on and break down the entire process latency of the authorization request. You can use the **CLEAR ALL** button to clear all filters.

![Decision log filters](../.gitbook/assets/filters%20%281%29.png)

### About the Filters

When using the filters, use the down arrow to expand the filter to show some/all of the available options. You can click **Clear** to remove your selection, or **Apply** to see the results of that filter. As you apply additional filters and click **Apply**, the display be updated. You can use the **Clear All** option to remove all filters and show you the full decision logs table.

The filters above the decision logs table include the following:

| Filter name | Filter description |
| :--- | :--- |
| **Timestamp \(UTC\)** | Filter decisions based on the date and time when the decision was made. You can enter a specific **Start** and **End** times to filter for a range of times, or you can use predefined filters \(for example, last minute, 5 minutes, 15 minutes, hour, 24 hours, week, or month\). |
| **Policy** | Filter the display according to which policy the decision was related. The list of currently defined policies will be displayed and you can select one, all or none. |
| **PDP Name** | Filter the results to show decisions that were returned by one or more of the currently defined PDPs. Click in the checkbox of the PDP\(s\) you wish to include in the display. You can select more than one. You can use the search box to find a PDP, for example one that is not currently displayed. |
| **PEP Address** | Filter by the IP address of the PEP \(Policy Enforcement Point\) that will be tasked with enforcing the PDP's decision. |
| **Path** | Filter by policy path that represents the policy and rules that the request was evaluated by. |
| **Duration \(msec\)** | Filter by the total duration time of the decision-making process performed by the PDP. The time is calculated from the request arrival time to the time the PDP sends the decision to the PEP. You can filter all the decisions based on duration by specifying a time range in msec from the minimum value to the maximum value. |
| **Decision ID** | Each decision is given a decision ID. You can use this filter to search for a decision result based on the decision ID. |
|  **Input** |  When filtering the table according to request input, you can use part of a request to find all other requests that contained the same words or code.   Note that the filter is not case-sensitive, and will only return results for complete words. For example, if you enter "all", you will not get any input code that contained the word "allow". Instead, you must search for the full word "allow". |
| **Result** | When filtering the table according to decision result, you can use part of a decision to find all decisions that contained the same words or code.   Note that the filter is not case-sensitive, and will only return results for complete words. For example, if you enter "all", you will not get any input code that contained the word "allow". Instead, you must search for the full word "allow". |

