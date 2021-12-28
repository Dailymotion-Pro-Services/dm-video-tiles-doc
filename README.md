# Dailymotion Video Tiles

Dailymotion Video Tiles is composed with two main components i.e., 
- Feature Video Component : A top-of-the-page video wuth previews
- Playlist Components : A list of videos/channels as carousel slideshow

The playlist components can be different types based on [parameters](#parameters-available). 

To use Dailymotion Video Tiles you should create a player first through [Partner HQ](https://www.dailymotion.com/partner/x1wzpns/embed/players) and get the `{PLAYER_ID}`.


### Start Embedding

You need to do 2 things to embed the Dailymotion Video Tiles.

1. Put the [script](https://staging.dmvs-apac.com/dm-video-tiles/dm-video-tiles.js) at the very bottom before `body` end in your website
```js
<script src="https://staging.dmvs-apac.com/dm-video-tiles/dm-video-tiles.js"></script>
```
3. Add `<div class="dm-video-tiles" `[{PARAMS}](#parameters-available)`></div>` in your target of body content.


### Standard Embed Tag

```html
<div class="dm-story" playlistId="{PLAYLIST_ID}" playerId="{PLAYER_ID}" style="height: 230px;"></div>
<div class="dm-video-tiles"
    anchor="true"
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
|
| PlayerId <br /> `Mandatory` | string | You can get `{PLAYER_ID}` from [Dailymotion partner HQ](https://www.dailymotion.com/partner/x1wzpns/embed/players) in the player tab, inside the embed menu. |
| featureVideo <br /> `Mandatory` | string | **Feature Video Component :** Add video xid to feature Dailymotion Video Tiles|
| highlightVideos | string | **Playlist Components :** To create playlist based video xids. Please use `","` separator while adding video xids.|
| playlistIds | string | **Playlist Components :** To create playlist based on `{PLAYLIST_ID}`. Learn more on [how to create, sort, feed and embed playlist](https://faq.dailymotion.com/hc/en-us/sections/360003674799-Playlist).  Please use `","` separator to use more than one `{PLAYLIST_ID}`. |
| topicVideos | string | **Playlist Components :** To create based on topic. By using [video-tags-filter API](https://developer.dailymotion.com/api/#video-tags-filter), playlist will be created. Please use `","` separator to use more than one topic.  |
| channels | string | **list Components :** To create list of channels as carousel slideshow. On click of this list it will redirect to Dailymotion channel's page. Please use `","` separator to use more than one topic.  |
| anchor | boolean | Set true for anchor which will show *Feature Video Component* only. After you click the anchor, Dailymotion video tiles will expand and the rest *Playlist Components* will render. To know more check [Different Embed options]() |
| expandLink | string | You can add a page url that ties to anchor. Clicking on the anchor will open that page in another tab. To know more check [Different Embed options]() |
| expandType | string | Set "popup" to expand Dailymotion video tiles as popup after clicking on the anchor link. To know more check [Different Embed options]() |

### Different Embed options :




### Example Links
- [Anchor Embed - Expand link](https://staging.dmvs-apac.com/dm-video-tiles/lab/anchor_expand_link.html)
- [Anchor Embed - Popup expand](https://staging.dmvs-apac.com/dm-video-tiles/lab/anchor_expand_popup.html)
- [Anchor Embed - Inline expand](https://staging.dmvs-apac.com/dm-video-tiles/lab/anchor_expand_inline.html)
- [Inline Embed](https://staging.dmvs-apac.com/dm-video-tiles/lab/inline_embed.html