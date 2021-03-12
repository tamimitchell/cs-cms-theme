# ClockShark CMS Theme

This repo corresponds with the 'CS Theme' folder in HubSpot and the Landing Pages Webflow. By using this theme for landing pages, we can standardize our modules and styles for a more consistant brand-wide look.

## Getting Started 

* Clone this repo down to your computer. 
* Install the HubSpot CLI per their [Getting started with local development Guide](https://developers.hubspot.com/docs/cms/guides/getting-started-with-local-development).
* Rename `src/theme.json.default` to `src/theme.json` to and update the `label` field to be the your own personal development label. For example, my initials are 'tmm' so my dev theme is named "ClockShark CMS Theme (TmmDev)".
* Using the HubSpot ClI, upload this theme to your own personal development folder.

```
hs upload src CS\ Theme\ YourLabel
```

* Please do not upload/watch directly to "CS Theme", because this can cause issues in the HubSpot system if multiple developers are uploading at the same time.
* You can see your new folder in HubSpot > Files and Templates > Design Tools. Click on this folder and then Actions > Lock Folder to ensure changes cannot be made from the web interface.

## Development Workflow

Now you can work on the theme code locally. 

* There is no local server. Run the watch command to automatically upload any file changes to HubSpot

```
hs watch src CS\ Theme\ YourLabel
```

* You can update the WebFlow css url in `src/config-vars.html`. 
* To view your theme changes, create a test page in HubSpot using your development theme. You'll need to manually refresh the browser page, but it updates quickly after the watch upload runs. 
* Commit work to git branches until ready to deploy changes live. Pushing to master will automatically update the main CS Theme, so be cautious. 

## Deploying to Production 

* Merge work in git branches to master. Pushing to master will automatically update the main CS Theme.

## Other Notes

* This repo is based on <https://github.com/HubSpot/cms-theme-boilerplate> and [Setting up continuous integration with a GitHub repository using GitHub Actions](https://developers.hubspot.com/docs/cms/guides/github-integration). It may be a little unweildy if we ever get a lot of developers using it, but I believe using the HubSpot theme structure and being able to work fast locally will be worth it. 
* File Structure
  * The HubSpot theme came with a nice file structure. The original repo has some drag and drop template examples, or use "guides-landing-page" as a non-drag-and-drop example. 
  * Keep templates clean by using partials for major parts of the page.
  * Use standard modules when possible so users can edit directly on the page.
  * Use custom modules when more customization is needed, but try to keep them simple. 
  * Distinguish specific template modules from generic modules. Some may be designed specifically for their pages and trying to make them work across multiple designs might result in constant iterations when different stakeholders want different looks. For example, `GL FAQ` was designed specifially for the Guides Landing template.
* New Modules
  * Modules use a json file structure for input config. It's faster to create these in the UI than locally. You can do this by unlocking your dev theme folder, creating the module in the HubSpot interface *for your dev theme*, then copying down the new code with the HubSpot CLI:

```
hs fetch CS\ Theme\ YourLabel src
```
  * Adding these files to the repo will add them to the main theme folder once they're pushed to master.
