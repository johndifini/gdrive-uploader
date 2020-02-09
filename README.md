# Gdrive Uploader
Gdrive Uploader is a simple JavaScript to upload a file to Google Drive and set its MIME type.  Why would you ever need to do such a thing?  Well, in my case, I was trying to upload a vector graphic via Google Drive's web interface, but it wasn't setting the MIME type correctly.  Therefore, I wasn't able to open the vector graphic with Google Drawings.
## Dependancies
* [Node.js](https://nodejs.org/en/download/)
* [Google API v3 Node.js Client](https://www.npmjs.com/package/googleapis) (e.g. `npm install --global googleapis`)
## Usage
1. Edit config.js
   * config.destination.name - The name of the file as you would like it to appear in Google Drive.  Typically set to the same name used in config.source.path.
   * config.destination.mimeType - For a ".emf" file, use "application/x-msmetafile".  Otherwise, [here](https://developers.google.com/drive/api/v3/mime-types) are the MIME Types that are specific to G Suite and Google Drive.
   * config.source.path - The local path of the file that you want to upload.
1. Authorize the use of Drive API - Follow Google's instructions in [Step 1 of their documentation](https://developers.google.com/drive/api/v3/quickstart/nodejs#step_1_turn_on_the); however, saving any credential-related file in a working directory is a bad practice.  Instead, save the credentials.json file to your home directory, and then tightly restrict its permissions (`chmod 600 credentials.json`).  Note that the upload.js file will automatically save the corresponding token.json file to your home directory too.  Also note that if you happen to change `SCOPES` in upload.js, you'll need to delete the token.json file so that the code can recreate it.
1. Run `node upload.js`.  If it's your first time running it, you'll need to followi the command prompt in order to generated your token.json file (this will involve coping & pasting the given link into a browser, which will in turn prompt you to grant access).
## Security Info
If you are concerned about some strange code having access to your Google Drive, **good for you**!  I had the similar concern, which led me to develop this simple utility script (see Alternative).  The first part of the code is nearly verbatim from Google's official [Quickstart documentation](https://developers.google.com/drive/api/v3/quickstart/nodejs#step_3_set_up_the_sample), but I made it more secure by putting the credentials.json and token.json in the home dir.

The last part of the code is also nearly verbatim from Google's official (Perform a simple upload)[https://developers.google.com/drive/api/v3/manage-uploads#simple] example, but I made it more flexible using a configuration file.  I also fixed a bug (file.id should be file.data.id).
## Alternative
If you are looking for a simpler way to get a vector graphic into Google Drive, you can do it with CloudConvert using [these instructions](https://graphicdesign.stackexchange.com/a/115861).  This was the approach that I originally took, but I didn't like the idea of granting a third-party access to my Google Drive and access to the to-be-converted file.  CloudConvert seems like a very reputable company, but I personally like to play it safe.
