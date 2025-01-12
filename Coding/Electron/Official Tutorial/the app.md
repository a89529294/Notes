## Prerequisites
To check which version of Node.js is running in your app, you can access the global [`process.versions`](https://nodejs.org/api/process.html#processversions) variable in the main process or preload script. You can also reference [https://releases.electronjs.org/releases.json](https://releases.electronjs.org/releases.json).

## Building your First App
- create a directory and cd into it, then run `npm init -y`
-  _entry point_ should be `main.js` (you will be creating that file soon).
- _author_, _license_, and _description_ can be any value, but will be necessary for [packaging](https://www.electronjs.org/docs/latest/tutorial/tutorial-packaging) later on.
- `npm install electron --save-dev`

In Electron, each window displays a web page that can be loaded either from a local HTML file or a remote web address.

Each web page your app displays in a window will run in a separate process called a **renderer** process (or simply _renderer_ for short). Renderer processes have access to the same JavaScript APIs and tooling you use for typical front-end web development, such as using [webpack](https://webpack.js.org/) to bundle and minify your code or [React](https://reactjs.org/) to build your user interfaces.

Checking against Node's [`process.platform`](https://nodejs.org/api/process.html#process_process_platform) variable can help you to run code conditionally on certain platforms. Note that there are only three possible platforms that Electron can run in: `win32` (Windows), `linux` (Linux), and `darwin` (macOS).

```js
if (process.platform === 'win32') { 
// Code that runs only on Windows 
console.log('This is Windows'); } 
else if (process.platform === 'darwin') { 
// Code that runs only on macOS 
console.log('This is macOS'); }
else if (process.platform === 'linux') { 
// Code that runs only on Linux 
console.log('This is Linux'); 
}
```

## Using Preload Scripts
Electron's main process is a Node.js environment that has full operating system access. On top of [Electron modules](https://www.electronjs.org/docs/latest/api/app), you can also access [Node.js built-ins](https://nodejs.org/dist/latest/docs/api/), as well as any packages installed via npm. On the other hand, renderer processes run web pages and do not run Node.js by default for security reasons.

To bridge Electron's different process types together, we will need to use a special script called a **preload**.

A _BrowserWindow's preload script_ runs in a context that has access to both the _HTML DOM and a limited subset of Node.js and Electron APIs_.

| Available API      | Details                                       |
|--------------------|-----------------------------------------------|
| Electron Modules   | Renderer process modules                      |
| Node.js Modules    | events, timers, url                           |
| Polyfilled globals | Buffer, process, setImmediate, clearImmediate |

## Packaging your Application
- `npm install --save-dev @electron-forge/cli`
- `npx electron-forge import`
- 
