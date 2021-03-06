# hackd

A Hacker News React Native powered iOS application. Built to learn React Native and Redux.

Currently a work in progress.

### Features

Features that aren't checked below are yet to be implemented. If you want to implement them, please create a pull request!

##### Main

- [x] Browse anonymously or login
- [x] 6 feeds to choose from:
	- Top
	- New
	- Best
	- Ask
	- Show
	- Jobs
- The user can:
	- [x] Share posts
	- [ ] Search, filter and view posts (stories, show, ask), comments, polls and users
	- [x] Read articles in app with Safari View Controller
	- [x] Read, collapse and expand comments
- If logged in, the user can also:
	- [x] Upvote posts
	- [x] Upvote comments
	- [x] Unvote comments
	- [ ] Comment
	- [ ] Submit a post
	- [x] Save a post
	- [ ] Add a post to their offline reading section
	- [ ] View their recently viewed articles
	- [ ] View their upvoted posts
	- [x] View their own profile
- [x] Users can login/logout of multiple different accounts without losing their saved/upvoted/offline/viewed posts

##### Other

- [x] Haptic feedback for common actions
- [x] 3D touch actions and preview (peek and pop)<sup><a href="#1">1</a></sup>
- [x] Themable app colors (i.e. comments, navigation, buttons, tabbar)
- [x] Swipe horizontally to upvote or save
- [x] Infinite scroll

### TODO

- [ ] Add features not implemented above
- [x] Fix and improve comment fetching. 
	- Comments are fetched recursively due to Hacker News's API design, then flattened into an array where each reply is the next item in the array. This isn't a good solution beacuse the user has to wait for all the comments to be loaded before they can see any (`Promise.all()`).
	- To fix this, each top comment and its replies should be fetched individually, appended to an array and the component will re render with the new comment added. The user will also be able to view comments almost immediately while others load.
- [ ] Add caching for comments (older than 10 minutes), and posts. If post/comment requested again, check if in cache, if so load from cache.

### Run Locally

```bash
# Clone hackd
$ git clone https://github.com/lukakerr/hackd.git

# Change directories
$ cd hackd

# Install dependencies
$ npm install

# Link native libraries
$ npm run link

# Run the app
$ npm run start
# Or for iPhone X
$ npm run start:x
```

### Test

Jest is used for testing. To test, run:

```bash
$ npm run test
```

### Design

Inspired by [Apollo App](https://apolloapp.io), I tried to design hackd around an iOS centric theme.

The comments design in hackd is based off a stripped down version of Apollo's comments.

Hackd also supports font scaling for readers who want smaller or larger text.

I've tried to add and support as many native API's as possible such as haptic feedback and 3D touch. Although many new API's aren't available in the React Native environment yet. 

### Screenshots

<p align="center">
  <img src="https://i.imgur.com/h7b8sfc.png" width="275" alt="hackd1">
  <img src="https://i.imgur.com/w0WAiUJ.png" width="275" alt="hackd2">
  <img src="https://i.imgur.com/ktXZzcT.png" width="275" alt="hackd3">
</p>

<p align="center">
	<img src="https://i.imgur.com/A7CXz6f.png" width="275" alt="hackd4">
  <img src="https://i.imgur.com/np0pc3S.png" width="275" alt="hackd5">
  <img src="https://i.imgur.com/w1ZSiOR.png" width="275" alt="hackd6">
</p>

<p align="center">
  <img src="https://i.imgur.com/peOz8Ix.png" width="275" alt="hackd7">
  <img src="https://i.imgur.com/MciVZK1.png" width="275" alt="hackd8">
  <img src="https://i.imgur.com/PbuheBP.png" width="275" alt="hackd9">
</p>

<br><br>

<sup id="1">1</sup> 3D touch is only available on supported devices. Currently only Wix's [react-native-navigation](https://github.com/wix/react-native-navigation) supports it, although there is a [relatively major bug](https://github.com/wix/react-native-navigation/issues/2445) that hasn't been fixed yet. This bug is present in Hackd.