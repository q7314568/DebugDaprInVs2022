# 在Visual Studio 2022 跑Debug mode for Dapr

## 前置需求

> 1. 需要安裝 [PowerShell 7 / Core](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3) (Example: dotnet tool install --global PowerShell)
> 
> 2. 需要Visual Studio extension [Microsoft Child Process Debugging Power Tool](https://marketplace.visualstudio.com/items?itemName=vsdbgplat.MicrosoftChildProcessDebuggingPowerTool2022)
>
> 3. 安裝完成後在開啟 Visual Studio 2022 :
>
>>偵錯->其他偵錯目標->Child Process Debugging Settings
>
> 設定方式如下圖

![Child Process Debugging Settings設定圖示](https://github.com/q7314568/DebugDaprInVs2022/blob/3a783f11e55e587285f4f77bf19923f69636f694/Child%20Process%20Debugging%20Settings.png?raw=true)


## launchSettings.json 調整

``` json
"Dapr-PWSH": {
      "commandName": "Executable",
      "executablePath": "pwsh",
      "commandLineArgs": "-Command \"dapr run --app-id DaprCounterASPNET --app-port 5000 --dapr-http-port 5005 --dapr-grpc-port 5006 -- dotnet run --no-build\"",
      "workingDirectory": ".",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      },
      "nativeDebugging": true
}
```


設定完按下F5進入 Debug mode即可。
