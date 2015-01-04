YoutubePlayer.react
===================

React component for rendering and controlling an embedded Youtube player.

The component is written in JavaScript Harmony (ES6), so you need to use the harmony flag with jsx (read about it [here](http://facebook.github.io/react/blog/2014/07/17/react-v0.11.html#jsx)). It's using the Youtube's Iframe Player API which renders the player in an iframe.

**_The component is built and tested with React v0.12.1_**

### Example:
```js
var Example = React.createClass({
  render: function() {
    return (
      <YoutubePlayer
        ref="player"
        // This is the ID of the video: https://www.youtube.com/watch?v=XxVg_s8xAms
        videoID="XxVg_s8xAms"
        width={640}
        height={390}
        // Called when the user selects a video from the recommendations at the end
        onSwitchVideo={this._onSwitch}
        // Called when the video starts playing
        onPlay={this._onPlay}
        // Called when the video is paused
        onPause={this._onPause}
        // Called when the end of the video is reached
        onEnd={this._onEnd}
      />
    );
  },
  
  _onSwitch: function(videoID) {
    console.log('The user switched to the video:', videoID);
  },
  
  _onPlay: function() {
    console.log('The video is now playing');
  },
  
  _onPause: function() {
    console.log('The video is now paused');
  },
  
  _onEnd: function() {
    console.log('The video end is reached');
    // Let's do something fun :)
    // When the end is reached, let's play the video again, muted!
    this.refs.player.play();
    this.refs.player.mute();
  },
});
```


### Missing features/future work
- Provide some examples
- Support playlists
- Allow access to video information e.g. title, duration, url, 
- Report buffering progress through callbacks
- Support other options e.g. start-end ranges, playback quality, etc
- Support more APIs e.g. get/set volume, set size, get current time, etc


### More information
- React: http://facebook.github.io/react/
- Youtube Player API: https://developers.google.com/youtube/iframe_api_reference
