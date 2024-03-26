# How-to-achieve-item-tapped-in-.NET-MAUI-Rotator
This section explains how to achieve item tapped in the .NET MAUI Rotator control. We can achieve it by following the below steps,

Here, the ItemTapped property provides the tapped event.

**Step 1:** Create a Model and ViewModel classes in sample.

**Step 2:** Create a list of collections in the ViewModel class and add corresponding image value.

**C#:**
**Model**
```
public class RotatorModel
{
    public RotatorModel(string image)
    {
        Image = image;
    }
    private string _image;
    public string Image
    {
        get { return _image; }
        set { _image = value; }
    }
}
```
**C#:**
**ViewModel**
```
public class RotatorViewModel
{
    public RotatorViewModel()
    {
        ImageCollection.Add(new RotatorModel("image1.png"));
        ImageCollection.Add(new RotatorModel("image2.png"));
        ImageCollection.Add(new RotatorModel("image3.png"));
        ImageCollection.Add(new RotatorModel("image4.png"));
        ImageCollection.Add(new RotatorModel("image5.png"));
    }
    private List<RotatorModel> imageCollection = new List<RotatorModel>();
    public List<RotatorModel> ImageCollection
    {
        get { return imageCollection; }
        set { imageCollection = value; }
    }
}
```
**Step 3:** Initialize the .NET MAUI SfRotator in XAML page in which the view model class is set to BindingContext, and use ItemTapped property to make the Rotator items clickable.

**XAML:**
```
<syncfusion:SfRotator VerticalOptions="Center" Background="Transparent"
                    x:Name="rotator"  
                    ItemsSource="{Binding ImageCollection}" 
                    ItemTapped="rotator_ItemTapped">

    <syncfusion:SfRotator.ItemTemplate>
        <DataTemplate>
            <Image Source="{Binding Image}"/>
        </DataTemplate>
    </syncfusion:SfRotator.ItemTemplate>
</syncfusion:SfRotator>
```
**Step 4:** The following event is created by ItemTapped property, here you can provide the code within that event method as per your requirements.

**C#:**
```
private void rotator_ItemTapped(object sender, EventArgs e)
{
    DisplayAlert("Image", "Rotator Item has been tapped", "Ok");
}
```

        
