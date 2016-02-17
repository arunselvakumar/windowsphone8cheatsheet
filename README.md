# Windows Phone 8 Developer Cheat Sheet
<b>Folder Structure of Windows Phone </b>
App.xaml 
-> Starting point of every Windows Phone Application
-> Initializes the application and the frame (which will contain pages)

MainPage.xaml
-> Default main page of the application
-> This page is launched after teh app is initialized
-> Every page inherits from PhoneApplicationPage 

Assets (Folder)
-> Folder which containes images

Resources (Folder)
-> Has AppResource.resx file by default
-> Every Language will have a different AppResource.resx File

Manifest File
-> Present inside Properties folder (WMAppManifest.xml)
-> Important File
-> It is called manifest because it's used to declare all the capabilities and features of the application


* Manifest File is XML, But when opened in VS - It pops as a screen with following Tabs
1. APPLICATION UI
-> You can browse and add Application Tile Image, Splash Screen.. etc

2. Capabilities
-> There will be a list of Hardware & Software Features - Check what your application will use
-> Say for example you are desiging Tureet App for Windows Phone - You will need capability such as accessing user's photo, which you should enable here

3. Requirements:
-> Don't confuse with Capabilities
-> Requirements are Hardware and Software reqirements for the app to install
-> Say if you are developing a video chat application, you will definitly need front-cam. If you enable this in Requirments the app will not be downloadable from the store if the device does not have front cam

4. Packing:
-> Contains package information like, the Company Name, Version Number, etc

Some Refreshing Points in XAML:
1. No Click Events, Use Tap Events in Windows Phone as opposed to WPF
<Button Tap="OnButtonTapped" />

2. <phone.PhoneApplicationPage.Resource>  --- You can place resources such as styles and converters here - Hope you remember --- </phone.PhoneApplicationPage.Resource>

3. Styling:
	<TextBlock Style="{StaticResource TextNormalStyle}"/>
-> TextNormalStyle is Style return inside <Page.Resources></Page.Resources> like this
	<Style x:Key="TextNormalStyle" TargetType="TextBlock">
		<Setter Property="FontSize" Value="24" />
		<Setter Property="FontWeight" Value="Bold" />
	</Style>
-> or styles can be maintained in different xaml file and referred inside page resources like this
	<Page.Resources>
		<ResourceDictionary>
			<ResourceDictionary Source="Assets/Styles.xaml"/>
		</ResourceDictionary>
	</Page.Resources>
4. Data Template:
-> Data Template is applied to define a control's appearance
eg., 
<DataTemplate x:Key="CountryTemplate">
	<StackPanel Orientation="Vertical">
		<Image Src={Binding Path = ImageUrl}/>
		<TextBlock Text={Binding Path=CountryName}/>
	<StackPanel>
</DataTemplate>

<ListBox ItemTemplate = "{StaticResource CountryTemplate}"/>

5. Animations:
-> We generally use Storyboards to do animations
-> Animations are easy to do using Microsoft Blend

DataBinding:
-> Binds the Properties in the DataContext
1. Binding a Property
	<TextBox Text="{Binding Path=Name, Mode=TwoWay}" />
2. Binding to Element
	<TextBox x:Name="NewTextBox"/>
	<TextBlock Text="{Binding ElementName=NewTextBox, Path=Text}" />
3. INotifyPropertyChanged
-> Implement in the ViewModel to notify any property changes to the UI
-> When you implement INofityPropertyChanged, there is an Event called PropertyChanged - Raise this event when value of property changes

Converters:
-> Converters are useful if you want to show something that is different from the object source (Like appending a string to the bindable object)
-> Converters are just a class which implements IValueConverter
eg., 
Public TestConverter : IValueConverter
{
	public object Convert(--------)

	public object convertBack(-------)
}

Core Windows Phone Concepts:
1. Navigation

i) Navigation Services
NavigationService.Navigate(new Uri('/Pages/Page2.xaml', UriKind.Relative));

ii) Navigation Overrides (Available across all pages)
override OnNavigatedTo(NavigationEventArgs e) 
{
	// When you move from another page to current page
}

override OnNavigatedFrom(NavigationEventArgs e)
{
	// When you move from current page to next page
}

iii) Passing Parameters to another page
NavigationContext.QueryString --> Dictionary that holds information as key value pair
Eg.
-> Sending Value as Query String
	    string uri = string.Format("/Page1.xaml?name={0}&&rollno={1}", Name, Rollno);
            //adding Navigation Statement
            NavigationService.Navigate(new Uri(uri, UriKind.Relative));

-> Receiving Value
	protected override void OnNavigatedTo(NavigationEventArgs e)
	{
		var value = NavigationContext.QueryString.ContainsKey("id"))
	}

iv) Navigation Stack
-> Every Application has navigatiobn stack, which is a list of pages that the user has moved throught while using the application
-> Properties (in NavigationServices) : CanGoBack, CanGoForward
-> Methods (in NavigationServices) : GoBack(), GoForward(), Navigate(), Refresh(), StopLoading()
-> Events (in NavigationServices) : LoadCompleted, Navigated, Navigatign, NavigationFailed, NavigationProgress, NavigationStopped

