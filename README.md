# What is iToast

This page tells you what toast notifications are and why you may need them in your iPhone/iPad application.

***

If you develop already for Android, then you know what it is so you can skip to the next section.

For the others of us: a toast is a spécial way to display 'non intrusive' message to the user. Those message are displayed on a configurable place on the screen and they disapear after a configurable time interval. The way they appear is similar to the way the Growl app (on mac do).


# Difference between iToast and Toast on Android =

  * The iToasts disapear when tapped by the user even if the configured time is not elapsed.
  * iToasts can have an image-icon attached to them (info, warning, error).
  * There is application wide configuration object that you can use so that all your iToast looks the same.
  * We are planning to add a plug-in based system so that we can offer many look'n feel for the toasts instead of the default.
  * iToast advertise the chaining of call so that you can create any toast with any configuration in on instruction.

# Benefits of using Toast = 

Some benefits are:

  * The user is not distracted by such alert and just notice them: he don't need to click "Ok". As a rule of thumb we use iToast now everywhere we would have put a UIAlertView with only a single Button.
  * You can add it anywhere on the screen depending of the importance of the iToast. We display them with a gravity of *Top* when it is of medium importance, *Center* when it is *Very importan* an Bottom when it is of low importance.

# Not yet implemented

You are interested by those features? write the code and share with the community.

  * Display of icons based of the type of iToast.
  * Plugin based interface to customize the toasts.