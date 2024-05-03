The address of the image attribute can be used in two different ways. 
An address that contains the full URI, i.e., the protocol, the host, etc, will lead the browser requesting the content from the full path. 
If the address contains just a path, the image will be requested either starting from the root of the server (if the `src` attribute value starts with `/`) or starting from the current path (if the `src` attribute value does not start with `/`).

## example
```
<img src="images/image.png" alt="alt text" />
on the page http://aalto.fi/content/index.html

gives the full path: http://aalto.fi/content/images/image.png
```
Note that it is relative to the current file's(index.html) parent directory(content).