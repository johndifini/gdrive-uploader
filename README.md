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
1. Authorize the use of Drive API - Follow Google's instructions in [Step 1 of their documentation](https://developers.google.com/drive/api/v3/quickstart/nodejs#step_1_turn_on_the); however, saving any credential-related file in a working directory is a bad practice.  Instead, save the credentials.json file to your home directory, and then tightly restrict its permissions (`chmod 600 credentials.json`).  Note that the upload.js file will automatically save the corresponding token.js file to your home directory too.  Also note that if you happen to change `SCOPES` in upload.js, you'll need to delete the token.js file so that the code can recreate it.
1. Run `node upload.js`.  If it's your first time running it, you'll need to following the prompt in order to generated your token.js file (this will involve coping & pasting a the given link into a browser, which will prompt you to grant access).
## Security Info
If you are concerned about some strange code having access to your Google Drive, GOOD FOR YOU!  I'll explain what access the code has in a bit...
