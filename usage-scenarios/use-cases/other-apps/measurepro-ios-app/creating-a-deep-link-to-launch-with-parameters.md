# Creating a Deep Link to Launch with Parameters

To launch the Measure pro application from sources like websites or salesforce mobile we can call the following URL schema to automatically open the app if it's installed or to launch the App Store to enable the user to download the app

```
rdscan://home
```

\
Any parameters you pass into the link follow standard URL parameter schema starting with a? Following with the property name equals, and then the value we can utilize this to preselect the flow that the user is going to launch and pass any relevant information along to the flow that is needed to ensure contextual information is passed along for the end user without them having to know it.

```
'rdscan://home?recordId=' & {!FinalQuoteId} & '&flow_name=Opportunity_Post_Measurement'
```



{% hint style="info" %}
The property flow\_name is reserved and that is to be the API name of the flow you want to pre-select, all other properties would simply be passed to the flow that we are launching note that if you do pass a parameter in this URL schema that doesn't exist on the flow as an input parameter, the flow will fail to launch
{% endhint %}



### Creating a clickable link from within a Salesforce flow to launch the app&#x20;

We need to start by creating a formula within a lightning flow that returns a text type from there we utilize our schema of rdscan://home and then can depend to any values needed in order to pass those along to the mobile app

<figure><img src="../../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>



From here, you can create a screen and use an output or display text and insert a hyperlink with the link value being a look up to that formula. In this case, that value will be {!RenderDrawScanURL}.&#x20;

<figure><img src="../../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

The user is presented with a URL that's clickable and will launch the app on mobile.



