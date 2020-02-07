# Gdrive Uploader
Gdrive Uploader is a simple JavaScript to upload a file to Google Drive and set its MIME type.  Why would you ever need to do such a thing?  Well, in my case, I was trying to upload vector graphics via Google Drives browser interface, but it wasn't setting the MIME type correctly.  Therefore, I wasn't able to open the vector graphics with Google Drawings.
## Dependancies
* [Node.js](https://nodejs.org/en/download/)
* [Google API v3 Node.js Client](https://www.npmjs.com/package/googleapis) (e.g. `npm install --global googleapis`)
## Usage
1. Edit config.js
  * config.destination.name - The name of the file as you would like it to appear in Google Drive.  Typically set to the same name used in config.source.path.
  * config.destination.mimeType - For a ".emf" file, use "application/x-msmetafile".  Otherwise, [here](https://developers.google.com/drive/api/v3/mime-types) are the MIME Types that are specific to G Suite and Google Drive.
  * config.source.path - The local path of the file that you want to upload.
1. asdf
