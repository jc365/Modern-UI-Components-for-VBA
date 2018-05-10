# A friendly helper DLL that will makes you smile.
No installation, no ActiveX, no Admin-Rights. Just add this Dll to your VBA projects and have some cool UI features. Have only tested in MS Access but it should work in all VBA environment. Works with ACCDE too.

## What is does?
Helps you to make your application more user-friendly by providing some .NET components and functions that you can use within your VBA application. Visually and functionally better than VBA!

## How to use?
Some VBA skills are required! Just download the <a href="https://github.com/krishKM/VBA_TOOLS/tree/master/samples"> sample</a> ACCDB from sample folder where you can find the Dll. Copy and paste the functions you require to your VBA application. 


# Interesting features
<ul>
  <li>Show non-blocking notifications</li>
  <li>Show Cool DialogBox</li>
  <li>Show Cool Progressbar</li>
  <li>Download a file with progressbar</li>
  <li><a href="https://github.com/krishKM/VBA_TOOLS/blob/master/README.md#show-cool-inputboxes">Show Cool InputBoxes</a></li>
</ul>

### [Show non-blocking notifications]
Inspired from Toastr (https://github.com/CodeSeven/toastr).
Allowing VBA users to show simple notifications without having to wait or stress their VBA application.
With a simple command a little colourful notification pops up with a message without taking any focus or disturbing the user.
I mainly use it to show messages that do not require action. I.e. A mail has arrived or a task has been completed.

![just a notification](https://raw.githubusercontent.com/krishKM/VBA_TOOLS/master/screenshots/information.png)

## customise your notification like you want:
following customisations are possible now.
```
1.Message   : can contain <a href="">text</a> for hyperlinks (any other html tags are ignored, hyperlink must begin with www or http or https (basically web links only?)
2.Duration in Milli-Seconds (default 2000. 0 will keep the notification for long time.  int.max)
3.Background colour (html colour code)
4.Font colour (html colour code)
5.X,Y position on the desktop
```



![picture of 3 notifications](https://raw.githubusercontent.com/krishKM/VBA_TOOLS/master/screenshots/collections.png)
```VBA
'used commands
Toastr.Toast "Ups something went wrong!",vberror,0
Toastr.Toast "Yellow weather warning!",vbexclamation,0
Toastr.Toast "You've just received a notification",vbinformation,0
```

in Action
![Notification in action gif](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InAction.gif)
![Notification in action gif](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InAction1.gif)

#### how about little interaction with user and show some hyperlinks?
You can have html ```<a href="">text</a>``` tags in your message which will be translated into hyperlinks.
![Notification in action gif](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/Hyperlink.png)

## Download 
Download the sample and test it in your project. Please leave comment how you feel.
<a href="https://github.com/krishKM/VBA_TOOLS/tree/master/samples"> Samples</a>

<hr>

# Show Cool DialogBox
Standard Message boxes are great but sometimes you want little more than standard features.
I.e
<ul>
  <li>Be able to have some colours</li>
  <li>Be able to have more than 3 buttons</li>
  <li>Be able auto-close</li>
  <li>Be able to use HTML tags </li>
  <li>not stressing your vba app with a loop?</li>
</ul>
Meet the new simplified DialogBox for VBA users. This dialogbox will allow above listed features and should help you to keep your application colourful. :) This feature is still under development and could some feedback from testers.


![Cool DialogBox](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/DialogboxGreen.png)
![Cool DialogBox1](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/4Buttons.png)

There is vba wrapper in the sample accdb which can be extended as per your need. It uses the 3rd party JSON Converter plugin with some miner fixes from my side.

```
  'usign the wrapper it would be as simple as 
  Debug.Print gDll.DialogRich("This is a title", "Some content", (vbExclamation + vbYesNo))
```

# Show cool Progressbar
Progressbars are crucial element when informing users about a progress. Meet the cool progressbar which can pop up on top of your application at any time with a simple code as such as.

```
  Dim ProgressBarID As Long
  ProgressBarID = gDll.ShowProgressBar(100, "Executing your query", "Please wait. We are preparing printer drivers")
    
  ProgressBarID = gDll.SetProgressBar(ProgressBarID, 10, "Waiting for driver..")
```
![Cool ProgressbarGreen](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/ProgressBar.png)

As usual, you are allowed to change theme colours as per your taste.
![Cool ProgressbarRed](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/ProgressBarRed.png)

### note:
```ShowProgressBar and SetProgressBar``` returns an ID which you can refer your progressbar to. This also allows VBA users to have multiple progressbars at the same time. 

# Show Cool InputBoxes
InputBox another heavily used component. Some like the plain system looking InputBox but we love the modern UI colours :)
What would you chose from these tables?

![InputBoxCollection](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InputBoxDefault.png)  ![InputBoxCollection](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InputBoxMultiline.png) 

## Nice colours! but what's the point?
The new InputBoxes comes with some inbuilt functions and can be configured accordingly.
Following types are supported now.
```
'        Password        = 1, : Masked using systempassword mask
'        Text            = 2, : Single line text:
'        MultilineText   = 32, : Multi line text box
'        Number          = 4, : Numbers only
'        ShortDate       = 8, : Masked dd/mm/yyyy. Dates are validated upon exit
'        LongDate        = 16,  : masked using dd/Month/yyyy
'        DateTime        = 48,  : masked using dd/mm/yyyy hh:mm:ss
' With the dll in place, use it as

  result = gDll.DLL.showinputbox(Type:=32, Title:="", Message:="Tell us what happened on that day!", ThemeBg:="", ThemeForeColour:="")
```

in action:

![InputBoxCollection](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InputBox.png)

as always we can change theme colours:)

![purple input box](https://github.com/krishKM/VBA_TOOLS/blob/master/screenshots/InputBoxPurple.png)

<hr>
<hr>


# [Other futures that are interesting]


### Download a file and show progressbar for vba
Another cool feature. This function allows you to download a file from the internet and shows the download progress using above cool progressbar.

```DownloadedFile = DLL.DownloadAFile(Url, [Destination], [OverWrite = true], [ShowProgress = true])```
Except the Url, all other parameters are optional. If destination is not provided. File will be saved in application.path

### Save Clipboard images to local file
Sometimes, simple things can be very dificult in VBA. If you are after saving clipboard image to a local path. Check this function.

``` SaveClipboardToImage(string PathToSave, string FileName, string ImageType) ``` All parameters are optional and by default Jpeg image type is used. If the clipbord object contains any images, it will be saved wherever you want and the file path is returned.
in the sample accdb, there is a wrapper ```SaveClipboardToImage``` check it out.



### [Receive SignalR Messages]
This works for me because I do have own signalR server but generally is under development or say not ready yet!
It's like google push messages or any other push message service. You can send notification to all of your logged in yours from one place.
Expanding this, you could also use as a chat server where all logged in participants could send and receive messages among them.
Again without stressing VBA apps.


### ByteToImage
ByteToImage(byte[] byteArraym string TemporaryPath, bool useCache) is a function for MS Access users. Basically you can convert a byteARray received from database into a pictures.
Will return the path of the image file. Use the path as image location for your image property.
something like Me.Image32.Picture = gDll.ByteToImage(ByteArray, "SaveLocationPath")

### FTPS_UPLOAD
simple tool which uses WinScp to upload files securely to your host. Handy if you want to upload some files without doing too much VBA or having activeX components.



# [Upcoming functions]
many... :) 
if you want a specific function email or leave a comment :)



Copyright © 2018 Krish
