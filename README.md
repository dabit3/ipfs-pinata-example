## An example of how to pin a file to IPFS with Pinata in a JavaScript app

If you're like me and had no luck finding any examples or code to show how this is done, then hopefully this will help you.

### Pinning a string

```javascript
async function save(e) {
  let ipfs = await IPFS.create({
    url: "https://api.pinata.cloud/psa",
    repo: 'file-path' + `${Math.random()}`
  })
  const { cid } = await ipfs.add('hello world')
  const url = `https://gateway.pinata.cloud/ipfs/${cid.string}`
  console.log(url)
}
```

### Pinning a file

```javascript
async function onChange(e) {
  const file = e.target.files[0]
  let ipfs = await IPFS.create({
    url: "https://api.pinata.cloud/psa",
    repo: 'file-path' + `${Math.random()}`
  })
  const { cid } = await ipfs.add(file)
  const url = `https://gateway.pinata.cloud/ipfs/${cid.string}`
  console.log(url)
}
```