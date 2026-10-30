# Changelog

## [1.1.0] - 2026-10-13

- Bổ sung enum `MobileIdScope` (`PHONE_VERIFY`, `PHONE`, `MOBILE_ID`) và các overload xác thực đa scope.
- Bổ sung tham số `state` tuỳ chọn trong hàm `doAuthentication` để hỗ trợ định danh phiên xác thực.
- Cung cấp hàm `configure` trả về raw JSON chuỗi response.
- Tối ưu hóa hiệu năng và độ ổn định của SDK.

## [1.0.3] - 2026-09-14

### Added

- Hỗ trợ overload `configure(configUrl, headers, onSuccess, onError)` trả về chuỗi Raw JSON String để đối tác có thể nhận các metadata tuỳ biến từ backend.
- Bổ sung trường `rawResponse: String?` vào `MobileIdError` để trả về phản hồi thô từ server khi yêu cầu cấu hình thất bại.

### Changed

- Cập nhật tài liệu `README.md` với hướng dẫn sử dụng cấu hình Raw JSON string và xử lý lỗi với `rawResponse`.

## [1.0.0] - 2026-07-21

- Bản phát hành đầu tiên
