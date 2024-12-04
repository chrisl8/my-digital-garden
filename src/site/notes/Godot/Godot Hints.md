---
{"created":"2023-09-01","time":"Friday, September 1st, 2023 @ 4:07:54pm","tags":["Godot"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/godot/godot-hints/","dgPassFrontmatter":true}
---

Some hints I've collected on doing things in Godot

# Angle Maths
 - I have a transform3d that is looking at some direction and I want to know the angle from that direction to the target how could I do that?
```swift
var looking_direction = -some_transform.basis.z
var target_direction = target.global_position - some_transform.origin
var angle_between = looking_direction.angle_to(target_direction)
```
https://discord.com/channels/212250894228652034/908062856459743262/1147271399065530438

# Print Entire Scene Tree
`print_tree()`
or
`print_tree_pretty()`

# Get root node from anywhere
`get_tree().get_root()`

# Color Picker
The Color picker feels broken to some of us. Like if you slide the sliders all over to white, the wheel is now just . . . white.

How do I pick a color?!
![](/img/user/attachments/Pasted image 20231004173651.png)

Click the little OI thingy on the right and change it to "VHS Circle" and then it looks like you probably expected it to
![](/img/user/attachments/Pasted image 20231004173807.png)

However this will revert back every time, so go into Editor Settings and set the default under Interface->Inspector->Default Color Picker Shape
![](/img/user/attachments/Pasted image 20231004174109.png)
# Await
First **please** READ THIS fully:
https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_basics.html#awaiting-for-signals-or-coroutines

`await` feels a little bit magic, because it feels like it turns a function into a magical "I will return early, but do my thing anyway" trick.

It kind of is, but here is how I look at it to make it feel less magic:

*The `await` keyword prevents a function from continuing to the next line of code until the awaited thing finishes, BUT the **function itself RETURNS immediately** upon hitting the `await` keyword.*

You have two choices when running a function containing an `await` line in it:
1. Do **NOT** ask for the return value.
2. `await` the function yourself, essentially chaining things.

It is a little weird that `await` magically causes a return "value" that you didn't specifically ask for or `return`, but that is what it does.
The return "value" is a coroutine. You an `await` THAT coroutine if you want to.

Remember that you **CANNOT** just get the return value of such a function without awaiting it, which the documentation you read at the beginning clearly states. So you cannot just grab and pass around a "ticking function".

**TL;DR:** If you want something to happen after a timer, but don't want your `_read()` or `_process()` or `whatever()` function to stall, put it in ANOTHER function and call THAT function, since it will just return and let you carry on.

This code will help demonstrate:
```
func _ready() -> void:
    print("1")
    await get_tree().create_timer(5).timeout
    print("2")
    wait_on_something()
    print("3")

func wait_on_something() -> void:
    print("4")
    await get_tree().create_timer(5).timeout
    print("5")
```

The result will be:
 - 1
 - Five second pause
 - 2
 - 4
 - 3
 - Five second pause
 - 5

Notice how the `wait_on_something()` function is run, normally, and waited upon, so 4 happens before 3, but then when it hits `await` it immediately returns control to `_ready()` which carries on, and then much later 5 appears because `wait_on_something()` is still running in the background, even though we carried on without it.

Finally, this is why using `await` in `_ready()` doesn't prevent the game from continuing, and why using it in `_process()` will cause it to fire repeatedly, because the Godot engine itself is following this rule. It waits to finish the rest of `_ready()` or `_process()`, but it carries on with out, to run the rest of the code and/or the next instance of `_process()`!

## Ternary-if Expressions

https://gdscript.com/tutorials/conditional-statements/

"This is a handy one-liner to assign a value to a variable based on a condition."

In other words, this is the equivalent of a "ternary" in Godot:

`var x = [value] if [expression] else [value]`

Code example:

```gdscript
var paid = false
var strength = 9.9 if paid else 1.0
print("Strength = ", strength)
```
