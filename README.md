# libtorrent adds support for the WebTorrent protocol

The vision of the WebTorrent project is to extend the BitTorrent protocol so that it becomes more web-friendly, allowing any browser to become a peer in the torrent network.

That’s why I’m super excited that libtorrent – the engine that powers many of the most popular torrent clients including qBittorrent, Deluge, and many more – has added support for the WebTorrent protocol.

WebTorrent support in libtorrent opens the door for many more torrent clients to connect to browser peers. Browser peers (which must use WebRTC) will now be able to access a huge trove of torrents currently only available to TCP/UDP peers.

The WebTorrent protocol allows peers to connect over WebRTC in addition to the widely supported TCP and UDP transports. In fact, UDP support itself was added to the BitTorrent protocol in a protocol extension (see the μTP protocol) and now UDP is the primary transport used by BitTorrent clients.

With this big news, we’re one step closer to the vision of browser-based torrents. One day soon, you’ll be able to navigate your web browser to any site with a JavaScript torrent implmentation embedded – like Instant.io or βTorrent – and be able to torrent anything available in the normal torrent network.

While desktop torrent clients aren’t going anywhere anytime soon, now the web browser will become a viable alternative to an installed torrent client. This is huge for less-technical users, users who can’t install native apps, or users who just feel safer using a website. WebTorrent offers more options and more ways to connect.
![image](https://user-images.githubusercontent.com/63551022/186521458-2174931d-29d6-4de9-85df-2430f90ef969.png)
https://webtorrent.io/faq
Torrent clients that can speak to both traditional TCP/UDP peers (orange) as well as the WebRTC-only browser peers (blue) are called “hybrid” peers (green). The libtorrent support for WebTorrent means that there are about to be a lot more hybrid peers!

The wider WebTorrent world
WebTorrent is more than a protocol extension to BitTorrent.

We build a popular desktop torrent client, WebTorrent Desktop, which supports powerful features like instant video streaming.
![image](https://user-images.githubusercontent.com/63551022/186521617-d1a279c5-d947-4300-8370-b2ed0759a61c.png)
We also build a webtorrent JavaScript package which implements the full BitTorrent/WebTorrent protocol in JavaScript, the language of the web. This implementation uses TCP, UDP, and/or WebRTC for peer-to-peer transport in any environment – whether Node.js (TCP/UDP), Electron (TCP/UDP/WebRTC), or the web browser (WebRTC). In the browser, the webtorrent package uses WebRTC which doesn’t require a browser plugin, extension, or any kind of installation to work.

If you’re building a website and want to fetch files from a torrent, you can use webtorrent to do that directly client-side, in a decentralized manner. Our recently released WebTorrent Workshop is helpful for getting started and teaches you how to download and stream a torrent into an HTML page in just 10 lines of code.

const client = new WebTorrent()

const torrentId = 'https://webtorrent.io/torrents/sintel.torrent'
const torrent = client.add(torrentId)

torrent.on('ready', () => {
  // Torrents can contain many files. Let's use the .mp4 file
  const file = torrent.files.find(file => file.name.endsWith('.mp4'))

  // Display the file by adding it to the DOM
  file.appendTo('body', { autoplay: true, muted: true })
})

See this code in action on CodePen.

Also, I want to remind everyone that WebTorrent has been built into the popular, privacy-focused Brave browser since 2016. Just click on .torrent files or magnet links and they’ll magically work. And that’s all powered by WebTorrent.
![image](https://user-images.githubusercontent.com/63551022/186521913-164e639d-450e-4a9d-93f6-befbdc60b71b.png)
With support for the WebTorrent protocol in libtorrent-based torrent clients, you’ll soon be able to connect to more peers which means faster, more reliable downloads.

The future is bright for WebTorrent!

(If you liked this, you might like Freedom of Speech on the Internet.)
