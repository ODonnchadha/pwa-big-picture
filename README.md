## Progressive Web Apps: The Big Picture by Maximiliano Firtman

- OVERVIEW:
  - This course helps you understand the platform of progressive web apps, how it works, and when to choose it for developing your next app. 
  - You will see PWAs in action, in mobile and desktop, and see how to distribute them to end-users.

- UNDERSTANDING PROGRESSIBVE WEB APPS:
  - PWA: Progressive Web App. Open definition. App built with web technologies. Works fast while online/offline. Can be installed on different platforms.
  - Ideal for all those apps that consume web content or web services.
  - Native SDKs versus Web development. And hybrid development. PWS part of Web development. Bowser and device experiences.
  - Characteristics:
    - Multiplatform support. Browser. Mobile devices. Desktop computers.
    - Web. Native. Best of both worlds.
      - Web: Links and discoverability. Easy to deploy. Easy to update. Standards and tools.
        - Web frameworks. Web APIs. Web SDKs. Web security model. Privacy. Permissions. Browser abilities.
      - Native: Offline access. Installed icon and standalone. Push notifications. Performance and UX.
  - Apps in action:
  - When to use the platform:
    - Move your Web experience into the app world. No native app development experience. Create an installed app. 
    - Corporate internal apps. Increase user experience. Work offline. Multi-platform and fast deploy.
    - Already have a website with active users. Increase engagement and conversion. Integrate with user devices. Upgrade to PWA.

- CREATING AN APP EXPERIENCE FOR MOBILE & DESKTOP:
  - Criteria: PWA is simply a desing pattern for the Web.
    1. Web app.
    2. Service worker.
    3. App distribution model. (Web app manifest.) W3C spec. JSON file. Meta.
      - Use lighthouse to discern if website is a PWA. Using PWA Criteria:
        - App meta data. Service worker is installed and secure. Offline. Is fast?
  - App experience:
    - PWA theme colour. Standalone experience. (No browser UI.) Completely detached.
    - Android Standalone. Android minimal UI experience. Andriod full-screen experience. (Games. Cannot view App Info.)
    - Pages. (1) SPA. (One URL with client-side routing.) (2) Multiple-page application. Several HTML documents with links.
    - PWA scope: Origin and path that defines where PWA resides. e.g.: domain.app or domain.com/app.
      - Different host? Folder? You create a different scope.
    - Progressive enhancement: 
      - Web design strategy that emphasizes core webpage content first and then progressively adds layers of features as the end user's browser/Internet connection allows.
      - Features: Basic Web content. Installation. Service worker. Hardware useage. e.g.: COnnecting to bluetooth.
      - React to different environments. Offer a good experience for everyone. Same code: Delivering different levels of quality.
      - Use APIs to detect envirponment and act in consequence.
  - The icon:
    - Android: Shortcut to the browser's engine. Doesn't appear in the app's list. Installed only on the home screen.
    - Android: WebAPK. If PWA criteria passes. Home screen and launcher. Only available with Google Chrome play services.
      - WebAPK Link Capturing: Android OS, PWA will capture all links pointing to PWA scope. So, PWA will render rather than browser.
  - Abilities: WebAssembly. WebGL. AR/VR. WebPush. WebShare. WebAuth. Payment request. GamePad. WebRTC. WebBluetooth. MediaRecorder. Machine learning.
    - SesoSensorsnrs and geolocation. Communicationb with other native apps.
    - API support: Progressive enhancement. Extend to Web with native SDKs.
  - Limitations:
    - Web platform. Not every native API is exposed. 
    - Background executation. Geofencing, BLE beacons. Low-level hardware access. OS event handling. 
      - Bugs and lack of documentation. HTTPS required for some abilities.
    - Web App Manifest Spec: Multi-origin PWAs are not allowed. Splash screen customization. Multi-platform icons. Multi-installation detection.
    - Platform awareness. PWAs may live alongside native apps. e.g.: Twitter.

- PROGRAMMING THE PWA WITH WEB TOOLS:
  - Service workers: The brain of the PWA.
    - Service worker registration. Service worker will then download resources . And save them locally within the client. And server to Web runtime.
    - Service worker: A JavaScript file running in its own thread that will act as a local installed Web server/proxy for the PWA.
      - Including resources and API calls. Runs client-side in the browser's engine. HTTPS required.
      - Installed by a Web page. Own thread and lifecycle. Acts as network proxy or local Web server. Abilities to run in the background.
        - No need for user's permission.
  - Scope: An origin (host and port) and a path.
  - Service worker & scope: Manages all pages within browser and within installed app from scope. Any page within scope can install sw.
    - After installed, it can serve all files requested from the scope. Only one service worker per scope is allowed.
    - WebKit adds partition management.
    - Advantages: Fast PWA loading with local cache. Offline support serving locally. 
      - Query the context to offer the best possible experience. Data synchronization with the server.
      - And extras. Background sync. Background fetch. Web push.
    - Caching and serving resources.
      - Local cache via service worker. All or some resources via JavaScript promise. 
        - Prefetch on service worker installation. Cache on request. App Shell pattern.
      - The sw will respond to every request. Serve from cache. Forward request to network. Synthesize a response. Any mixed algorithm is possible.
    - Caching strategies: (1) Cache first. (2) Network first. Error/offline, then cache. (3) Stale while revalidate. Serve from cache, repopulate via network.
    - Updating resources: Files are saved on client. Updating files in the server will not trigger any automatic change in client.
      - We need to define and code an update algorithm. A process within your build sysstem for hashing or versioning files.
      - Developer in full control as how to cache & serve the resources of the PWA, and how to manage API calls.
        - Updating the app doesn't require full reinstallation. Just replace the updated files silently or with user notification.
    - Adding a service worker:
      - A service worker is a middleware, so we can add it or remove it to any web project without architectural changes.
      - sw: Low-level API. Powerful but also with not so many tools for common scenarios.
      - PWA not mandatory. A sw is mandatory for a PWA, but being a PWA is optional for using service worker's abilities.
      - Adding: Define which abilities we'll use. Write the JS or use a library. Register it with the JS API in the wensite or Web app.
        - Prepare your analytics and server for this *new* paradigm. Define an update policy. (And do we notify the user?)
        - Workbox JS: An open-source library to manage the common design patterns for a service worker within a PWA.
          - Managed by Chrome team. Precaching and runtime caching. Request routing. Updating resources. Background sync.
            - Offline analytics. Integration with Webpack, npm, Rollup. Flexibility with plugins.
    - PWAs with Angular. & React.
      - Angular CLI support PWAs as a first-class output, part of the build system as an official add-on.
        - Via CLI, you can add PWA support: Create a Web App Manifest. Generate a SW and a resources' manifest on each build.
        - Generate an APp Shell for performance. Include automatic update for PWA files. Routing setup is available through JSON.
        - SW plugins are also avaliable. SwUpdate and SwPush services available.
        ```javascript
          @angular/pwa
        ```
      - React supports PWAs as a first-class output, part of the build system. Disabled by default.
        - SW is not customizeale, but can be replaced. Otherwise, see Angular.
        ```javascript
          create-react-app
        ```

- DISTRIBUTING THE APP TO YOUR USERS:
  - Distribution models: How users will find, and install, our app.
    1. Browser:
    2. Enterprise:
    3. App store:
    - Web packaging:


- WHAT'S THE PATH TO PWAS?: