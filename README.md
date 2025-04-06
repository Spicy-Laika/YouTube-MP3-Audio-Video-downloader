![Screenshot](https://12388101.xyz/fls/image.jpg)

# YouTube MP3 Audio Video downloader
Functionality to download YouTube videos and convert them into audio MP3 or M4A files

## Detailed Description

The YouTube MP3 Audio Video Downloader enables seamless downloading of YouTube videos and conversion into audio or video files in various formats. Whether you need an MP3 for a playlist this provides a fast and reliable solution. 

### Features:
- **Audio Extraction**: Convert YouTube videos into high-quality audio files (MP3 or M4A).
- **Custom Quality Options**: Select desired quality levels for both video and audio.
- **Fast Processing**: Optimized for quick responses and efficient processing.
- **Ease of Integration**: Simple endpoints and clear documentation for quick implementation.

### Use Cases:
- Build a personal content downloader.
- Enable audio-only playback for YouTube videos in your app.
- Create offline music playlists.

### Supported Formats:
- **Audio**: MP3, M4A


[Try the API now and get instant results](https://api999.short.gy/QiWJS8)

How to use? Easy!
-----------
The request returns a ready mp3 or m4a file immediately. You just need to save the response to the request as a file.

Shell
```
curl -X GET "https://youtube-mp3-audio-video-downloader.p.rapidapi.com/download-mp3/R1F7nAomdn8" \
-H "x-rapidapi-host: youtube-mp3-audio-video-downloader.p.rapidapi.com" \
-H "x-rapidapi-key: *your_rapid_key*" \
-o audio.mp3 
```
this code save audio from Youtube video to audio.mp3

Details
-----------

**Recommended Format:**
Use M4A format for the fastest download, especially for videos longer than 1 hour. For best audio quality, please, use MP3.

**MP3 Format:**
MP3 downloads are slower due to server-side conversion.
You can specify MP3 quality using the **quality** parameter:
"low" "mid" "high".

Methods
-----------
### **Download audio M4A - `/download-m4a/{videoId}`**

The API returns the best available audio quality. 

PHP
```
&lt;?php
$ch = curl_init("https://youtube-mp3-audio-video-downloader.p.rapidapi.com/download-m4a/R1F7nAomdn8");
curl_setopt_array($ch, [
    CURLOPT_HTTPHEADER =&gt; [
        "x-rapidapi-host: youtube-mp3-audio-video-downloader.p.rapidapi.com",
        "x-rapidapi-key: YOUR_RAPID_KEY"
    ],
    CURLOPT_RETURNTRANSFER =&gt; true
]);
file_put_contents("audio.m4a", curl_exec($ch));
curl_close($ch);
?&gt;

```
JS
```
const axios = require("axios");
const fs = require("fs");

axios({
    method: "GET",
    url: "https://youtube-mp3-audio-video-downloader.p.rapidapi.com/download-m4a/R1F7nAomdn8",
    headers: {
        "x-rapidapi-host": "youtube-mp3-audio-video-downloader.p.rapidapi.com",
        "x-rapidapi-key": "YOUR_RAPID_KEY"
    },
    responseType: "stream"
}).then(res =&gt; res.data.pipe(fs.createWriteStream("audio.m4a")));
```


### **Download audio MP3 - `/download-mp3/{videoId}`**
You can specify the quality of MP3 using the "quality" parameter with values "low", "mid", and "high". Due to RapidAPI’s request size limit of 50 MB and response time constraint of 150 seconds, MP3s longer than 20 minutes may experience a reduction in quality to meet these requirements.

PHP
```
&lt;?php
$ch = curl_init("https://youtube-mp3-audio-video-downloader.p.rapidapi.com/download-mp3/R1F7nAomdn8");
curl_setopt_array($ch, [
    CURLOPT_HTTPHEADER =&gt; [
        "x-rapidapi-host: youtube-mp3-audio-video-downloader.p.rapidapi.com",
        "x-rapidapi-key: YOUR_RAPID_KEY"
    ],
    CURLOPT_RETURNTRANSFER =&gt; true
]);
file_put_contents("audio.mp3", curl_exec($ch));
curl_close($ch);
?&gt;

```
JS
```
const axios = require("axios");
const fs = require("fs");

axios({
    method: "GET",
    url: "https://youtube-mp3-audio-video-downloader.p.rapidapi.com/download-mp3/R1F7nAomdn8",
    headers: {
        "x-rapidapi-host": "youtube-mp3-audio-video-downloader.p.rapidapi.com",
        "x-rapidapi-key": "YOUR_RAPID_KEY"
    },
    responseType: "stream"
}).then(res =&gt; res.data.pipe(fs.createWriteStream("audio.mp3")));
```

### **Get Direct URL For Download M4A file (FASTEST) - `/get_m4a_download_link/{videoId}`**

The method takes only one parameter - videoId. And returns audio in m4a format in the best quality available for download. The file is available for download immediately.

Example:

``
{"file":"https:\/\/url.com\/dl_1onFIVvT9ro-9f48612b435701947a399ce647e66754823.m4a","comment":"The file is ready for download. The file will be available for download only 10 minutes"}
``

### **Get Direct URL For Download Mp3 file  - `/get_mp3_download_link/{videoId}`**

The method takes only one parameter - videoId.

The download link immediately returns a 404 error, within 20-300 seconds (depending on the length of the video and the server load). And only then the file will be available for download. This time is needed to download and process the file.

``
{"file":"https:\/\/url.com\/dl_1onFIVvT9ro-9f48612b435701947a399ce647e66754692.mp3","comment":"The file will soon be ready (from 20 to 300 seconds). Until it is ready, attempting to access it will return a 404 error. The file will be available for download only 10 minutes"}
``


### **Get Video Info - `/get-video-info/{videoId}`**

**title**

Description: The title of the video.

*Example value: "How to create an NFT collection | Thirdweb".*

**description**

Description: The video description, including text information and links.

*Example value: "In this video I show you how to create an NFT collection using Thirdweb. You'll learn how to use Thirdweb's no-code web app to create an ERC-721 smart contract for your NFT...".*

**author**

Description: The author of the video.
*Example value: "Sean Watase".*

**lengthSeconds**

Description: The duration of the video in seconds.



**viewCount**

Description: The number of views for the video.

**keywords**

Description: A list of keywords related to the video.

*Example value: ["thirdweb nft", "erc721 smart contract", "how to make money with nfts"].*

**isLiveContent**

Description: Indicates whether the video is a live stream.

**thumbnail**

Description: A list of video thumbnail images with their resolutions.
Example value:

```
[
  {
    "url": "https://i.ytimg.com/vi/DSffICxyj3A/maxresdefault.jpg",
    "width": 1280,
    "height": 720
  }
]
```

**embed.iframeUrl**

Description: URL for embedding the video in an iframe.

*Example value: "https://www.youtube.com/embed/DSffICxyj3A".*

**embed.width and embed.height**

Description: The width and height of the embedded video.

**ownerProfileUrl**

Description: The profile URL of the video owner.
Example value: "http://www.youtube.com/@SeanWatase".

**externalChannelId**

Description: The external ID of the channel.
Example value: "UChjGu9jkMSz_A2qQV1G-Y9w".

**isFamilySafe**

Description: Indicates whether the video is family-friendly.

**availableCountries**

Description: A list of countries where the video is available.
Example value: ["US", "GB", "CA", "AU"].

**category**

Description: The category of the video.
*Example value: "Science & Technology".*

**publishDate and uploadDate**

Description: The publication and upload dates of the video.
*Example values:
publishDate: "2022-10-14T11:51:29-07:00".
uploadDate: "2022-10-14T11:51:29-07:00".*

**isUnlisted**
Description: Indicates whether the video is unlisted.

---
### Possible errors and their fixes!

#### Error 404
Server response 404 - when the specified video is not found. This may be due to regional restrictions on the video and the server's inability to load it.

#### Error 504

A very common error with the "Download Audio MP3 Format" method if the video is long - (if the video is longer than 1-2 hours) and a connection timeout occurs (180 seconds is a rapidapi limitation). Due to rapidapi limitations, enhanced audio conversion and a decrease in audio quality are required and sometimes the server does not have time to process the request.

There are two ways out of this situation: use the "Download Audio M4A" method (it is processed much faster) or use faster methods "/get-m4a-download-link/{videoId}" 

---

 [See the API in action – test it instantly here ](https://api999.short.gy/QiWJS8)

 ---

**Feel free to write to me with any questions not listed in the documentation! :)**

#### Telegram Support: 

https://t.me/+Zlto9kxqYjthYTQy
