**[View document in Syncfusion Xamarin Knowledge base](https://www.syncfusion.com/kb/12134/how-to-remove-expander-sfexpander-from-itemtemplate-of-xamarin-forms-sflistview)**

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
