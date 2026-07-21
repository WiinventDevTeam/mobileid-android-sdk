# MobileID Android SDK

SDK xác thực số điện thoại di động cho Android

Yêu cầu: minSdk 21, Java 11.

## Cài đặt

1. Thêm Maven repo của MobileID vào `repositories` (trong `settings.gradle` với dependency
   resolution management, hoặc root `build.gradle`):

   ```gradle
   repositories {
       google()
       mavenCentral()
       maven { url "https://raw.githubusercontent.com/WiinventDevTeam/mobileid-android-sdk/main/maven" }
   }
   ```

2. Thêm dependency trong `build.gradle` cấp **module app**:

   ```gradle
   dependencies {
       implementation "com.github.WiinventDevTeam:mobileid-android-sdk:1.0.0"
   }
   ```

## Sử dụng nhanh

SDK nhận cấu hình lúc runtime qua `configure(configUrl:)` — trỏ tới endpoint cấu hình
của backend bạn. Không cần khai gì thêm trong app.

```kotlin
val sdk = MobileIdSdk(activity)

// 1. Nạp cấu hình từ backend.
sdk.configure(
    configUrl = "https://your-backend.com/api/sdk-config",
    onSuccess = {
        // 2. Kiểm tra coverage rồi xác thực.
        sdk.checkCoverageWithPhoneNumber(
            "84901234567",
            onSuccess = {
                sdk.doAuthentication("84901234567", object : AuthListener {
                    override fun onSuccess(result: String) { /* đổi result với backend lấy token */ }
                    override fun onFail(result: MobileIdError) { /* xử lý lỗi */ }
                })
            },
            onError = { error -> /* xử lý lỗi */ }
        )
    },
    onError = { error ->
        // Lỗi resolve cấu hình (mạng, backend từ chối, app không được phép…).
    }
)
```

`configure` nhận thêm tham số `headers: Map<String, String>` (tùy chọn) nếu backend của
bạn yêu cầu header auth riêng (vd `Authorization`). SDK không quy định cơ chế auth.

### Xử lý lỗi

`MobileIdError` gồm `errorCode` và `errorMessage`. Nên xử lý theo `errorCode`.

> **Lưu ý**: xác thực qua mạng di động cần thiết bị thật kết nối **cellular data** —
> không chạy được trên Wifi hoặc emulator.
