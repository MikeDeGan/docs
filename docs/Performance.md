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