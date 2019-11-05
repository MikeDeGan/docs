---
title: Performance
---

# Tips for web site performance

## network transfer optimizations

1. minimize your html, css and js files.

Optimize images

- use the appropriate image format for the job
  - animations - use a gif
  - colorful images - use a jpeg
  - simple icons or logos - use an SVG
  - https://99designs.com/blog/tips/image-file-types/
  - https://www.sitepoint.com/gif-png-jpg-which-one-to-use/
  - image size analysis tool https://pageweight.imgix.com/
- reduce png files with the TinyPNG site
- Reduce jpg files with the JPEG-optimizer site
- Choose simple illustrations over highly detailed photos
- Always lower jpeg image quality
- Resize the image based in the size that it will be displayed. 500px wide use a 500px wide image.
- Use media queries to display different sized images for different devices.
- Use CDN's like Imigx or CloudFlare. They can optimize images automatically among other things.
- Remove image metadata. EXIF. www.verexif.com

## Critical Render Path

![Citical Render Path](./images/Screenshot 2019-11-04 at 7.29.35 PM.png)

1. Load <style> in head. The css Object Model is required to render.

2. Load <script> right before the /body tag. If the js is in the head the render will wait for the js to download. JS needs the html and css parsing to finish prior to running. So having js at the bottom gives your html, css and media a chance to download and render before the js downloads and runs.

3. Load only what is needed. Clean up your css no unnecessary or unused css.

4. Above the fold loading. Get just the css needed to style the above the fold stuff. You can have two css files, one that gets loaded in the head and the below the fold css that gets loaded after the initial render. It can be done like this..

   ```javascript
   //At the bottom of the html
   <script type="text/javascript">
       const loadStyleSheet = src => {
           if(document.createStylesheet) {
               document.createStylesheet(src)
           }  else {
               const stylesheet = document.createElement('link');
               stylesheet.href = src;
               stylesheet.type = 'text/css';
               stylesheet.rel = 'stylesheet';
               document.getElementsByTagName('head')[0].appendChild(stylesheet)
           }
       }
       window.onload - function() {
           loadStyleSheet('./style.css')
       }
   </script>
   </body>
   ```

5. Media attributes. You can do these in your html files as well. As example you can put the following in your <head> tag to only load this css on screens over 500px. media= will always default to media="all".

   ```html
   <link rel="stylesheet" href="./style2.css" media="only screen and (min-width:500px)">
   ```

6. Less specificity. The less specific your css the less processing the browser will have to do and the fewer characters that will be needed to download. Not a huge performance increase but it is something.