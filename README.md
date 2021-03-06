# Background-Color-Change-Chrome-Extension
An extension that allows the user to change the background color of any page on <a href="#">any webpage</a></br>
just put the URL of the webpage for which color is to be changed in <b>pageUrl: {hostEquals: 'https://www.____com'}</b>, in <b>background.js</b> file
1. <b>Create the Manifest</b> : <br>
Extensions start with their manifest. Creating a file called <b>manifest.json</b>
2. <b>Add Instructions</b> : <br>
Introducing a background script by creating a file titled <b>background.js</b> for giving instructions to the manifest.Background scripts, and many other important components, must be registered in the manifest. Registering a background script in the manifest tells the extension which file to reference, and how that file should behave.
<br> The extension is now aware that it includes a non-persistent background script and will scan the registered file for important events it needs to listen for.<br> This extension will need information from a persistent variable as soon as its installed. Thus Started by including a listening event for runtime.onInstalled in the background script. Inside the onInstalled listener, the extension will set a value using the storage API. This will allow multiple extension components to access that value and update it.
<br> Most APIs, including the storage API, must be registered under the "permissions" field in the manifest for the extension to use them.
3. <b>The User Interface</b> :<br>
Extensions can have many forms of a user interface, but this one is using a popup. Create and add a file titled <b>popup.html</b> to the directory, or download it here. This extension uses a button to change the background color. <br>
Like the background script, this file needs to be designated as a popup in the manifest under<b> page_action</b>. <br>
Designation for toolbar icons is also included under page_action in the default_icons field. <br>
Extensions also display images on the extension management page, the permissions warning, and favicon. These images are designated in the manifest under icons.<br>
If the extension is reloaded at this stage, it will include a grey-scale icon, but will not contain any functionality differences. Because page_action is declared in the manifest, it is up to the extension to tell the browser when the user can interact with <b>popup.html</b>.<br>
Adding declared rules to the background script with the declarativeContent API within the <b>runtime.onInstalled listener</b> event.<br>
The extension will need permission to access the <b>declarativeContent API</b> in its manifest.
  <br>The browser will now show a full-color page action icon in the browser toolbar when users navigate to a URL that contains <b>"developer.chrome.com"</b>. When the icon is full-color, users can click it to view <b>popup.html</b>.
  <br>The last step for the popup UI is adding color to the button. Thus Created and added a file called <b>popup.js</b><br>
 4. <b>Layer Logic </b>:
  <br> The extension now knows the popup should be available to users on <b>developer.chrome.com</b> and displays a colored button, but needs logic for further user interaction. Updating <b>popup.js</b> <br>
  The updated code adds an onclick event the button, which triggers a <b>programatically injected content script</b>. This turns the background color of the page the same color as the button. Using programmatic injection allows for user-invoked content scripts, instead of auto inserting unwanted code into web pages.<br>
The manifest will need the <b>activeTab</b> permission to allow the extension temporary access to the <b>tabs API</b>. This enables the extension to call <b>tabs.executeScript</b>.<br>
 5. <b>Give User Options</b> : <br>
  Including an options page gives users more control over the extension's functionality, further customizing their browsing experience.<br>
  creating a file in the directory called <b>options.html</b> 
