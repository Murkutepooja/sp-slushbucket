# sp-slushbucket
Portal widget to add slushbuckets to portal catalog item forms.

![alt text](https://github.com/robhumphries5/sp-slushbucket/blob/master/SP%20Slushbucket.png?raw=true "Screenshot")

## The update set includes:
+ a widget SP Slushbucket to be used in any macro/macro with label variables in the Service Portal
+ a variable Slushbucket Demo to demonstrate the widget set up and use

## Implementation instructions:
+ download the update set from the [ServiecNow Community](https://developer.servicenow.com/connect.do#!/share/contents/3638254_service_portal_slushbucket_widget?v=1&t=PRODUCT_DETAILS) or from the [GitHub Repository](https://github.com/robhumphries5/sp-slushbucket)
+ in your instance go to /sys_remote_update_set_list.do
+ use the Import Update Set from XML related link to import the update set
+ preview and commit the update set

If you are only looking to demo the widget you can add the demo variable to any form to see how it works:
+ go to /sc_cat_item_list.do
+ select any active item with an active category in your Service Catalog to add the variable to
+ go to the Variables related list at the bottom of the form
+ click Edit
+ search for Slushbucket Demo and add to the form
+ go to the catalog item in the Service Portal and you will see the field referencing the User table

If you are looking to implement the widget, do not use the variable, create new Macro/Macro with label variables and add the widget to them
+ go to /sc_cat_item_list.do
+ select the item you want to add the variable to
+ go to the Variables related list at the bottom of the form
+ click New
+ Set the type to Macro or Macro with Label
+ Set other mandatory values
+ Under Type Specification set Widget to SP Slushbucket
+ Under Default Value set the Default Value to a JSON as below

```
{

variableName:"whatever you called your variable",

table:"the table to reference",

refQual:"any additional reference qualifier",

sortBy:"the field to sort by",

display:"the display value",

secondaryField:"additional field to show on hover",

fields:an array of field names to include, will not be displayed but can be used to filter

}
```

## Using the value:
The field will not display in the RITM or TASK Variable editor, this will come in a later update
However the value is available at sc_req_item.variables[variableName]
You can get this value in scripts and workflows to be used

