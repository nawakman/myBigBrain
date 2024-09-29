[[GAMEDEV]]]
```
;RuleOfThree
#SingleInstance force

^+++x::																				;ctrl + shift + x
	Gui,Destroy
	Gui,Add,Text,,What to get?
	Gui,Add,DropDownList,vWhichRes,get resolution X||get resolution Y
	Gui,Add,Button,+Default wp gbtn_get_X,OK
	Gui,Show,,RoT
	return

		btn_get_X:
			Gui,Submit
			Gui,Destroy
			Gui,Add, Text,,enter X:
			Gui,Add, Edit,vResX1,
			Gui,Add,Button,+Default wp gbtn_get_Y,OK
			Gui,Show,,RoT
			return

		btn_get_Y:
			Gui,Submit
			Gui,Destroy
			Gui,Add, Text,,enter Y:
			Gui,Add, Edit,vResY1,
			Gui,Add,Button,+Default wp gbtn_which_res,OK
			Gui,Show,,RoT
			return

		btn_which_res:
			Gui,Submit
			Gui,Destroy
			if WhichRes = get resolution X
			{
				Gui,Add,Text,,enter second Y:
				Gui,Add,Edit,vResY2,
				Gui,Add,Button,+Default wp gbtn_calculate_X,OK
				Gui,Show,,RoT
				return
			}

			if WhichRes = get resolution Y
			{
				Gui,Add,Text,,enter second X:
				Gui,Add,Edit,vResX2,
				Gui,Add,Button,+Default wp gbtn_calculate_Y,OK
				Gui,Show,,RoT
				return
			}

			btn_calculate_X:
				Gui,Submit
				Gui,Destroy
				X_result := % ((ResY2*ResX1)/ResY1)									;rule of three
				X_result:= SubStr(X_result,1,InStr(X_result, .)-1)					;remove everything after "."
				sendinput,% X_result
				return 


			btn_calculate_Y:
				Gui,Submit
				Gui,Destroy
				Y_result := % ((ResX2*ResY1)/ResX1)									;rule of three
				Y_result:= SubStr(Y_result,1,InStr(Y_result, .)-1)					;remove everything after "."
				sendinput,% Y_result
				return
```

Ctrl+Shift+X to open the script when running