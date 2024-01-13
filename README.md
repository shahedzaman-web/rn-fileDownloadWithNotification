# rn-fileDownloadWithNotification

import RNFetchBlob from "rn-fetch-blob";

  const downloadImage = () => {
    let date = new Date();
    let image_URL = REMOTE_IMAGE_PATH;
    let ext = getExtention(image_URL);
    ext = '.' + ext[0];
    const {config, fs} = RNFetchBlob;
    let PictureDir = fs.dirs.PictureDir;
    let options = {
      fileCache: true,
      addAndroidDownloads: {
        useDownloadManager: true,
        notification: true,
        path:
          PictureDir +
          '/video_' +
          Math.floor(date.getTime() + date.getSeconds() / 2) +
          ext,
        description: 'Video',
      },
    };
    config(options)
      .fetch('GET', image_URL)
      .then(res => {
        console.log('res -> ', JSON.stringify(res));
        alert('Image Downloaded Successfully.');
      });
  };
