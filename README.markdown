## CodeIgniter jQuery Mobile Library

Library for the development of mobile versions of pages with the jQuery Mobile framework.

```
public function index()
{
	if($this->agent->is_mobile())
	{
		$this->mobile->header('Welcome to CodeIgniter!', 'e')->button('welcome/help', 'Help', 'info');

		$this->mobile->navbar(array(
			'welcome/index' 	=> array('text' => 'Home',      'icon' => 'home'),
			'welcome/settings'	=> array('text' => 'Settings', 	'icon' => 'gear')
		), 'a');

		$this->mobile->footer('Footer', 'a');

		$this->mobile->view('welcome_message');
	}
}
```

## Methods

### $this->mobile->header(*$title, $theme*)

Create a horizontal bar with the title as the first argument and, as the second 
argument (optional), one of the themes available from jQuery Mobile. It will be a 
letter from a-e. To define a global theme, we can do it within the configuration file. 
Also, if we want the bar to maintain a static position and move with the page, we 
can define it within the configuration file with `$config['mobile']['fixed_toolbars'] = TRUE;`

### $this->mobile->header( … )->back_to(*$url, $text*)

This method must be linked to `header()` to work. Create a button in the left 
area of ​​the horizontal bar with a link to the page that we indicate, 
making a backward slide. By default, jQuery Mobile creates back buttons automatically. 
If we want to set ours, we must do it this way and disable the option of 
`$config['mobile']['backbtn_auto'] = FALSE;` inside the configuration file.

### $this->mobile->header( … )->button(*$url, $text, $icon*)

Again, this method must be linked to that of `header()`. You can also do 
a double chain between  `$this->mobile->header( … )->back_to( … )->button( … )`. 
The latter creates a button in the right area of ​​the navigation bar. As a third argument *(optional)* 
we can define one of the [preset icons within jQuery Mobile](https://api.jqueryui.com/theming/icons/).

### $this->mobile->navbar(*$links = array( ), $theme*)

Just below the top navigation bar, we can create another auxiliary with various buttons. 
To do this, we must create an array with the url as key and the link text as value. 
That is, `$links['welcome/index'] = 'Home'`, for example. 
jQuery Mobile already takes care of automatically dividing this bar into as many 
parts as there are values ​​in the navigation bar. If we want the text to have an icon, 
we can create a compound array specifying the text and the icon we want. That is, 
the previous example with icon would be:  
`$links['welcome/index'] = array('text' => 'Home', 'icon' => 'home');`.
As the second argument to the `navbar()` method, we can set an individual theme for it.

### $this->mobile->footer(*$title, $theme*)

It works exactly the same as the header bar, but creating a navigation bar at the 
bottom of the page. In the same way as the header bar, we can also set the static 
position of the footer bar within the configuration file.

### $this->mobile->view(*$view, $data = array()*)

For its operation, this library has a template file with the base of the page structure. 
This means that we do not have to individually create the header for each page and 
there is only one version of it. Therefore, the only thing we have to load into the view 
**is the content of the page that we want to see**. The operation of this method is exactly 
the same as that of CodeIgniter `$this->load->view( … )` and accepts the same parameters.

## Functions

Apart from the basic methods of the library, some auxiliary functions have been 
defined that help in the development of the pages thanks to jQuery Mobile.

#### link_to(*$url, $title, $attr = array(), $transition*)

It works exactly the same as the `anchor()` function of CodeIgniter but 
it accepts as the last parameter the transition we want to make for the next page 
`('slide', 'slideup', 'slidedown', 'pop', 'fade', 'flip')`.
Inside the configuration file, we can define a general transition for all those 
that are made (it will also be applied in the `back_to()` and `button()` methods. 
Also, the transitions will only be made if we have the option to load by AJAX activated.

### mail_to(*$email, $text*)

Create a link to send an email to the address that we specify as the first argument. 
As a result, a link will appear with the email address. If we want, we can define 
an alternative text to not show the email address directly as the second argument.

### text_field(*$name, $text, $placeholder*)

This function has to be used within forms. Just create a form container as set by 
jQuery Mobile. The arguments to use are the name `name` that will be used within the 
input field, the text that we want to accompany our field as a label (optional) and, 
finally, the *placeholder* text that we want to appear within the field (optional).

### pass_field(*$name, $text, $placeholder*)

It works exactly the same as the `text_field()` function above, but instead of 
creating a text field for forms, it creates a field for passwords.
