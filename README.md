# What is iToast

This page tells you what toast notifications are and why you may need them in your iPhone/iPad application.

***

If you develop already for Android, then you know what it is so you can skip to the next section.

For the others of us: a toast is a spécial way to display 'non intrusive' message to the user. Those message are displayed on a configurable place on the screen and they disapear after a configurable time interval. The way they appear is similar to the way the Growl app (on mac do).


# Difference between iToast and Toast on Android

  * The iToasts disapear when tapped by the user even if the configured time is not elapsed.
  * iToasts can have an image-icon attached to them (info, warning, error).
  * There is application wide configuration object that you can use so that all your iToast looks the same.
  * We are planning to add a plug-in based system so that we can offer many look'n feel for the toasts instead of the default.
  * iToast advertise the chaining of call so that you can create any toast with any configuration in on instruction.

# Benefits of using Toast

Some benefits are:

  * The user is not distracted by such alert and just notice them: he don't need to click "Ok". As a rule of thumb we use iToast now everywhere we would have put a UIAlertView with only a single Button.
  * You can add it anywhere on the screen depending of the importance of the iToast. We display them with a gravity of *Top* when it is of medium importance, *Center* when it is *Very importan* an Bottom when it is of low importance.
# How to use iToast.

# Simple Usage

There is only one way to create an iToast: so you won't need to retain much. In it basic form, you create an iToast this way:


    [[iToast makeText:NSLocalizedString(@"The activity has been successfully saved.", @"")] show];



# Chaining calls
Like in jQuery, you can chain call and terminate by using the *show* method, there are many things you can configure. Look bellow.



    [[[iToast makeText:NSLocalizedString(@"The activity has been successfully saved.", @"")] 
      			setGravity:iToastGravityBottom] show];

    

Note : Above the gravity can be any of `iToastGravityBottom`, `iToastGravityTop`, `iToastGravityCenter`.

  * You can also provide the a physical position on the screen: see the class interface.
  * You can provide two offset value that will be added to the actual position of the iToast: you can use this to either move it a few pixel to the left (negative *offsetLeft*), right (positive *offsetLeft*), top or bottom.

Or


    [[[[iToast makeText:NSLocalizedString(@"Something to display a very long time", @"")] 
        				setGravity:iToastGravityBottom] setDuration:iToastDurationLong] show];
    

*Note :* Above the duration can be any integer (the number of millisecond to display it). There is Three preset you can use for duration:

  * iToastDurationLong 
  * iToastDurationShort 
  * iToastDurationNormal

## The Interface


    @interface iToast : NSObject {
	    iToastSettings *_settings;
	    NSInteger offsetLeft;
	    NSInteger offsetTop;
	
	    NSTimer *timer;
	
	    UIView *view;
	    NSString *text;
    }

    - (void) show;

    - (iToast *) setDuration:(NSInteger ) duration;
    - (iToast *) setGravity:(iToastGravity) gravity 
    			 offsetLeft:(NSInteger) left
    			 offsetTop:(NSInteger) top;
    - (iToast *) setGravity:(iToastGravity) gravity;
    - (iToast *) setPostion:(CGPoint) position;

    + (iToast *) makeText:(NSString *) text;

    -(iToastSettings *) theSettings;

    @end
    

# The Shared Settings

You don't need to set all the settings each time you want to show an iToast. There is a shared settings repo that each iToast copy it setting when first created. 

To modify the shared setting, you first obtain the shared settings like:

    iToastSettings *theSettings = [iToastSettings getSharedSettings];


Then you change the settings:


    theSettings.duration = 4000;


## The interface of the SharedSettings
 
	 @interface iToastSettings : NSObject<NSCopying>{
	NSInteger duration;
	iToastGravity gravity;
	CGPoint postition;
	iToastType toastType;
	
	NSDictionary *images;
	
	BOOL positionIsSet;
	}


	@property(assign) NSInteger duration;
	@property(assign) iToastGravity gravity;
	@property(assign) CGPoint postition;
	@property(readonly) NSDictionary *images;


	- (void) setImage:(UIImage *)img forType:(iToastType) type;
	+ (iToastSettings *) getSharedSettings;
						  
	@end
	


# Not yet implemented

You are interested by those features? write the code and share with the community.

  * Display of icons based of the type of iToast.
  * Plugin based interface to customize the toasts.