# Decision Logs

The decision logs table enables you to view all decisions made by the PDPs managed in the project. By viewing what the authorization decision was, you can analyze how effectively your authorization policy is being implemented and determine whether or not it is necessary to "tweak" the policy.

To help you find a specific decision or group of decisions, it is possible to filter the data displayed in the table by using several built-in build.security [filters](decision-log-filters.md).

![Decision logs table](https://files.readme.io/28a73e0-decisionlog2.PNG)

### Decision Log Columns

Each line of the table includes the following information for each authorization request/response that was sent to and received from the PDPs:

| Filter name | Filter description |
| :--- | :--- |
| Decision | Displays the syntax of the decision that was made by the PDP. You can hover over a value in the Decision column to display the full decision syntax.  You can click the **&gt;** arrow to expand each decision to view greater details about the decision. These details include: - Decision ID - Metrics \(and duration\) - Input - Result For more information on the expanded decision view, see [Decision Details](https://docs.build.security/docs/decision-log-filters2) |
| Timestamp \(UTC\) | The Timestamp \(UTC\) column displays the timestamp assigned to this decision. Format is MM/DD/YYYY, H:MM:SS AM \(or PM\). |
| Policy | Lists which policy was used in the decision process. |
| PDP Name | The name of the PDP, as it exists in the control plane, responsible for determining the authorization decision. |
| Policy Enforcement Point | The PEP IP address to which the PDP's decision was sent for enforcement. |
| Path | The path used to send the policy against which the authorization request is evaluated. |
| Duration | The duration of the decision process as calculated from the request arrival time to the time that the PDP sends the decision result to the PEP \(in msec\). |

