# Changelog

## [1.0.3] - 2026-09-14

### Added

- Hỗ trợ overload `configure(configUrl, headers, onSuccess, onError)` trả về chuỗi Raw JSON String để đối tác có thể nhận các metadata tuỳ biến từ backend.
- Bổ sung trường `rawResponse: String?` vào `MobileIdError` để trả về phản hồi thô từ server khi yêu cầu cấu hình thất bại.

### Changed

- Cập nhật tài liệu `README.md` với hướng dẫn sử dụng cấu hình Raw JSON string và xử lý lỗi với `rawResponse`.

## [1.0.0] - 2026-07-21

- Bản phát hành đầu tiên
