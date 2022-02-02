# Dailymotion Video Tiles

Dailymotion Video Tiles has two main components i.e., 
- Feature Video Component : A top-of-the-page video with previews
- Playlist Components : A list of videos/channels as carousel slideshow

The playlist components can be customised based on a list of [parameters](#parameters-available). 

To use Dailymotion Video Tiles you should create a player first through your [Partner HQ](https://www.dailymotion.com/partner/embed/players) and get the `{PLAYER_ID}` from the UI once the template is created.


### Start Embedding

You need to do 2 things to embed the Dailymotion Video Tiles.

1. Add the [script](https://srvr.dmvs-apac.com/dm-video-tiles/dm-video-tiles.min.js) at the very bottom before `body` end in your website
```html
<script src="https://srvr.dmvs-apac.com/dm-video-tiles/dm-video-tiles.min.js"></script>
```
3. Add `<div class="dm-video-tiles" `[{PARAMS}](#parameters-available)`></div>` in your target location within the body content.


### Standard Embed Tag

```html
<div class="dm-video-tiles"
    type="anchor"
    expandType="popup"
    playerId="{PLAYER_ID}"
    owners="{YOUR_CHANNEL_NAME}"
    featureVideo="{VIDEO_ID}"
    highlightVideos = "{VIDEO_ID},{VIDEO_ID},{VIDEO_ID},{VIDEO_ID},{VIDEO_ID}"
    playlistIds="{PLAYLIST_ID},{PLAYLIST_ID}"
    topicVideos="Sports,Entertainment"
    channels="{YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME}" 
>
</div>
```

### Parameters Available

| Name | Type | Description |
| :---: | :---: | --- |
| owners <br /> `Mandatory` | string | You need to put the username of the channels from which the script will search content. If your channel name URL is www.dailymotion.com/channelABC then your username is channelABC. This is case sensitive, meaning channelABC is not the same as Channelabc. To put more than 1 you can separate by ","
| playerId <br /> `Mandatory` | string | You can get `{PLAYER_ID}` from [Dailymotion partner HQ](https://www.dailymotion.com/partner/embed/players) in the player tab, inside the embed menu. |
| featureVideo <br /> `Mandatory` | string | **Featured Video Component :** Add `{VIDEO_XID}` to feature as your top Video Tile|
| highlightVideos | string | **Playlist Components :** To create a playlist based on `{VIDEO_XID}`. Please use `","` separator while adding video xids.|
| playlistIds | string | **Playlist Components :** To create playlist based on `{PLAYLIST_ID}`. Learn more on [how to create, sort, feed and embed playlist](https://faq.dailymotion.com/hc/en-us/sections/360003674799-Playlist).  Please use `","` separator to use more than one `{PLAYLIST_ID}` for your tiles. |
| topicVideos | string | **Playlist Components :** To create a tile based on topic. By using [video-tags-filter API](https://developer.dailymotion.com/api/#video-tags-filter), a playlist of video assets relevant to the topic chosen will be created. Please use `","` separator to use more than one topic.  |
| channels | string | **list Components :** To create a list of dailymotion channels as a carousel slideshow. On click, it will redirect to the corresponding Dailymotion channel page. Please use `","` separator to feature more than one channel.  |
| type | string | Set to `"anchor"` which will show *Featured Video Component* only. After you click the anchor, Dailymotion video tiles will expand and the *Playlist Components* will then render. To learn more, check the [different embed options](#different-embed-options-) |
| expandLink | string | You can add a page url that ties to anchor. Clicking on the anchor will open that page in another tab. To learn more, check the [different embed options](#different-embed-options) |
| expandType | string | Set "popup" to expand Dailymotion video tiles as a popup instead after clicking on the anchor link. To learn more, check the [different embed options](#different-embed-options) |

### Different Embed options :
By default Dailymotion Video Tiles expand inline which will horizontally fill the width of its parent element and expand vertically based on how much content you added to your Dailymotion Video Tiles. By using `Anchor`, Dailymotion Video Tiles loads *Feature Video Component* only as an animated preview . To see the expanded video tiles, Anchor can be linked to another page or a popup in same page. Check below to see the embed options.
    
**Anchor with expanded popup :** When Anchor is clicked the expanded video tiles will open ad popup in same page.
Sample Code: 
```html
<div class="dm-video-tiles"
  type="anchor"
  expandType="popup"
  playerId="x6wze"
  owners="oneindia"
  featureVideo="x85xu4t"
  highlightVideos = "x85xvf0,x85xurb,x85xtvb,x85xton,x85xsd5,x85xkqr,x85xjt5"
  playlistIds="x661nk,x661nh"
  topicVideos="Sports,Entertainment"
  channels="filmibeat,oneindiahindi,boldsky,oneindiatamil,gizbot,oneindiatelugu,drivespark,oneindiamalayalam" 
>
</div>
```
> Sample example : [Anchor Embed - Popup expand](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_popup.html)

**Anchor with expanded inline :** When Anchor is clicked, the expanded video tiles will open inline and it will grow vertically based on the content of the video tiles.
Sample Code: 
```html
<div class="dm-video-tiles"
  type="anchor"
  playerId="x6wze"
  owners="oneindia"
  featureVideo="x85xu4t"
  highlightVideos = "x85xvf0,x85xurb,x85xtvb,x85xton,x85xsd5,x85xkqr,x85xjt5"
  playlistIds="x661nk,x661nh"
  topicVideos="Sports,Entertainment"
  channels="filmibeat,oneindiahindi,boldsky,oneindiatamil,gizbot,oneindiatelugu,drivespark,oneindiamalayalam" 
>
</div>
```
> Sample example : [Anchor Embed - Inline expand](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_inline.html)

**Anchor with expand link :** When Anchor is clicked, it will open the link in another tab where you can have full view of the video tiles.
Sample Code: 
```html
<div class="dm-video-tiles"
  type="anchor"
  expandLink="fullpage.html"
  owners="oneindia"
  featureVideo="x85xu4t">
</div>
```
> Sample example : [Anchor Embed - Expand link](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_link.html)

**Inline embed :** Dailymotion Video Tiles will be expanded inline which will grow vertically based on the content of the video tiles
Sample Code: 
```html
<div class="dm-video-tiles"
  owners="oneindia"
  playerId="x6wze"
  featureVideo="x85xu4t"
  highlightVideos = "x85xvf0,x85xurb,x85xtvb,x85xton,x85xsd5,x85xkqr,x85xjt5"
  playlistIds="x661nk,x661nh"
  topicVideos="Sports,Entertainment"
  channels="filmibeat,oneindiahindi,boldsky,oneindiatamil,gizbot,oneindiatelugu,drivespark,oneindiamalayalam"
>
</div>
```
> Sample example : [Inline Embed](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/inline_embed.html)

### Example Links
- [Anchor Embed - Expand link](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_link.html)
- [Anchor Embed - Popup expand](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_popup.html)
- [Anchor Embed - Inline expand](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/anchor_expand_inline.html)
- [Inline Embed](https://dmvs-apac.github.io/dm-video-tiles-doc/lab/inline_embed.html)
