## 计算机控制命令

名称 | 命令 
------------ | -------------
关机 | systemctl poweroff   
重启 | systemctl restart
挂起 | systemctl suspend
休眠 | systemctl hibernate
屏幕锁定 | loginctl lock-session
屏幕解锁 | loginctl unlock-session
屏幕关闭 | xset dpms force off
屏幕开启 | xset dpms force on

## 音量控制
名称 | 命令 
------------ | -------------
音量减 | qdbus org.kde.kglobalaccel /component/kmix invokeShortcut "decrease_volume"
音量加 | qdbus org.kde.kglobalaccel /component/kmix invokeShortcut "increase_volume"
静音 | qdbus org.kde.kglobalaccel /component/kmix invokeShortcut "mute"
麦克风静音 | qdbus org.kde.kglobalaccel /component/kmix invokeShortcut "mic_mute"

## 亮度调节
名称 | 命令 
------------ | -------------
亮度调高 | qdbus org.kde.Solid.PowerManagement /org/kde/Solid/PowerManagement/Actions/BrightnessControl org.kde.Solid.PowerManagement.Actions.BrightnessControl.setBrightness $(expr $(qdbus org.kde.Solid.PowerManagement /org/kde/Solid/PowerManagement/Actions/BrightnessControl org.kde.Solid.PowerManagement.Actions.BrightnessControl.brightness) + 375)
亮度降低 | qdbus org.kde.Solid.PowerManagement /org/kde/Solid/PowerManagement/Actions/BrightnessControl org.kde.Solid.PowerManagement.Actions.BrightnessControl.setBrightness $(expr $(qdbus org.kde.Solid.PowerManagement /org/kde/Solid/PowerManagement/Actions/BrightnessControl org.kde.Solid.PowerManagement.Actions.BrightnessControl.brightness) - 375)

## 截屏操作
名称 | 命令 
------------ | -------------
截屏 | spectacle -b
截屏至手机 | file=/tmp/$(hostname)_$(date "+%Y%m%d_%H%M%S").png; spectacle -bo "${file}" && kdeconnect-cli -d $(kdeconnect-cli -a --id-only) --share ${file}
投屏至手机 | file="$HOME/Pictures/WebcamImage_$(date "+%Y%m%d_%H%M%S").jpg"; ffmpeg -f video4linux2 -input_format mjpeg -s 1280x720 -i /dev/video0 -frames:v 1 "${file}" && kdeconnect-cli -d $(kdeconnect-cli -a --id-only) --share "${file}"

## 虚拟桌面控制
名称 | 命令
------------ | -------------
主桌面 | qdbus org.kde.KWin /KWin setCurrentDesktop 1
下一个桌面 | qdbus org.kde.KWin /KWin nextDesktop
上一个桌面 | qdbus org.kde.KWin /KWin previousDesktop
