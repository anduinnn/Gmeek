
## 延长更新暂停时间

**第一步：设置注册表**

1. 右键点击"开始"按钮，选择"以管理员身份运行"打开命令提示符

2. 复制以下命令并粘贴到CMD窗口中：

   ```sh
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings" /v FlightSettingsMaxPauseDays /t reg_dword /d 36500 /f
   ```

3. 按回车键执行命令

**第二步：在设置中暂停更新**

根据你的Windows版本，操作方式稍有不同：

- **Windows 11用户**：打开设置 → Windows 更新 → 暂停更新 → 现在可以选择延长最高4641周
- **Windows 10用户**：打开设置 → 更新和安全 → Windows 更新 → 高级选项 → 暂停更新

## 恢复系统更新

1. 同样以管理员身份打开命令提示符

2. 执行这个命令将暂停天数恢复默认：

   ```sh
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings" /v FlightSettingsMaxPauseDays /t reg_dword /d 1 /f
   ```

3. 进入设置 → Windows更新 → 点击"恢复更新"按钮



> reg add 这个命令的作用是修改Windows注册表,
原本Windows只允许暂停更新几周时间，通过修改注册表中的`FlightSettingsMaxPauseDays`值，我们可以大幅延长这个限制.
> 将`FlightSettingsMaxPauseDays`的值重新设置为1天，恢复到Windows系统的默认限制。这样系统就会按照原来的规则，只允许短期暂停更新。

