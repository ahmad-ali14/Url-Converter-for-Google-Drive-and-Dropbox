# Url-Converter-for-Google-Drive-and-Dropbox

### live at: https://url-converter-for-gdrive-dropbox.netlify.app/


## what is this ??
- when you host an image on google drive or dropbox you can't use the direct url of your file to be an image source.
- you need to make changes to this url in order to use it directly as an image source.
- This App will take the url of your image file, and change it to be used directly as an image source.
- Important : you need to check your files permessions first, and wether it's public.
- another live example with react: https://ybmex.csb.app/

## functionality
| Function title: goobox |  tags: image hosting, regex, url, google drive, dropbox, advanced |
| :-: | :-:  |
| return: string | Returns a string url that can be used directly as source of an image. |


```js
const goobox = (url)=>{
    let dropbox_regex = /(http(s)*:\/\/)*(www\.)*(dropbox.com)/;
    let drive_regex =/(http(s)*:\/\/)*(www\.)*(drive.google.com\/file\/d\/)/;
    if(url.match(dropbox_regex)){
       return url.replace(/(http(s)*:\/\/)*(www\.)*/, "https://dl.");
    }
    if(url.match(drive_regex)){
     return `https://drive.google.com/uc?id=${url.replace(drive_regex, "").match(/[\w]*\//)[0].replace(/\//,"")}`;
    }
    return console.error('Wrong URL, not a vlid drobox or google drive url');
}
```

```js
let gDriveUrl = "https://drive.google.com/file/d/1VctOazcyDrm8nxoWFAWM_t5bxlpyLI9s/view?usp=sharing";
let dropboxUrl = "https://www.dropbox.com/s/degru93hceo26m6/30sec.png?dl=0";
goobox(gDriveUrl);  // https://drive.google.com/uc?id=1VctOazcyDrm8nxoWFAWM_t5bxlpyLI9s
goobox(dropboxUrl); // https://dl.dropbox.com/s/degru93hceo26m6/30sec.png?dl=0
```

<img src="https://pbs.twimg.com/media/ETouJ-LXQAU_SqV?format=png&name=small" width="200px" >
