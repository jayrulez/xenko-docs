## Value changes ignored at runtime
  
When you add a script to your project as a component, Game Studio lists its public variables in the component's Properties grid. These are the values used at runtime. However, if you then change a value in the script, Game Studio doesn't update the component with the new value.

For example, imagine you have a script with the variable `SpeedFactor` with the value `5.0f`. You add the script to the project as a component. Now, in the script, you change the `SpeedFactor` variable to `6.0f`, save the script, and run the project. Game Studio doesn't update the component, so the speed `SpeedFactor` value is still `5.0f`.

## Fix

In your project, delete and re-add the script component.

Alternatively, if you want Game Studio to update the values in the component properties after you change them in the script, you can do this with additional code. You need to add a new line of code for every property you want this to apply to.

1. Add `using System.ComponentModel` at the top of the script.

2. Above the value you want to update, add ``[DefaultValue()]``. For example:

```
[DefaultValue(6.0f)]
public float SpeedFactor { get; set; } = 6.0f;
```

When you change the value, update both the `SpeedFactor` and the `DefaultValue` to the same value.

> [!Note]
> This doesn't work in both directions. In Game Studio, if you set a value other than the `DefaultValue`, the value is saved in Game Studio only. If you then change a value directly in the script, Game Studio no longer updates the component with the new value.