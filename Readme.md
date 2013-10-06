#BBCombobox.js

Component database combobox widget.
Not only autocomplit.

For database rich application value of component usually is surrogate longint key, but not word from real world.
To addition, display value of component is not everywhere equal to search value.
For this profit component has *keyValue*, *searchValue* and *displayValue* property. But not require all of this to define.

If you need to place value of component ( *keyValue* ) to userdefined html input element - define *store* property as *ID* attribute of this input element.

For backend all of RESTfull product available. But for PHP developer present 2 helper class. Standalone BBCombobox.php (for PDO connection). And for CodeIgniter user My_Controller.php.

#Requirments

So, for JavaScript you must configure Require.js with DomReady! plugin. It's load you class.
Basckbone.js - is main of libraries. But you must configure it with jQuery, Underscore, JSON2 - uff...

#Simple usage

	 requirejs.config({
		waitSeconds: 240,
		 baseUrl: 'bhv/vendors',
		 paths: {
			 bhv: '..',
			 app: '../../test',
			 cms: '../../cms'
		 },
		 urlArgs: "bust=" + (new Date()).getTime(),
		 map: {
			 '*' : {'jquery': 'jquery-1.9.1'}
		 }
	});

	requirejs(['bhv/widget/combobox/BBCombobox', 'domReady!'], function ( bbcmb ) {

	combobox1 = new bbcmb({
		parent: 'combo1', /*userdefined span html element*/
		url: 'test_pdo.php', /*url to backend script*/
		keyName: 'id',
		searchName: 'name',
		displayName: 'richName',
		store: 'input1'
	});
	
#Backend configuration

	 $combo = new BBCombobox( array (
		'connectionString'=>"pgsql:host=localhost;dbname=Ceh16;user=root;password=26682316",
		'table'=>'abc',
		'keyName'=>'id',
		'searchName'=> 'name',
		'displayName'=> '"name"||\'#\'||"id" as richName',
		'order'=>'name',
		'encoding'=>'UTF8'
	) );

	
#Example

Cyryllic UTF-8 text http://apapacy.zz.mu/ok/test_combobox_pdo.html

google_analytics_code: UA-44634095-1
<script type="text/javascript">
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-44634095-1', 'github.com');
  ga('send', 'pageview');

</script>
