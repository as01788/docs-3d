# Introduction To Preview Process And Common Error Handling

## Introduction To Preview Process

Since **Cocos Creator 3D** only supports preview in browser currently, only the browser preview process is introduced here.

When open Cocos Creator 3D, the editor will open an web server(we use Express).When click the preview button, the user's default browser will opened to access the preview URL.Editor use preview template to write some simple logic for loading the engine、 initializing the game, loading game resources. The loading of game resources mainly depends on the generation of `setting.js`,cause `setting.js` records the url of resources, scripts, and some project settings.The `setting.js` is generated by calling the interface of the build plugin. So if `setting.js` is not generated correctly, you can open the build debugging tool to inpect.

## Common Error Handling

**Notes**: please make sure that your solved all error thrown in editor before preview。

### Load setting.js Failed

You can open **`Developer-> Build Debugging Tools`** to see if there is any error message.

Under normal circumstances, if `settings.js` generate failed, there will be some error message in console.The more common is a script error, because when generate `settings.js`, all scripts in project is loaded in builder process. If any project script contains illegal writing, an unexpected error will be thrown during the loading process and the setting.js will generate failed.For specific error message information, you can refer to the hint in the error message. Usually the error content here is the uuid of the resource. The corresponding uuid can be copied to the `assets` panel to search and locate the script.

You can refer to [Introduction To The Build Process](../publish/build-guide.md) to see more details about how **Cocos Creator 3D** generate `settings.js`.

### Resources Loading 404

Usually it is caused by resource loss or import failure. Please `use the missing resource uuid to search in the editor's assets panel`. If no resource is found, usually the resource is lost. You need to modify the scene or resource using the resource. If resources are found, you can try to re-import.If you still can't solve the above problems, please contact us through the [forums](https://discuss.cocos2d-x.org/).