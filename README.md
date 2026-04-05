# curl -c

ui library or stuff it makes guis and doesnt crash anymore

press `rightshift` to hide it idk

### example 

just put ts in ur executor and look at it

```luau
-- get the thing
local curl = loadstring(game:HttpGet("https://raw.githubusercontent.com/Spektronazam/curlc/refs/heads/main/source"))()

-- make window
local win = curl.new()

-- make tab
local tab = win:addPage({ title = "main stuffs" })

-- make section
local sec = tab:addSection({ title = "buttons and things" })

-- add elements
sec:addButton({
    title = "click me",
    callback = function()
        print("you clicked it")
        win:Notify({ title = "yo", text = "button clicked" })
    end
})

sec:addToggle({
    title = "toggle me",
    default = false,
    callback = function(state)
        print("toggled:", state)
    end
})

sec:addTextbox({
    title = "type something",
    default = "idk",
    callback = function(text, enterPressed)
        print("you typed:", text)
    end
})

sec:addKeybind({
    title = "press a key (or mouse)",
    key = Enum.KeyCode.F,
    callback = function()
        print("keybind pressed")
    end,
    changedCallback = function(newKey)
        print("changed bind to:", newKey)
    end
})

sec:addSlider({
    title = "slide it",
    min = 0,
    max = 100,
    default = 50,
    callback = function(val)
        print("slider is at:", val)
    end
})

sec:addDropdown({
    title = "pick one",
    list = {"apple", "banana", "car", 69},
    callback = function(chosen)
        print("you picked:", chosen)
    end
})

sec:addColorPicker({
    title = "color picker",
    default = Color3.fromRGB(255, 0, 0),
    callback = function(color)
        print("color changed to:", color)
    end
})

-- theme stuff if you want it
local themeTab = win:addPage({ title = "colors" })
local themeSec = themeTab:addSection({ title = "change theme" })

themeSec:addColorPicker({
    title = "Accent Color",
    default = Color3.fromRGB(10, 10, 10),
    callback = function(color)
        win:setTheme({ theme = "Accent", color3 = color })
    end
})

-- load it up
win:SelectPage({ page = win.pages[1], toggle = true })
```

ok bye
