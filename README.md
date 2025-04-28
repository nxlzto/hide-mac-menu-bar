> [!TIP]
> To completely hide the Mac OS menu bar using Yabai.

### Automatically hide menu bar

1. Go to Control Center
   ![[/images/menu.png]]

### Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install Yabai

```bash
brew install koekeishiya/formulae/yabai
```

### Accessibility

1. Go to Privacy & Security > Accessibility
   ![[/images/yabai.png]]

### .yabairc

```bash
#1 create yabairc file
vim ~/.yabairc

#2 copy the following content to .yabairc
yabai -m config menubar_opacity 0.0
```

### Start & Stop yabai

```bash
# start
yabai --start-service

# stop
yabai --stop-service
```

### Raycast script

> vim ~/raycast/scripts/yabai.sh

```bash
#!/bin/bash

# @raycast.schemaVersion 1
# @raycast.title Yabai Service
# @raycast.mode silent
# @raycast.packageName System
# @raycast.description Toggle Yabai window manager service (start/stop)
# @raycast.author nxlz

# 检查 yabai 是否正在运行
if pgrep -f yabai >/dev/null; then
  # 如果 yabai 在运行，则停止服务
  yabai --stop-service
  if [ $? -eq 0 ]; then
    echo "Yabai service stopped successfully"
  else
    echo "Failed to stop Yabai service"
  fi
else
  # 如果 yabai 未运行，则启动服务
  yabai --start-service
  if [ $? -eq 0 ]; then
    echo "Yabai service started successfully"
  else
    echo "Failed to start Yabai service"
  fi
fi

```

### Reference

![[/images/raycast.png]]
