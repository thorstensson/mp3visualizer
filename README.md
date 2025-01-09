![audiocompact](https://github.com/user-attachments/assets/858baef1-026a-4ba9-95f7-7a608855e834)


![Static Badge](https://img.shields.io/badge/Vue-3.5.13-green) 

![Static Badge](https://img.shields.io/badge/Typescript-5.6.3-navy)

![Static Badge](https://img.shields.io/badge/Composition%20API-orange)

# Audio Player - Vue - TS - Web Audio API

Here is the compact version of the mp3 Player that I first posted @ https://github.com/thorstensson/audio-player-vue-ts. Made for the footer, this version measures only 70 pixels tall :zap:

In the code, I have cleaned up my back and forth on semicolons. Next, to clean up the other player.
On the roadmap for both: add info message if no mp3 format or audio context in user's browser.

I won't be adding such failsafes until sometime in February as I now plan get busy with my nex portfolio.
I've decided to build it with Nuxt. Doing a course as well :collision:

## Demo

👉 Netlify: https://compactaudio.netlify.app/

## Run Locally

Clone the project

```bash
  git clone https://github.com/thorstensson/audio-player-vue-ts.git
```

Go to the project directory

```bash
  cd my-project
```

Install dependencies

```bash
  npm install
```

Start the server

```bash
  npm run dev
```
## Suggested S3 config (if you're ok with a public S3 bucket)

For the moment I'm'using S3 for the mp3 files. But play well and don't reuse my S3, if you somehow navigated to here :sunglasses: Mine is set to 0 budget, and I will soon store the tracks elsewhere. 

To be able to play mp3 files from S3 without running into CORS restrictions, you need to configure the S3 bucket and its CORS policy. Login to your AWS, click on your bucket, then click on permissions and scroll down. Then add

### Bucket Policy
```json
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Sid": "AllowPublicRead",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::{YOUR BUCKET NAME HERE}/*"
        }
    ]
}
```

### Cross-origin resource sharing (CORS)
```json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "POST",
            "GET",
            "PUT",
            "DELETE",
            "HEAD"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```
git 
#### The path to your tracks will then be: https://{YOUR BUCKET NAME}.amazonaws.com 

Alternatively, research how to use a signed URL to protect access...

## Roadmap
- [ ] Add messaging if no support for mp3 format | audio context.

## Contributing

Contributions are always welcome!

## License

[MIT](https://choosealicense.com/licenses/mit/)

## More on the Web Audio API

 - [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API/Visualizations_with_Web_Audio_API)
 - [Web Audio API - Book/Amazon](https://www.amazon.com/Web-Audio-API-Advanced-Interactive/dp/1449332684)


