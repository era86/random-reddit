# Random Reddit [![npm](https://img.shields.io/npm/v/random-reddit?style=flat-square)](https://www.npmjs.com/package/random-reddit)

The class with functions that get random posts or images from specified subreddit.

## Usage

### Installation
1. `npm install random-reddit`
2. Create a `RandomReddit` instance.
3. Use `getPost()` or `getImage()` from the instance.  

### Example

```js
const { RandomReddit } = require('random-reddit')

const reddit = new RandomReddit();

function async getPost() {
  const post = await reddit.getPost('memes')
  console.log(post) // returns the reddit post object
  // ...
}

function async getImage() {
  const image = await reddit.getImage('memes')
  console.log(image) // e.g. https://i.redd.it/sri113wns9351.png
}
```

#### `getPost()`

```ts
RandomReddit.getPost(subreddit: string | string[]): Promise
```
Returns the whole Reddit post.

**Arguments**:
- `subreddit` (`string | string[]`) - a subreddit to fetch the post from. You can also specify an array of subreddit names

#### `getImage()`

```ts
RandomReddit.getImage(subreddit: string | string[], retryLimit?: number): Promise
```
Returns the random post's image URL. If it won't find one - the request will be sent again until the `retryLimit` is reached.

**Arguments**:
- `subreddit` (`string | string[]`) - a subreddit to fetch the image from. You can also specify an array of subreddit names
- `retryLimit` (`number`) - *optional*. Request retry limit. Default is 10.

#### `getPostById()`

```ts
RandomReddit.getPostById(id: string, subreddit: string): Promise
```
Returns specific post with given id (ID36) and specified subreddit.

**Arguments**:
- `id` (`string`) - post's id
- `subreddit` (`string`) - a subreddit to fetch the post from