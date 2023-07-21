# AppleScript 

## get wallpaper

```AppleScript
tell application "System Events"
    set outputText to "{"
    set isFirstDesktop to true
    repeat with current_desktop in desktops
        if isFirstDesktop then
            set outputText to outputText & "\"" & name of current_desktop & "\"" & ":" & "\"" & picture of current_desktop & "\""
            set isFirstDesktop to false
        else
            set outputText to outputText & "," & "\"" & name of current_desktop & "\"" & ":" & "\"" & picture of current_desktop & "\""
        end if	
    end repeat
    set outputText to outputText & "}"
end tell
return outputText
```



