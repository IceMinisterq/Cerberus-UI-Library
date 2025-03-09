# Cerberus



## Getting started

```lua
local Library = loadstring(game:HttpGet("", true))()
```

## Creating a Window
```lua
local Window = Library:BeginWindow({
    Title = "Title",
    -- LogoId = "", -- In case of custom id
    ToggleKey = Enum.KeyCode.RightShift,
    -- DestroyKey = "RightBracket"
})
```

## Creating a Page
```lua
local Page = Window:BeginPage("Page Name")
```

## Creating a Section
```lua
local Section = Page:CreateSection("Section 1")
```

## Creating Components

### Action / Button
```lua
local action1 = Section:CreateButton({
    Name = "Button",
    Callback = function()
        print("clicked")
    end
})
```

### Boolean / Toggle

* There are two styles, "Switch" and "Checkbox"
- Default Debounce is **0.3 seconds** but can be changed with the `Debounce`

```lua
-- Switch
local switch = Section:CreateSwitch({
    Name = "Switch",
    Default = true,
    Callback = function(value) 
        print(value)
    end
})

-- Checkbox
local checkbox = Section:CreateCheckbox({
    Name = "Checkbox",
    Default = true,
    Callback = function(value) 
        print(value)
    end
})
```

### Sliders / Number
- By default, sliders aren't using floats number, you can change that by looking at the example

```lua
local slider = section:CreateSlider({
    Name = "Slider",
    Range = { 16, 500 },
    Default = 16,
    Callback = function(value)
        print(value)
    end
})

local fslider = section:CreateSlider({
    Name = "Float Slider",
    IsFloat = true,
    MaxDecimals = 2,
    Range = { 1, 5 },
    Default = 16,
    Callback = function(value)
        print(value)
    end
})
```

* Sliders have an option for keybinds.
```lua
local slider = Section:CreateSlider({
    Name = "Walkspeed Slider",
    Description = "Modify your walkspeed",
    Range = { 16, 500 },
    Default = 16,
    Callback = function(value, enabled)
        game:GetService("Players").LocalPlayer.Character.Humanoid.WalkSpeed = value
    end
})
```

### Dropdowns / List
```lua
local dropdown = Section:CreateDropdown({
    Name = "Type",
    Options = {
        "Option 1";
        "Option 2";
        "Option 3";
        "Option 4";
        "Option 5";
    }
    Callback = function(value) 
        print(value)
    end
})
```

### Multi-dropdowns / Multi-booleans
```lua
local multidropdown = Section:CreateMultiDropdown({
    Name = "Multi Dropdown",
    Options = {
        {"Option 1", false};
        {"Option 2", false};
        {"Option 3", false};
        {"Option 4", false};
        {"Option 5", false};
    },
    Callback = function(flag, value) 
        print(flag, ":", value)
    end
})
```

## Methods

### Toggles (Checkbox & Switches)
```lua
-- Change the Toggle state to the boolean provided
toggle:SetValue(true)

-- Change the Toggle's Callback to the new function provided
toggle:SetCallback(function(value)
    print("New value :", value)
end)

-- Change the Toggle's Name to the new name provided
toggle:SetName("Name")
```

### Sliders
```lua
-- Change the Slider value to the new value provided(**qsdqssq**)

slider:Set(100)


```

### Dropdowns
```lua
...
dropdown:AddNewItem("Item 2")
```
```lua
...
dropdown:RemoveItem("Item 2")
```
## Notes

* When adding `keybinds` to sliders, the callback function will pass the value and the state of slider.

* On startup, keybinds may not initiate, to fix this just edit the `keybind`