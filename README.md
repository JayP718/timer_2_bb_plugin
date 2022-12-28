# Timer_2

A second version of my original timer plugin. 2nd Plugin to not break existing implementations of original plugin. This plugin is not dependent in being inside a form, takes parameters in the form of milliseconds since the epoch, and can run actions upon timer completion.
# Description
Version 2.0 of the timer which does not have to be a part of a form. It can accept any binding (number) and shows a progress bar as well.

| Option  | Description |
| ------------- | ------------- |
| End Date Time Field  | End time of Timer. Accepts milliseconds since Epoch. Examples below |
| Shape | Shape of Timer (Square/Medium Rounded/Rounded)  |
| Background Color | Color of Timer |
| Countdown Reached Text | Text once timer completes |
| Starting Date Time Field | Optional* Accepts milliseconds since epoch. If starting Date time is not current date time.  |
| Beginning Date Time Field | Optional* Accepts milliseconds since epoch. If beginning Date time is not current date time.  |
| On Timeout | Actions which will run upon timeout  |

# Examples of End Date Time Options - Javascript

## If from data provider
return new Date($("New Data Provider.Rows")[0].endDateTime).getTime()

## If static--30 Second Timer
return new Date().getTime()+30000

Find out more about [Budibase](https://github.com/Budibase/budibase).

## Instructions

To build your new  plugin run the following in your Budibase CLI:
```
budi plugins --build
```

You can also re-build everytime you make a change to your plugin with the command:
```
budi plugins --watch
```

