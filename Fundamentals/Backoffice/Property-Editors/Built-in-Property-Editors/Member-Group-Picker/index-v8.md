---
versionFrom: 8.0.0
---

# Member Group Picker

`Alias: Umbraco.MemberGroupPicker`

`Returns: string`

The Member Group Picker opens a panel to pick one or more member groups from the Member section. The value saved is of type string (comma separated IDs).

## Data Type Definition Example

![Member Group Picker Type Definition](images/Member-Picker-DataType.png)

## Content Example

![Member Grouep Picker Content](images/Member-Group-Picker-Content.png)

## MVC View Example

### Without Modelsbuilder

```csharp
@if (Model.HasValue("memberGroup"))
{
    var memberGroup = Model.Value<string>("memberGroup"); 
    <p>@memberGroup</p>
}
```

### With Modelsbuilder

```csharp
@if (!string.IsNullOrEmpty(Model.MemberGroup))
{
    <p>@Model.MemberGroup</p>
}
```

## Add values programmatically

See the example below to see how a value can be added or changed programmatically. To update a value of a property editor you need the [Content Service](../../../../../Reference/Management/Services/ContentService/index.md).

```csharp
@{
    // Get access to ContentService
    var contentService = Services.ContentService;

    // Create a variable for the GUID of the page you want to update
    var guid = new Guid("796a8d5c-b7bb-46d9-bc57-ab834d0d1248");
    
    // Get the page using the GUID you've defined
    var content = contentService.GetById(guid); // ID of your page

    // Set the value of the property with alias 'memberGroup'. The value is the specific ID of the member group
    content.SetValue("memberGroup", 1067);
            
    // Save the change
    contentService.Save(content);
}
```

You can also add multiple groups by creating a comma separated string with the desired member group IDs.

```csharp
@{
    // Set the value of the property with alias 'memberGroup'. 
    content.SetValue("memberGroup", "1067","1068");
}
```

Although the use of a GUID is preferable, you can also use the numeric ID to get the page:

```csharp
@{
    // Get the page using it's id
    var content = contentService.GetById(1234); 
}
```

If Modelsbuilder is enabled you can get the alias of the desired property without using a magic string:

```csharp
@{
    // Set the value of the property with alias 'memberGroup'
    content.SetValue(Home.GetModelPropertyType(x => x.MemberGroup).Alias, 1067);
}
```
