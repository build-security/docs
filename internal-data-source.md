# Using Internal Data Source

This is a short example of how to add build an internal data source as one of your PDP data sources.

### Before you begin: Install a PDP using the build.security control plane

See instructions here: [Creating a New PDP Configuration](policy-decision-points-pdp/creating-a-new-pdp-configuration.md)  
Make sure to run the PDP on the same host that is running the plugged Docker Engine.

### Step \#1 - Defining your data source

1. Click the **NEW DATA SOURCE** button on the Data Source screen. The New Data Source panel will open on the right.
2. Fill the form

Initially, the file is created with a default structure that will help you create the most common use case for this feature. You can build the JSON file as needed. Initially, the file reflects a default structure according to most common use case for this feature. Specifically, the roles-permissions matrix.

1. Click **SAVE** to create the new internal data source.

The new internal data source will now appear in the list of existing data sources on the data source screen.

![](https://files.readme.io/b69c821-BuildDs.png)

### Step \#3 - Add new rule to your PDP

1. Create or use an already existed policy
2. In your policy screen, create a rule that uses the your new data source. In order to access the data from your build internal data source your query should start with `data.datasources[]`. Then you can manipulate the data as you wish using the Rego language .

```scala
buildData := data.datasources["My internal data source"]
```

![](https://files.readme.io/d1a515d-BuildDsQuery.png)

### Step \#4 - Publish your PDP

Press on the "publish" button and wait for your policy to be published to the control plane.

### Step \#5 - Test your policy

**Congratulations ! your setup has been completed!**  
You will now notice that there is a new response from the PDP containing your DS data.

**So what's next ?**  
You can edit your Rego code in order to enforce your policy using the new data source you had just configured.

