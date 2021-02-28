# Popup Page

## How to read title of the current page

in this senario, it reads the title of the current window and active tab. for instance, if you are browsing YouTube, the title of YouTube will be read.

```javascript
chrome.tabs.query({ active: true, currentWindow: true }, function (tabs) {
  const title = tabs[0].title;
  console.log(title);
});
```

## How to open a new tab in popup page

```javascript
chrome.tabs.create({ url });
```

## How to send a message object to the background script

Send a message from popup page to background script. Same approach as content script

```javascript
chrome.runtime.sendMessage({
  type: 'setBadgeText',
  data: 'Hi',
});
```

## How to send a message object to the content script and send an XHR request to your API

This approach here is slightly different than sending a message to background script. You first need to find which window and which tab you should send the message. <code>{ active: true, currentWindow: true }</code> and then send the message to the current tab <code>tabs[0].id</code>.

In this case it will first sends a message to content.js and then the content.js will send an XHR request to your api let's say api.github.com to fetch a repository. content.js will get the response from api and send it back to popup page. Right click on popup page > "inspect" to see the responded data in console. To see the XHR request, open Devtools > Network on the active tab.

```javascript
chrome.tabs.query({ active: true, currentWindow: true }, function (tabs) {
  chrome.tabs.sendMessage(
    tabs[0].id,
    { type: 'sendXhrRequest' },
    function (callbackData) {
      console.log('Message sent to content.js from popup.', callbackData);
    }
  );
});
```

Click
[here](content?id=how-to-send-an-xhr-request-to-your-api)
to see how the content script sends an XHR request to your API
