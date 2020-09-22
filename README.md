<div align="center">

## Ripple Effect


</div>

### Description

This is an ripple effect (well, it seems to be), which uses pure VB. My friends say, they look like ripples, but I don't. Just Hold the mouse over the form and move it.
 
### More Info
 
Something good (I hope)


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Butterkeks](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/butterkeks.md)
**Level**          |Beginner
**User Rating**    |4.4 (22 globes from 5 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[Custom Controls/ Forms/  Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/custom-controls-forms-menus__1-4.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/butterkeks-ripple-effect__1-32377/archive/master.zip)





### Source Code

```
Private Type RippleType
  X As Long
  Y As Long
  wid As Long
  color As Long
  speed As Integer
  Maxwid As Integer
End Type
Dim Ripple(0 To 250) As RippleType
Dim LeftP
Dim TopP
Dim Draw As Boolean
Sub Init(nr)
With Ripple(nr)
  .wid = 0
  .X = LeftP
  .Y = TopP
  .color = 255
  .speed = Int((40 * Rnd) + 20)
  .Maxwid = Int((2000 * Rnd) + 1)
End With
End Sub
Private Sub Form_Load()
For I = 0 To UBound(Ripple)
  Init I
Next I
End Sub
Private Sub Form_MouseDown(Button As Integer, Shift As Integer, X As Single, Y As Single)
Draw = True
End Sub
Private Sub Form_MouseMove(Button As Integer, Shift As Integer, X As Single, Y As Single)
If Draw = True Then
  LeftP = X
  TopP = Y
  Init I
End If
End Sub
Private Sub Form_MouseUp(Button As Integer, Shift As Integer, X As Single, Y As Single)
Draw = False
End Sub
Private Sub Timer1_Timer()
Me.Cls
For I = 0 To UBound(Ripple)
  With Ripple(I)
    .color = .color - .speed / 4
    If .color < 0 Then
      If Draw = True Then Init I
      If Draw = False Then .color = 0
    End If
    .wid = .wid + .speed
    If Draw = True Then
      If .wid > .Maxwid Then Init I
    End If
    Me.Circle (.X, .Y), .wid, RGB(0, 0, .color)
  End With
Next I
End Sub
```

