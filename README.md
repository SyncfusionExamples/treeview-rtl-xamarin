# How to work with RTL in Xamarin.Forms TreeView (SfTreeView)

You can use [SfTreeView](https://help.syncfusion.com/xamarin/treeview/overview) with [RTL](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/localization/right-to-left) in Xamarin.Forms by setting the [FlowDirection](https://docs.microsoft.com/en-us/dotnet/api/xamarin.forms.visualelement.flowdirection?view=xamarin-forms#Xamarin_Forms_VisualElement_FlowDirection) property for SfTreeView.

You can also refer the following article.

https://www.syncfusion.com/kb/11414/how-to-work-with-rtl-in-xamarin-forms-treeview-sftreeview

**XAML**

Set **FlowDirection** as **RightToLeft** to TreeView.
``` xml
<treeview:SfTreeView x:Name="treeView" ItemHeight="40" Indentation="15" ExpanderWidth="40" AutoExpandMode="AllNodesExpanded" VerticalOptions="Center"
                        FlowDirection="{OnPlatform Android='RightToLeft',iOS='RightToLeft'}" ItemTemplateContextType="Node" ChildPropertyName="SubFiles" 
                        ItemsSource="{Binding ImageNodeInfo}">
    <treeview:SfTreeView.ItemTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                    <Grid x:Name="grid" Padding="5,5,5,5" RowSpacing="0">
                        <Grid.ColumnDefinitions>
                            <ColumnDefinition Width="40" />
                            <ColumnDefinition Width="*" />
                        </Grid.ColumnDefinitions>
                        <Image Source="{Binding Content.ImageIcon}" VerticalOptions="Center" HorizontalOptions="Center"
                                HeightRequest="35" WidthRequest="35"/>
                        <Grid Grid.Column="1" RowSpacing="1" Padding="1,0,0,0" VerticalOptions="Center">
                            <Label Text="{Binding Content.ItemName}" LineBreakMode="NoWrap" VerticalTextAlignment="Center" HorizontalOptions="{OnPlatform iOS='StartAndExpand'}"/>
                        </Grid>
                    </Grid>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </treeview:SfTreeView.ItemTemplate>
</treeview:SfTreeView>
```
In UWP platform, the ScrollView is not changed when RTL is enabled (framework issue). To overcome this issue, set the FlowDirection property in constructor of MainPage in UWP renderer.

**C#**

Set **FlowDirection** to **RightToLeft** in constructor of MainPage
``` c#
namespace TreeViewXamarin.UWP
{
    public sealed partial class MainPage
    {
        public MainPage()
        {
            this.InitializeComponent();
            this.FlowDirection = FlowDirection.RightToLeft;
            SfTreeViewRenderer.Init();
            LoadApplication(new TreeViewXamarin.App());
        }
    }
}
```
**Output**

![TreeViewRTL](https://github.com/SyncfusionExamples/treeview-rtl-xamarin/blob/master/ScrennShots/TreeViewRTL.png)
