# Remove Expander from ListView ItemTemplate Xamarin
This example demonstrates how to remove expander from ListView itemtemplate in Xamarin.Forms ListView.

## Sample

```xaml
 <sflistView:SfListView x:Name="listView" ItemsSource="{Binding InboxInfo}" AutoFitMode="DynamicHeight" ItemSpacing="1"       BackgroundColor="LightGray">
    <sflistView:SfListView.ItemTemplate>
        <DataTemplate>
            <expander:SfExpander HeaderIconPosition="Start" HeaderBackgroundColor="White" IsExpanded="{Binding IsExpanded}">
                <expander:SfExpander.Header>
                    <code>
                    . . .
                    . . .
                    <code>
                </expander:SfExpander.Header>
                <expander:SfExpander.Content>
                    <Grid HeightRequest="100" >
                        <Button x:Name="save" Text="Mark as read" Command="{Binding Path=BindingContext.ReadCommand, Source={x:Reference listView}}" CommandParameter="{Binding .}"/>
                        <Button x:Name="delete" Text="Delete" Command="{Binding Path=BindingContext.DeleteCommand, Source={x:Reference listView}}" CommandParameter="{Binding .}"/>
                    </Grid>
                </expander:SfExpander.Content>
            </expander:SfExpander>
        </DataTemplate>
    </sflistView:SfListView.ItemTemplate>
</sflistView:SfListView>

ViewModel.cs:

ReadCommand = new Command<object>(OnReadClicked);
DeleteCommand = new Command<object>(OnDeleteClicked);

public Command<object> ReadCommand { get; set; }
public Command<object> DeleteCommand { get; set; }


private void OnDeleteClicked(object obj)
{
    var expanderItem = obj as InboxInfo;
    this.InboxInfo.Remove(expanderItem);
}

private void OnReadClicked(object obj)
{
    var expanderItem = obj as InboxInfo;
    expanderItem.FontStyle = FontAttributes.None;
    expanderItem.IsExpanded = false;
}
```

**[View document in Syncfusion Xamarin Knowledge base](https://www.syncfusion.com/kb/12134/how-to-remove-expander-sfexpander-from-itemtemplate-of-xamarin-forms-sflistview)**

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.