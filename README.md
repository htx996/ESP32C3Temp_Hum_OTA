# ESP32-C3 Temp/Hum Remote OTA

把本目录内容上传到 GitHub 仓库 `htx996/ESP32C3Temp_Hum_OTA` 的 `main` 分支根目录，并在仓库 Settings -> Pages 中启用 GitHub Pages。

固件默认读取：

```text
https://htx996.github.io/ESP32C3Temp_Hum_OTA/manifest.json
```

`manifest.json` 字段：

- `version`: 页面显示版本，例如 `2026.5.17`
- `version_num`: 固件比较用数字，必须比当前固件大才提示更新；现在应直接使用本次构建生成的 `build/generated/build_version.h` 里的 `APP_BUILD_VERSION_NUMBER`
- `url`: OTA app `.bin` 下载地址；文件名应包含 `version` 和 `version_num`，例如 `firmware/esp32_c3_guangzhanwenshidu-2026.5.17-1779023424.bin`
- `sha256`: app `.bin` 的 SHA-256
- `size`: app `.bin` 字节数

注意：这里上传的是 `idf.py build` 生成的 app `.bin`，不是 merged-flash `.bin`。远程 OTA 只写入 OTA app 分区。

说明：`APP_BUILD_FIRMWARE_VERSION` 仍然显示为日期，例如 `2026.5.17`；但 `APP_BUILD_VERSION_NUMBER` 已改成更细粒度的构建时间戳，因此同一天内多次编译并发布到 OTA 服务器，也能正确检测到更新。
