# Dailymotion Video Tiles

Dailymotion Video Tiles is composed of different types of `tiles` / `cards`. It creates a carousel slideshow for a list of videos, playlists, and channels. All the lists are added vertically throughout the page creating a video-hub alike experience. 

Based on UI and functionalities, There are mainly three types of lists.

**List of video-cards :** A list of videos mainly derived from `playlistId` / `videoIds` or through [DATA-API](https://developers.dailymotion.com/api/#video).

**List of playlist-cards:** A list of playlists mainly derived from `playlistIds` or through [DATA-API](https://developers.dailymotion.com/api/#playlist).

**List of channel-cards:**  list of channels mainly derived from `channelIds` or through [DATA-API](https://developers.dailymotion.com/api/#user).

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
    playerId="{PLAYER_ID}"
    owners="{YOUR_CHANNEL_NAME}"
    logoImg="{YOUR_LOGO_IMAGE_URL}"

    data-list-1 = "=video_playlist({PLAYLIST_ID})" 
    data-list-2 = "{Customized Title}=video_ids({VIDEO_ID},{VIDEO_ID},{VIDEO_ID},{VIDEO_ID},{VIDEO_ID})"
    data-list-3 = "{Customized Title}=video_api(sort=trending)"

    data-list-4 = "{Customized Title}=playlist_ids({PLAYLIST_ID},{PLAYLIST_ID},{PLAYLIST_ID},{PLAYLIST_ID})"
    data-list-5 = "{Customized Title}=playlist_api(sort=recent)"

    data-list-6 = "{Customized Title}=channel_ids({YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME},{YOUR_CHANNEL_NAME})"
    data-list-7 = "{Customized Title}=channel_api(sort=recent)"
>
</div>
```

### Parameters Available

| Name | Type | Description |
| :---: | :---: | --- |
| `owners` <br /> `Mandatory` | string | You need to put the username of the channels from which the script will search content. If your channel name URL is www.dailymotion.com/channelABC then your username is channelABC. This is case sensitive, meaning channelABC is not the same as Channelabc. To put more than 1 you can separate by ","
| `playerId` <br /> `Mandatory` | string | You can get `PLAYER_ID` from [Dailymotion partner HQ](https://www.dailymotion.com/partner/embed/players) in the player tab, inside the embed menu. |
| `logoImg` <br /> `Mandatory` | string | Add your logo image url for header |
| `data-list-{sequence_number}` | string | To add different type list. Ex : `data-list-1`. Check [Embeding different type of list](#embedding-different-type-of-lists)|
| `customHeader` | boolean | Set it `true` to customize the header. Check [Customize Your Header](#customize-your-header)|
| `videoTilesPreview` | boolean | If you are adding preview of you Video Tiles page, set it `true`. [Learn More](#embed-a-preview-of-video-tiles) |
| `videoTilesLink` | string | If you are adding preview of you Video Tiles page, add its `URL`. [Learn More](#embed-a-preview-of-video-tiles)|

### Embedding different type of lists:

Dailymotion Video Tiles provide `data-list-{sequence_number}` parameter to embed different types of lists and their sequence order. Also, you can add custom `Title`/`Header` to those lists.

1. To embed `List of video-cards`, you can use three ways based on requirements.
    1. With a `PLAYLIST_ID` . Example : 
    `data-list-1 = "=video_playlist(x661nk)"`
    > Learn more on [how to create, sort, feed and embed playlist](https://faq.dailymotion.com/hc/en-us/sections/360003674799-Playlist)
    2. With list of `VIDEO_ID`. Example :
    `data-list-2 = "My Selected videos=video_ids(x85xvf0,x85xurb,x85xtvb)"`
    > You must use `","` separator to add more `{VIDEO_ID}`
    3. With [dailymotion DATA-API](https://developers.dailymotion.com/api/#video). Example :
    `data-list-3 = "My Trending Videos=video_api(sort=trending)"`
    >  You can customized title as here `My Trending Videos`.

2. To embed `List of playlist-cards`, you can use two ways based on requirements.
    1. With list of `PLAYLIST_ID`. Example :
    `data-list-4 = "My playlists=playlist_ids(x661nk,x661nh,x51ill,x51ild)"`
    2. With [dailymotion DATA-API](https://developers.dailymotion.com/api/#playlist). Example :
    `data-list-5 = "Recent Playlist=playlist_api(sort=recent)"`

3. To embed `List of channel-cards`, you can use two ways based on requirements.
    1. With list of `CHANNEL_ID`. Example :
    `data-list-6 = "Test Channels=channel_ids(filmibeat,oneindiahindi,boldsky,oneindiatamil)"`
    2. With [dailymotion DATA-API](https://developers.dailymotion.com/api/#user). Example :
    `data-list-7 = "Recent Channels=channel_api(sort=recent)"`

![Rule](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/view.jpg)

### To Add Category and City :

Dailymotion Video Tiles also provide an option to add categories and cities through `application/json` `script` tag. You must add this `script` tag before main `script` i.e., [dm-video-tiles.min.js](https://srvr.dmvs-apac.com/dm-video-tiles/dm-video-tiles.min.js). Example : 

```html
<script type="application/json" id="dm_video_tiles">
    {
        "category": [
            {
                "name": "News",
                "playlist": "`PLAYLIST_ID`,`PLAYLIST_ID`"
            },
            {
                "name": "Entertainment",
                "playlist": "`PLAYLIST_ID`,`PLAYLIST_ID`"
            }
        ],
        "city": [
            {
                "name": "Hello Pune",
                "playlist": "`PLAYLIST_ID`"
            },
            {
                "name": "Hello Mumbai",
                "playlist": "`PLAYLIST_ID}`"
            },
        ]
    }
</script>
```
For each category, you can map multiple playlists with `PLAYLIST_ID`. For each city, you can map a single playlist with `PLAYLIST_ID`. Like the Example ⇧ .


### Embed a preview of Video Tiles:

Assuming that you have already a `video-hub` page created by Dailymotion video tiles, You can add a preview of the `video-hub` on a different page of your website. The preview will show a snapshot of the `video-hub` which can be clicked to open the `video-hub` in a different tab. Example Embed code:

```html
    <div class="dm-video-tiles"
        playerId="{PLAYER_ID}"
        owners="{YOUR_CHANNEL_NAME}"
        videoTilesPreview="true"
        videoTilesLink="video-hub.html"
        data-list-1 = "=video_playlist(x5nune)" 
    >
    </div>
```
> Just add one `data-list-1` which will be used to show the preview.

### Customize Your Header: 

Dailymotion video tiles create its header with the given `logoImg`, `Category` and `City`. But it can be customized if you set `customHeader` `true`. Adding this param, Dailymotion video tiles will trigger a CustomEvent(`tiles-header-render`) on the `document` after creating a container(`div`) of the header.

The `tiles-header-render` event conveys information and method which can be used to customize the header.

Example code:
```js
    // On header create get info
    document.addEventListener("tiles-header-render",(e)=>{
        let dmTilesObj = e.detail
        /**
         * dmTilesObj = {
         *  headerDom : {Header Dom object}
         *  singleLive : { //If there is one live video
         *                  thumbnail_240_url: string;
                            title: string;
                            id: string;
                            created_time: number;
                            duration: number;
                            url: string;
                            "owner.screenname": string;
                            "owner.username": string;
                            channel: string;
                            onair: boolean;
         *               } or null
            isMobile: {true if its mobile},
            updateUrl : { funtion to route category or city page}
                        (
                            name:string,value:{pageName&playlistId}
                        )

         * }
         */
    })
```
As seen above the code, `dmTilesObj` is an object of information and method. These are

1. **headerDom** : It is container of the header, precisely a `HTMLElement` `div` object.
2. **singleLive** : If there is a single live video currently `onair`, it will be an object of that video's information.
3. **isMobile** : It wil be `true` for mobile.
4. **updateUrl(name:`string`,value:`{pageName&playlistId}`)** : This is the funtion to route the different page.
    1. **name:`string`** : you can set to `category` or `city` to route the category/city page accordingly.
    2. **value:`{pageName&playlistId}`)** : This is a combination of `category`'s/`city`'s name and its playlist.
    Ex:
    ```js
        // for category
        dmTilesObj.updateUrl({
            name: "category",
            value: "News"+"&"+"`PLAYLIST_ID`,`PLAYLIST_ID`,`PLAYLIST_ID`"
        });
        // for city
        dmTilesObj.updateUrl({
            name: "city",
            value: "Hello Pune"+"&"+"`PLAYLIST_ID`"
        });
    ```
> Check the [example links](#example-links) for more details.

### Features : 

1. The first playlist will always be treated as a `Hero playlist` that shows previews of videos from the playlist at the top of the page.
2. If there are `live` videos found on a given channel, Dailymotion video tiles will add that list of `live` videos as the first playlist.
3. If you land the Video-hub page ( created by Video Tiles ) by clicking [Preview Embed](#embed-a-preview-of-video-tiles), the preview playlist will be added as the first playlist.
4. Dailymotion Video Tiles is a single-page application. Some Routes are described below:
    1. Clicking on the `Video Card` will land you video page. The selected video will play and the related playlist will show below the player.
    2. Clicking on the `Playlist Card` will land you Playlist page. The first video of the playlist will show as a preview and the rest videos will show below.
    3. Clicking on the `Channel Card` will land your channel page. All the playlists from that channel will show like video tiles and the first playlist will have a `Hero playlist` UI.

### Example Links :

- [Video Hub](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/fullpage.html)
- [Video Hub- Lokmat](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/lokmat_fullpage.html)
- [Video Hub- Customized Header](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/lokmat_customhead.html)
- [Preview of Video Hub](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/dm_video_tiles_preview.html)
- [Redirect Mechanism](https://dailymotion-pro-services.github.io/dm-video-tiles-doc/lab/redirect_url.html)

<!-- 4. Day-Night Mode is added at the top right corner. -->
