# Different column types in .NET MAUI DataGrid (SfDataGrid)
In this article, we will show how to configure and use different column types in the Syncfusion .NET MAUI DataGrid (SfDataGrid). The grid supports rich column types such as image, numeric, text, checkbox, date, and fully templated columns so you can present heterogeneous data effectively. The examples below are adapted from the included MainPage.xaml.

## XAML
```
<ContentPage.BindingContext>
    <local:DealerInfoViewModel />
</ContentPage.BindingContext>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding DealerInformation}"
                       AutoGenerateColumnsMode="None"
                       ColumnWidthMode="Fill"
                       HorizontalScrollBarVisibility="Always"
                       VerticalScrollBarVisibility="Always"
                       HeaderRowHeight="52"
                       RowHeight="80">

    <syncfusion:SfDataGrid.DefaultStyle>
        <syncfusion:DataGridStyle HeaderRowFontFamily="Roboto-Medium"/>
    </syncfusion:SfDataGrid.DefaultStyle>

    <syncfusion:SfDataGrid.Columns>
        <!-- Image column -->
        <syncfusion:DataGridImageColumn MappingName="DealerImage"
                                        HeaderText="Dealer"
                                        CellTextAlignment="Center"
                                        HeaderTextAlignment="Center"/>

        <!-- Numeric column -->
        <syncfusion:DataGridNumericColumn MappingName="ProductID"
                                          HeaderText="ID"
                                          Format="D"
                                          CellTextAlignment="Center"
                                          HeaderTextAlignment="Center"/>

        <!-- Text column -->
        <syncfusion:DataGridTextColumn MappingName="DealerName"
                                       HeaderText="Name"
                                       CellTextAlignment="Center"
                                       HeaderTextAlignment="Center"/>

        <!-- CheckBox column -->
        <syncfusion:DataGridCheckBoxColumn MappingName="IsOnline"
                                           HeaderText="Is Online"
                                           CellTextAlignment="Center"
                                           HeaderTextAlignment="Center"/>

        <!-- Date column -->
        <syncfusion:DataGridDateColumn MappingName="ShippedDate"
                                       HeaderText="Shipped Date"
                                       CellTextAlignment="Center"
                                       HeaderTextAlignment="Center"/>

        <!-- Template column (custom header + rich cell layout) -->
        <syncfusion:DataGridTemplateColumn MappingName="Name">
            <syncfusion:DataGridTemplateColumn.HeaderTemplate>
                <DataTemplate>
                    <Label Text="Product Details"
                           FontFamily="Roboto-Medium"
                           FontSize="14"
                           FontAttributes="Bold"
                           VerticalOptions="Center" />
                </DataTemplate>
            </syncfusion:DataGridTemplateColumn.HeaderTemplate>
            <syncfusion:DataGridTemplateColumn.CellTemplate>
                <DataTemplate>
                    <StackLayout Orientation="Horizontal">
                        <StackLayout>
                            <Label Text="ID :" />
                            <Label Text="No :" />
                            <Label Text="Price :" />
                        </StackLayout>
                        <StackLayout>
                            <Label Text="{Binding ProductID}" />
                            <Label Text="{Binding ProductNo}" />
                            <Label Text="{Binding ProductPrice, StringFormat='{0:C}'}" />
                        </StackLayout>
                    </StackLayout>
                </DataTemplate>
            </syncfusion:DataGridTemplateColumn.CellTemplate>
        </syncfusion:DataGridTemplateColumn>
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
```

## What each column does
- DataGridImageColumn: Renders images for each row using a property, ideal for avatars, logos, or thumbnails.
- DataGridNumericColumn: Displays numeric values with optional formats (D, N, C, P), enabling localization-friendly number rendering.
- DataGridTextColumn: Standard text display for strings or any ToString()-able value.
- DataGridCheckBoxColumn: Two-state boolean editor with consistent UI; can be bound to a bool property like IsOnline.
- DataGridDateColumn: Shows dates with built-in parsing/formatting and supports culture-aware rendering.
- DataGridTemplateColumn: Fully customizable column where you control header and cell layout using XAML templates.

## Notes and tips
- Set AutoGenerateColumnsMode="None" to define explicit columns and ensure column order is predictable.
- Use ColumnWidthMode="Fill" to distribute available width across columns; switch to Auto or LastColumnFill to mix auto-size and fixed widths.
- Header and cell alignment can be controlled independently via HeaderTextAlignment and CellTextAlignment.
- For consistent typography, apply a DataGridStyle via SfDataGrid.DefaultStyle, as shown above.
- Use OnPlatform resources in XAML to tune widths and margins per platform (Android, iOS, WinUI, MacCatalyst).

## Troubleshooting
- Column not visible: Ensure MappingName exactly matches the bound property and AutoGenerateColumnsMode is set correctly.
- Unexpected formatting: Check Format strings (for numeric/date columns) and the current culture settings.
- Template not applied: Verify templates are nested under DataGridTemplateColumn.HeaderTemplate or .CellTemplate, not directly under Columns.

## Learn more
- [.NET MAUI DataGrid overview](https://help.syncfusion.com/maui/datagrid/overview)
- [Column Types in .NET MAUI DataGrid](https://help.syncfusion.com/maui/datagrid/column-types)
- [Product page and feature tour](https://www.syncfusion.com/maui-controls/maui-datagrid) 

##### Conclusion
You have seen how to configure multiple column types in the Syncfusion .NET MAUI DataGrid to present diverse data clearly. Mix built-in column types for common scenarios and switch to DataGridTemplateColumn when you need full control over the header or cell layout. Explore the documentation links above for deeper guidance and additional samples such as sorting, filtering, editing, and styling.
