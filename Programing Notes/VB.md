- Double click button to access code
- `MsgBox()` Creates an alert box popup
- `MessageBox.Show()` Is identical to the above command and is preferred over `MsgBox()`
- Lines **don't** end in a semicolon
- Instead of using curly brackets, VB uses statements to end. E.g. `End Sub` or `End Class`
- Declare a variable using the `Dim` statement. E.g. `Dim strFirstName as String`
- In early versions of VB you were required to use `Let` command to assign a variable
- Use `&` to concatenate strings
- Integer, Decimal, Double, Single
- Use hash symbols to enclose date variables `#11/2/2024#` Second of November
- `VbNewLine` = /n
- Put an underscore prior to adding a new line to make is a single line in code.
- `InputBox` for input
- `txtBox.Text` to collect input from text boxes on screen
- `lstBox.SelectedItem` to collect input from list of items 
- `lstBox.Items.Add` to add items to list box.
- `Mod` is VB version of %
- No parenthesis when using if statement 
- End if statements with end keyword
- Check if two values are equal with just a single `=` sign.
- 
```VB
If Value = true Then 

ElseIf

End If
```
- `Select Case` is the switch statement in VB and ends with `End Select`
- `To` to check between two numbers. E.g. `variable = 1 to 5`
- For statements end in `Next` 
```VB
    For variable = 1 to 5

    Next
```
- `Do While` loops end in `Loop`
- Declare arrays in the following way
```VB
    Dim astFruit(5) as String

    astFruit(0) = "test"
    astFruit(1) = "test"
    astFruit(2) = "test"
    astFruit(3) = "test"
    astFruit(4) = "test"
```