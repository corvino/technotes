### Configuring and Scripting lldb

##### command alias
command alias is limited; variables can only be passed to whole command arguments. The command alias documentations describes this as: "Note: the positional arguments must substitute as whole words in the resultant
    command..." The workaround is using command regex, which allows for sed-style-match-and-replace values to be specified.

Thus, instead of:

```
command alias pod expression -O -- [[NSString alloc] initWithData:%1 encoding:4]
```

we do:

```
command regex pod 's/^(.+)$/expression -O -- [[NSString alloc] initWithData:%1 encoding:4]/'
```

While not as readable, this gets the job done.

References: http://stackoverflow.com/questions/7690181/i-cant-get-this-simple-lldb-alias-to-work/12195214#12195214

##### Reveal Integration Trickiness

To minimalize project-file modications need to run reveal, the following post is handy: [Integrating Reveal without modifying your Xcode project](http://blog.ittybittyapps.com/blog/2013/11/07/integrating-reveal-without-modifying-your-xcode-project/).

The gist is the following aliases:

>```
command alias reveal_load_sim expr (void*)dlopen("/Applications/Reveal.app/Contents/SharedSupport/iOS-Libraries/libReveal.dylib", 0x2);
command alias reveal_load_dev expr (void*)dlopen([(NSString*)[(NSBundle*)[NSBundle mainBundle] pathForResource:@"libReveal" ofType:@"dylib"] cStringUsingEncoding:0x4], 0x2);
command alias reveal_start expr (void)[(NSNotificationCenter*)[NSNotificationCenter defaultCenter] postNotificationName:@"IBARevealRequestStart" object:nil];
command alias reveal_stop expr (void)[(NSNotificationCenter*)[NSNotificationCenter defaultCenter] postNotificationName:@"IBARevealRequestStop" object:nil];
```

>* ```reveal_load_sim``` – This alias only works when running your app on the iOS Simulator. It loads the libReveal.dylib from the Reveal application bundle (assuming you put Reveal in your system’s Applications folder). If you have Reveal elsewhere change the alias to reflect this.
>* ```reveal_load_dev``` – This alias works when running your app on device or in the iOS Simulator. It however assumes you have added the libReveal.dylib bundled with Reveal to your application’s Copy Resources build phase. (Make sure it is not in your Link Binary with Libraries build phase. Yes, I was fibbing a little about not having to modify your Xcode project. Sorry.
>* ```reveal_start``` – This alias posts a notification via NSNotificationCenter to start the Reveal server.
>* ```reveal_stop``` – This alias posts a notification via NSNotificationCenter to stop the Reveal server.
