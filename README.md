# Android Device Monitor - Android logcat tool

- Để tìm bug khi build game ra thiết bị android thì mọi người hay dùng tool nào? Ngoài sử dụng `Android Studio` hoặc vào package manager của unity để cài tool `Android Logcat` thì mình thấy khá ít anh em biết có sự tồn tại của một tool logcat nữa đươc tích hợp sẵn khi mọi người cài unity editor.
- Tool mà mình đang nói đến là `Android Device Monitor`, mình thường dùng tool này là chủ yếu vì mình thấy giao diện của nó khá giống với log của `Android Studio` mà lại không phải cài thêm `Android Studio` gây tốn thêm bộ nhớ cho máy tính.

![monitor_device](https://github.com/user-attachments/assets/6aa8740a-cb9a-4e51-bffd-b70d8a91657f)

### Lưu ý

- Chạy trên window (máy mac thì bỏ qua luôn)
- Trong máy phải có java sdk 8 (cái này nếu k mở được lên thì chỉ cần down bừa một bản java sdk 8 về cài vào máy là chạy được, không phải setup thêm gì [Mình ghim 1 version java sdk 8 ở đây nhé](https://github.com/unityvn/android_device_monitor_tool_logcat/releases/download/1.0.0/JavaSetup8u441.exe))

### Cách dùng

- Lấy SDK path trong unity

![sdk_path](https://github.com/user-attachments/assets/48cce3c0-08d6-41fd-a77c-786cd8f9f356)

- Mở theo sdk path > tools > monitor

![monitor](https://github.com/user-attachments/assets/a8eab629-cf13-4340-911c-2b5eb351926e)

Đến đây chỉ cần mở monitor lên và dùng thôi (nếu mở thông thường không được thì hãy thử mở bằng Administrator)

- Hoặc ném method này vào static class nào đó rồi gọi nó ra cũng có thể mở được Monitor lên nhé

```csharp
        public static void OpenMonitor()
        {
            string path = $"{AndroidExternalToolsSettings.sdkRootPath}/tools/monitor.bat";
            if (File.Exists(path))
            {
                Process process = new Process();
                process.StartInfo.FileName = path;
                process.StartInfo.Verb = "runas";
                process.StartInfo.WindowStyle = ProcessWindowStyle.Hidden;
                process.Start();
            }
        }
```

`Chúc anh em nghịch thành công!`
