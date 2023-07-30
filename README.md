# Better way to detect the user's platform

Back then we could do something like:

```js
        let userAgent = window.navigator.userAgent,
            platform = window.navigator.platform,
            macosPlatforms = ['Macintosh', 'MacIntel', 'MacPPC', 'Mac68K'],
            windowsPlatforms = ['Win32', 'Win64', 'Windows', 'WinCE'],
            iosPlatforms = ['iPhone', 'iPad', 'iPod'],
            os = null;
```

but platform has been deprecated. Then, we could still do something like:

```js
(() => {
    const osContainer = document.getElementById('os');

    const getOS = () => {
        const userAgent = window.navigator.userAgent.toLowerCase();
        let os = "Unknown OS";

        if (userAgent.indexOf("win") > -1) {
            os = 'Windows';
        } else if (userAgent.indexOf("mac") > -1) {
            os = 'Mac OS';
        } else if (userAgent.indexOf("linux") > -1) {
            os = 'Linux';
        } else if (userAgent.indexOf("android") > -1) {
            os = 'Android';
        } else if (userAgent.indexOf("iphone") > -1 || userAgent.indexOf("ipad") > -1 || userAgent.indexOf("ipod") > -1) {
            os = 'iOS';
        }

        return os;
    };

    osContainer.textContent = `Operating System: ${getOS()}`;
})();
```

The problem is that the UA can be spoofed. So this solution helps prevent 
countering spoofing and is more reliable.