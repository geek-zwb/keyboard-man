# Use multiple displays with your Mac

Q：
当你使用多个屏幕的时候， 可以使用<kbd>Alt<kbd> + <kbd>Tab<kbd> 切换应用，
如果这个应用在另一个屏幕，Mouse focus 并不会一起移动至这个屏幕。

当你在这个屏幕内需要屏幕内切换桌面时， 不得不通过鼠标移动到这个屏幕。

A:
可以使用`Hammerspoon` 进行自定义鼠标事件， 通过快捷键移动鼠标位置。
- Download the latest release of Hammerspoon and drag it to your /Applications folder
- Run Hammerspoon.app and follow the prompts to enable Accessibility access for the app
- Click on the Hammerspoon menu bar icon and choose Open Config from the menu
- add follow func append the config
 ```
 -- Move Mouse to center of next Monitor
hs.hotkey.bind({'cmd', 'alt'} , '`', function()
    local screen = hs.mouse.getCurrentScreen()
    local nextScreen = screen:next()
    local rect = nextScreen:fullFrame()
    local center = hs.geometry.rectMidPoint(rect)

    hs.mouse.setAbsolutePosition(center)
end)
```
- currently you can use  <kbd>cmd<kbd> + <kbd>alt<kbd> + <kbd>`<kbd> to move your mouse position into next screen. 
 

