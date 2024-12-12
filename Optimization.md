
## Setting a budget
Set the frame per second we want
Check how much ms we need to achieve in order to do that.

## Scalability
Set scalability per platform [doc](https://dev.epicgames.com/documentation/en-us/unreal-engine/scalability-reference-for-unreal-engine) 
## Tools
Unreal commands => [[#Cheatsheet]]
Unreal Insight
Render doc
Presentmon (Intel tool)
Unreal frontend
[[#TraceGame.bat]]

## Profilling
**If in editor, set realtime to off, launch the game in standalone and minimze the editor.**
- [ ] Create a profiling build
	- [ ] **Project Settings** -> **Project** -> **Packaging**: Set build configuration to Development, Test or Shipping (Shipping doesn't allow profiling because it removes console commands)
	- [ ] **Project Settings** -> Engine -> **General settings**: Disable smooth frame rate
- [ ] Turn off VSync
- [ ] Set maxfps to 0
- [ ] Start Unreal Insight profiling
- [ ] Start the game
- [ ] Use `stat unit` & `stat unitgraph` to get an overview
	- [ ] Check the workload per category
- [ ] Play through part of the game/level to gather some data
- [ ] Check Unreal insight
## Cheatsheet 

| Command                   | Description                                                                                                                                                                         |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `stat UnitGraph`          | Graph of the workload                                                                                                                                                               |
| `stat unit`               | See time spent in ms per frame on each category. **For overview only**                                                                                                              |
| `r.screenpercentage`      | Get screen percentage value or set it to a value between 0-100                                                                                                                      |
| `r.vsync`                 | Turn on or off                                                                                                                                                                      |
| `t.maxfps`                | Set max fps                                                                                                                                                                         |
| `pause`                   | Pause the game, help to see the flat cost of rendering a frame                                                                                                                      |
| `stat namedevents`        | Add more details to profiling                                                                                                                                                       |
| `trace.bookmark {name}`   | Add points in the Unreal insight ui to reference, can be usefull to specify places in the level we enter for example. Could be link to triggers in the levels that runs the command |
| `trace.screenshot {name}` | Create a bookmark but with a screenshot also                                                                                                                                        |

## TraceGame.bat
[Command lines arguments available](https://dev.epicgames.com/documentation/en-us/unreal-engine/command-line-arguments-in-unreal-engine)

```
start {executable} {mapPath} -trace={traceChannelToShow} -benchmark -deterministic -fps={fpsBudget} -novsync -noverifygc -nosound -noailogging -benchmarkseconds=180 -corelimit=6 -demorec -statnamedevents
```