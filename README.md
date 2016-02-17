#Windows Phone 8 Developer Cheat Sheet 
<html>
	<head>
		<title></title>
	</head>
	<body>
		<div>
			<strong>Folder Structure of Windows Phone</strong></div>
		<div>
			<strong>App.xaml&nbsp;</strong></div>
		<ul>
			<li>
				Starting point of every Windows Phone Application</li>
			<li>
				Initializes the application and the frame (which will contain pages)</li>
		</ul>
		<div>
			<strong>MainPage.xaml</strong></div>
		<ul>
			<li>
				Default main page of the application</li>
			<li>
				This page is launched after teh app is initialized</li>
			<li>
				Every page inherits from PhoneApplicationPage&nbsp;</li>
		</ul>
		<div>
			<strong>Assets (Folder)</strong></div>
		<ul>
			<li>
				Folder which containes images</li>
		</ul>
		<div>
			<strong>Resources (Folder)</strong></div>
		<ul>
			<li>
				Has AppResource.resx file by default</li>
			<li>
				Every Language will have a different AppResource.resx File</li>
		</ul>
		<div>
			<strong>Manifest File</strong></div>
		<ul>
			<li>
				Present inside Properties folder (WMAppManifest.xml)</li>
			<li>
				Important File</li>
			<li>
				It is called manifest because it&#39;s used to declare all the capabilities and features of the application</li>
		</ul>
		<div>
			Manifest File is XML, But when opened in VS - It pops as a screen with following Tabs</div>
		<div>
			<strong>1. APPLICATION UI</strong></div>
		<ul>
			<li>
				You can browse and add Application Tile Image, Splash Screen.. etc</li>
		</ul>
		<div>
			<strong>2. Capabilities</strong></div>
		<ul>
			<li>
				There will be a list of Hardware &amp; Software Features - Check what your application will use</li>
			<li>
				Say for example you are desiging Tureet App for Windows Phone - You will need capability such as accessing user&#39;s photo, which you should enable here</li>
		</ul>
		<div>
			<strong>3. Requirements:</strong></div>
		<ul>
			<li>
				Don&#39;t confuse with Capabilities</li>
			<li>
				Requirements are Hardware and Software reqirements for the app to install</li>
			<li>
				Say if you are developing a video chat application, you will definitly need front-cam. If you enable this in Requirments the app will not be downloadable from the store if the device does not have front cam</li>
		</ul>
		<div>
			<strong>4. Packing:</strong></div>
		<ul>
			<li>
				Contains package information like, the Company Name, Version Number, etc</li>
		</ul>
		<div>
			<strong>Some Refreshing Points in XAML:</strong></div>
		<div>
			1. No Click Events, Use Tap Events in Windows Phone as opposed to WPF</div>
		<blockquote>
			<div>
				&lt;Button Tap=&quot;OnButtonTapped&quot; /&gt;</div>
		</blockquote>
		<div>
			&nbsp;</div>
		<div>
			2. &lt;phone.PhoneApplicationPage.Resource&gt; &nbsp;--- You can place resources such as styles and converters here - Hope you remember --- &lt;/phone.PhoneApplicationPage.Resource&gt;</div>
		<div>
			&nbsp;</div>
		<div>
			3. Styling:</div>
		<blockquote>
			<div>
				&lt;TextBlock Style=&quot;{StaticResource <span style="color:#ff0000;">TextNormalStyle</span>}&quot;/&gt;</div>
			<div>
				<span style="color:#ff0000;">TextNormalStyle </span>is Style return inside &lt;Page.Resources&gt;&lt;/Page.Resources&gt; like this</div>
			<div>
				&lt;Style x:Key=&quot;TextNormalStyle&quot; TargetType=&quot;TextBlock&quot;&gt;</div>
			<div style="margin-left: 40px;">
				&lt;Setter Property=&quot;FontSize&quot; Value=&quot;24&quot; /&gt;</div>
			<div style="margin-left: 40px;">
				&lt;Setter Property=&quot;FontWeight&quot; Value=&quot;Bold&quot; /&gt;</div>
			<div>
				&lt;/Style&gt;</div>
		</blockquote>
		<div>
			or styles can be maintained in different xaml file and referred inside page resources like this</div>
		<blockquote>
			<div>
				&lt;Page.Resources&gt;</div>
			<div style="margin-left: 40px;">
				&lt;ResourceDictionary&gt;</div>
			<div style="margin-left: 80px;">
				&lt;ResourceDictionary Source=&quot;Assets/Styles.xaml&quot;/&gt;</div>
			<div style="margin-left: 40px;">
				&lt;/ResourceDictionary&gt;</div>
			<div>
				&lt;/Page.Resources&gt;</div>
		</blockquote>
		<div>
			4. Data Template:</div>
		<div>
			Data Template is applied to define a control&#39;s appearance</div>
		<div>
			eg.,&nbsp;</div>
		<blockquote>
			<div>
				&lt;DataTemplate x:Key=&quot;CountryTemplate&quot;&gt;</div>
			<div style="margin-left: 40px;">
				&lt;StackPanel Orientation=&quot;Vertical&quot;&gt;</div>
			<div style="margin-left: 80px;">
				&lt;Image Src={Binding Path = ImageUrl}/&gt;</div>
			<div style="margin-left: 80px;">
				&lt;TextBlock Text={Binding Path=CountryName}/&gt;</div>
			<div style="margin-left: 40px;">
				&lt;StackPanel&gt;</div>
			<div>
				&lt;/DataTemplate&gt;</div>
		</blockquote>
		<blockquote>
			<div>
				&nbsp;</div>
			<div>
				&lt;ListBox ItemTemplate = &quot;{StaticResource CountryTemplate}&quot;/&gt;</div>
		</blockquote>
		<div>
			&nbsp;</div>
		<div>
			5. Animations:</div>
		<div>
			-&gt; We generally use Storyboards to do animations</div>
		<div>
			-&gt; Animations are easy to do using Microsoft Blend</div>
		<div>
			&nbsp;</div>
		<div>
			<strong>DataBinding:</strong></div>
		<div>
			Binds the Properties in the DataContext</div>
		<div>
			<strong>1. Binding a Property</strong></div>
		<blockquote>
			<div>
				&lt;TextBox Text=&quot;{Binding Path=Name, Mode=TwoWay}&quot; /&gt;</div>
		</blockquote>
		<div>
			<strong>2. Binding to Element</strong></div>
		<blockquote>
			<div>
				&lt;TextBox x:Name=&quot;NewTextBox&quot;/&gt;</div>
			<div>
				&lt;TextBlock Text=&quot;{Binding ElementName=NewTextBox, Path=Text}&quot; /&gt;</div>
		</blockquote>
		<div>
			<strong>3. INotifyPropertyChanged</strong></div>
		<ul>
			<li>
				Implement in the ViewModel to notify any property changes to the UI</li>
			<li>
				When you implement INofityPropertyChanged, there is an Event called PropertyChanged - Raise this event when value of property changes</li>
		</ul>
		<div>
			<strong>Converters:</strong></div>
		<ul>
			<li>
				Converters are useful if you want to show something that is different from the object source (Like appending a string to the bindable object)</li>
			<li>
				Converters are just a class which implements IValueConverter</li>
		</ul>
		<blockquote>
			<div>
				eg.,&nbsp;</div>
			<div>
				Public TestConverter : IValueConverter</div>
			<div>
				{</div>
			<div>
				public object Convert(--------)</div>
			<div>
				&nbsp;</div>
			<div>
				public object convertBack(-------)</div>
			<div>
				}</div>
		</blockquote>
		<div>
			&nbsp;</div>
		<div>
			<strong>Core Windows Phone Concepts:</strong></div>
		<div>
			<strong>1. Navigation</strong></div>
		<div>
			&nbsp;</div>
		<div>
			<strong>i) Navigation Services</strong></div>
		<div>
			NavigationService.Navigate(new Uri(&#39;/Pages/Page2.xaml&#39;, UriKind.Relative));</div>
		<div>
			&nbsp;</div>
		<div>
			<strong>ii) Navigation Overrides (Available across all pages)</strong></div>
		<blockquote>
			<div>
				override OnNavigatedTo(NavigationEventArgs e)&nbsp;</div>
			<div>
				{</div>
			<div>
				// When you move from another page to current page</div>
			<div>
				}</div>
			<div>
				&nbsp;</div>
			<div>
				override OnNavigatedFrom(NavigationEventArgs e)</div>
			<div>
				{</div>
			<div>
				// When you move from current page to next page</div>
			<div>
				}</div>
		</blockquote>
		<div>
			<strong>iii) Passing Parameters to another page</strong></div>
		<div>
			NavigationContext.QueryString --&gt; Dictionary that holds information as key value pair</div>
		<div>
			Eg.</div>
		<div>
			<strong>Sending Value as Query String</strong></div>
		<blockquote>
			<div>
				string uri = string.Format(&quot;/Page1.xaml?name={0}&amp;&amp;rollno={1}&quot;, Name, Rollno);</div>
			<div>
				NavigationService.Navigate(new Uri(uri, UriKind.Relative));</div>
		</blockquote>
		<div>
			<strong>Receiving Value</strong></div>
		<blockquote>
			<div>
				protected override void OnNavigatedTo(NavigationEventArgs e)</div>
			<div>
				{</div>
			<div style="margin-left: 40px;">
				var value = NavigationContext.QueryString.ContainsKey(&quot;id&quot;))</div>
			<div>
				}</div>
		</blockquote>
		<div>
			&nbsp;</div>
		<div>
			<strong>iv) Navigation Stack</strong></div>
		<ul>
			<li>
				Every Application has navigatiobn stack, which is a list of pages that the user has moved throught while using the application</li>
			<li>
				Properties (in NavigationServices) : CanGoBack, CanGoForward</li>
			<li>
				Methods (in NavigationServices) : GoBack(), GoForward(), Navigate(), Refresh(), StopLoading()</li>
			<li>
				Events (in NavigationServices) : LoadCompleted, Navigated, Navigatign, NavigationFailed, NavigationProgress, NavigationStopped</li>
		</ul>
		<div>
			<strong>Application LifeCycle of Windows Phone</strong></div>
		<div>
			&nbsp;</div>
		<div style="text-align: center;">
			<img alt="" src="https://lnluis.files.wordpress.com/2011/09/life-cycle-600x345.png" style="width: 600px; height: 345px;" /></div>
		<div>
			&nbsp;</div>
		<div>
			<div>
				You can control the application lifecycle using PhoneApplicationService class which is in App.xaml</div>
			<blockquote>
				<div>
					&lt;Application.ApplicationLifetimeObjects&gt;</div>
				<div style="margin-left: 40px;">
					&nbsp;&lt;shell:PhoneApplicationService &nbsp; &nbsp; &nbsp; Launching=&quot;Application_Launching&quot;&nbsp;</div>
				<div style="margin-left: 280px;">
					Closing=&quot;Application_Closing&quot;</div>
				<div style="margin-left: 280px;">
					Activated=&quot;Application_Activated&quot;</div>
				<div style="margin-left: 280px;">
					Deactivated=&quot;Application_Deactivated&quot;/&gt;</div>
				<div>
					&lt;/Application.ApplicationLifetimeObjects&gt;</div>
			</blockquote>
			<div>
				&nbsp;</div>
			<div>
				<strong>Application_Launching : </strong>Invoked when app starts for first time</div>
			<div>
				<strong>Application_Closing : </strong>Invloked when the app is completly closed</div>
			<div>
				<strong>Application_Activated : </strong>Invoked when app is resumed from a suspended state</div>
			<div>
				<strong>Application_Deactvated :</strong> Invoked when app is suspended</div>
			<div>
				&nbsp;</div>
			<div>
				<strong>Checking if the Application is Dormanted or Tombstoned:</strong></div>
			<blockquote>
				<div>
					private void Application_Activated(object sender, ActivatedEventArgs e)</div>
				<div>
					{</div>
				<div style="margin-left: 40px;">
					&nbsp;if (e.IsApplicationInstancePreserved)</div>
				<div style="margin-left: 40px;">
					&nbsp;{</div>
				<div style="margin-left: 80px;">
					&nbsp;Debug.WriteLine(&quot;The app was dormant&quot;);</div>
				<div style="margin-left: 40px;">
					&nbsp;}</div>
				<div style="margin-left: 40px;">
					&nbsp;else</div>
				<div style="margin-left: 40px;">
					&nbsp;{</div>
				<div style="margin-left: 80px;">
					&nbsp;Debug.WriteLine(&quot;The app was tombstoned&quot;);</div>
				<div style="margin-left: 40px;">
					&nbsp;}</div>
				<div>
					}</div>
			</blockquote>
			<div>
				&nbsp;</div>
			<div>
				<strong>Orientation:</strong></div>
			<div>
				By default, every new page added to windows phone is displayed in portrait mode</div>
			<div>
				This behaviour can be controlled by attributes as follows:</div>
			<blockquote>
				<div>
					&lt;phone:PhoneApplicationPage</div>
				<div>
					&nbsp;x:Class=&quot;Webinar.Rest.MainPage&quot;</div>
				<div>
					<span style="color:#008000;">&nbsp;SupportedOrientations=&quot;</span><span style="color:#ff0000;">Portrait</span><span style="color:#008000;">&quot; Orientation=&quot;</span><span style="color:#ff0000;">Portrait</span><span style="color:#008000;">&quot;</span></div>
				<div>
					<span style="color:#008000;">&nbsp;OrientationChanged=&quot;</span><span style="color:#ff0000;">MainPage_OnOrientationChanged</span><span style="color:#008000;">&quot;</span>&gt;</div>
			</blockquote>
			<div>
				&nbsp;</div>
			<blockquote>
				<div>
					private void <span style="color:#ff0000;">MainPage_OnOrientationChanged</span>(object sender, OrientationChangedEventArgs e)</div>
				<div>
					{</div>
				<div style="margin-left: 40px;">
					&nbsp;if (e.Orientation == PageOrientation.PortraitUp || e.Orientation == PageOrientation.PortraitDown)</div>
				<div style="margin-left: 40px;">
					&nbsp;{</div>
				<div style="margin-left: 40px;">
					&nbsp;</div>
				<div style="margin-left: 40px;">
					&nbsp;}</div>
				<div>
					}</div>
			</blockquote>
		</div>
		<p>
			&nbsp;</p>
	</body>
</html>
