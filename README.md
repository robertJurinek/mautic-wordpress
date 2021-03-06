Mautic WordPress plugin
=======================

[Mautic](http://mautic.org) [Wordpress Plugin](https://wordpress.org/plugins/wp-mautic/) 
inserts Mautic tracking, forms and dynamic content to the WP website. 
Your Mautic instance will be able to track information about your visitors that way.
You can also update your contacts via [Mautic API](https://github.com/mautic/api-library).

## Installation

### Via WP administration

Mautic - WordPress plugin [is listed](https://wordpress.org/plugins/wp-mautic/) in the in the official WordPress plugin repository. That makes it very easy to install it directly form WP administration.

1. Go to *Plugins* / *Add New*.
2. Search for **WP Mautic** in the search box.
3. The "WP Mautic" plugin should appear. Click on Install.
4. Go to *Settings* / WP Mautic and fill in the Base URL of your Mautic instance.

### Via ZIP package

If the installation via official WP plugin repository doesn't work for you, follow these steps:

1. [Download ZIP package](https://github.com/mautic/mautic-wordpress/archive/master.zip).
2. At your WP administration go to *Plugins* / *Add New* / *Upload plugin*.
3. Select the ZIP package you've downloaded in step 1.
4. Go to *Plugins* and enable WP Mautic plugin.
5. Go to *Settings* / WPMautic and fill in the Base URL of your Mautic instance.

## Usage

### Mautic Tracking

You can choose whether you want to use tracking pixel, JavaScript tracking or none of previously mentioned methods.
JavaScript tracking is preferred since tracking pixel is now deprecated and support for it will be removed from Mautic. 
You can check HTML source code (CTRL + U) of your WP website to make sure the plugin works. 
You should be able to find something like this:

```html
<script>
    (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n;
        w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t),
        m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m)
    })(window,document,'script','http://yourmauticsite.com/mtc.js','mt');

    mt('send', 'pageview');
</script>
```

Plugin adds more information (current url, referal url, page title, user language) to the image URL query encoded in base 64 (not humanly readable). This way your Mautic instance receives more valuable data.



### Mautic Forms

To load a Mautic Form to your WP post, insert this shortcode to the place you want the form to appear:

```
[mautic type="form" id="1"]
```

Replace "1" with the form ID you want to load. To get the ID of the form, go to your Mautic, open the form detail and look at the URL. The ID is right there. For example in this URL: http://yourmautic.com/s/forms/view/3 the ID = 3.

### Mautic Dynamic Content

To load dynamic content into your WP content, insert this shortcode where you'd like it to appear:

```
[mautic type="content" slot="slot_name"]Default content to display in case of error or unknown contact.[/mautic]
```

Replace the "slot_name" with the slot name you'd like to load. This corresponds to the slot name you defined when building your campaign and adding the "Request Dynamic Content" contact decision.

### Mautic Gated Videos

Mautic supports gated videos with Youtube, Vimeo, and MP4 as sources.

To load gated videos into your WP content, insert this shortcode where you'd like it to appear:

```
[mautic type="video" gate-time="#" form-id="#" src="URL"]
```

Replace the # signs with the appropriate number. For gate-time, enter the time
 (in seconds) where you want to pause the video and show the mautic form. For 
 form-id, enter the id of the mautic form that you'd like to display as the 
 gate. Replace URL with the browser URL to view the video. In the case of 
 Youtube or Vimeo, you can simply use the URL as it appears in your address 
 bar when viewing the video normally on the providing website. For MP4 videos,
 enter the full http URL to the MP4 file on the server.
 
### Mautic API
You can authorize your plugin with oAuth2 autorization and use Mautic API
for updating contacts (previously called leads). Follow these steps:

1. In your Mautic installation create API credentials with correct callback (you can copy this from plugin's settings page).
2. Fill in Mautic instance URL, Client key and Client secret and click on "Save changes" button.
3. Click on "Authorize" button. Log into your Mautic instance if required and authorize plugin.

Refactoring and API connection support were sponsored by www.svetzitrka.cz
