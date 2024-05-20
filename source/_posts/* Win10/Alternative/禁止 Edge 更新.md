即使关闭了系统更新, Edge 仍然会自动更新, 所以需要禁止

```shell
sc stop edgeupdate
sc stop edgeupdatem
sc config edgeupdate start= disabled
sc config edgeupdatem start= disabled
sc failure edgeupdate reset=0 actions=none
sc failure edgeupdatem reset=0 actions=none
:: delete task plan
schtasks /delete /TN "MicrosoftEdgeUpdateTaskMachineCore" /f
schtasks /delete /TN "MicrosoftEdgeUpdateTaskMachineUA" /f
```