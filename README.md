![audiocompact](https://github.com/user-attachments/assets/858baef1-026a-4ba9-95f7-7a608855e834)


![Static Badge](https://img.shields.io/badge/Vue-3.5.13-green) 

![Static Badge](https://img.shields.io/badge/Typescript-5.6.3-navy)

![Static Badge](https://img.shields.io/badge/Composition%20API-orange)

# Audio Player - Vue - TS - Web Audio API

Here is the compact version of the mp3 player that I first posted @ https://github.com/thorstensson/audio-player-vue-ts. 

This player uses a .env file for the URL (no longer on AWS). Thus, such .env vars are, of course, visible client-side, even if the .env file is not on GitHub.

I might later on do a Nuxt version where audio is fetched server-side, but if you use AWS or some other host, I would recommend restricting the policy to the domain you own—if you don't want public access.

For now have to get on with my portfolio and some other stuff coming on new repos in 2025 and leave audio as is, as it was not my intention to get so busy with audio in 2025, albeit fun!

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


