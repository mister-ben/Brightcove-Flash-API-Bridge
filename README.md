Flash Player API Bridge
=======================

This plugin exposes some methods of the Flash-only Player API to javscript. The intended use is for when you want to use the Smart Player API in the page, but need to access some fucntionality that is only implemented in the Flash-only player API.

##Usage

Add the swf plugin to the player as a plugin in player settings or as a module in the BEML template. Remember to have a crossdomain policy file on your server to enable Flash to load the plugin

The implemented Flash-only player API methods can be accessed from the swf object on the page. For instance, to initially reduce the player volume:

    <object id="myExperience123456789" class="BrightcoveExperience">
    ...
      <param name="inlcudeAPI" value="true" />
      <param name="templateReadyhandler" value="onReady" />
    </object>

    <script>
    function onReady(event) {
      var player = brightcove.getExperience(event.target.experience.id);
      //... Smart Player API code...
      var fapiPlayer = document.getElementById(event.target.experience.id);
      fapiPlayer.fapiSetVolume(0.5);
     }
     </script>
     
Events will be triggered if a `window.fapiEvent` function exists at the point the player is created.

    <script>
    function fapiEvent(id,event) {
      console.log ("Player " + id + " dispatched event " + event.type);
    }
    </script>

###Methods implemented

* `fapiSetVolume` - [VideoPlayerModule.setVolume(volume:Number):void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoPlayerModule.html#setVolume%28%29)
* `fapiGetVolume` - [VideoPlayerModule.getVolume():Number](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoPlayerModule.html#getVolume%28%29)
* `fapiMute` - [VideoPlayerModule.mute(mute:Boolean):void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoPlayerModule.html#mute%28%29)
* `fapiIsMuted` - [VideoPlayerModule.isMuted():Boolean](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoPlayerModule.html#getVolume%28%29)
* `fapiSetBitRateRange` - [VideoPlayerModule.setBitRateRange(min:int, max:Number):Object](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoPlayerModule.html#setBitRateRange%28%29)
* `fapiStopAd` - [AdvertisingModule.stopAd():void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/AdvertisingModule.html#stopAd%28%29)
* `fapiSetEmbedCode` - [SocialModule.setLink(linkURL:String):void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/SocialModule.html#setLink%28%29)
* `fapiSetLink` - [SocialModule.setEmbedCode(code:String):void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/SocialModule.html#setEmbedCode%28%29)
* `fapiRemoveUserMessage` - [VideoModule.removeUserMessage():void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/VideoModule.html#removeUserMessage%28%29)
* `fapiCloseMenuPage` - [MenuModule.closeMenuPage():void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/MenuModule.html#closeMenuPage%28%29)
* `fapiRemoveOverlayMenu` - [MenuModule.removeOverlayMenu():void](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/MenuModule.html#removeOverlayMenu%28%29)
* `fapiIsOverlayMenuShowing` - [MenuModule.isOverlayMenuShowing():Boolean](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/MenuModule.html#isOverlayMenuShowing%28%29)
* `fapiIsMenuPageShowing` - [MenuModule.isMenuPageShowing():Boolean](http://docs.brightcove.com/en/video-cloud/player/com/brightcove/api/modules/MenuModule.html#isMenuPageShowing%28%29)

###Events implemented

* ExperienceEvent.ENTER_FULLSCREEN
* ExperienceEvent.EXIT_FULLSCREEN
* MediaEvent.BUFFER_BEGIN
* MediaEvent.BUFFER_COMPLETE
* MediaEvent.MUTE_CHANGE
* MediaEvent.RENDITION_CHANGE_COMPLETE
* MediaEvent.RENDITION_CHANGE_REQUEST
* MediaEvent.VOLUME_CHANGE