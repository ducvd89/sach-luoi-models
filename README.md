# Sách lười — mô hình đi kèm

Nơi giữ bản sao các file mô hình mà [Sách lười](https://github.com/ducvd89/sach-luoi)
tải về lúc chạy. Không có mã nguồn nào ở đây, chỉ là chỗ tải ổn định.

**Vì sao cần:** nguồn gốc trên HuggingFace có thể bị khoá hoặc gỡ bất cứ lúc nào — và đã
xảy ra: `neuphonic/neucodec-onnx-decoder-int8` chuyển sang chế độ hạn chế truy cập, khiến
mọi người dùng Sách lười không tải nổi engine VieNeu v2 nữa.

Các file ở đây là **bản sao nguyên vẹn**, không sửa đổi. Kiểm bằng SHA256 ghi kèm bên dưới.

## Tệp

### `neucodec_decoder_int8.onnx`

Bộ giải mã âm của NeuCodec, bản lượng tử int8, dùng cho engine VieNeu-TTS v2.

| | |
|---|---|
| Nguồn gốc | [neuphonic/neucodec-onnx-decoder-int8](https://huggingface.co/neuphonic/neucodec-onnx-decoder-int8) |
| Tác giả | Neuphonic |
| Giấy phép | Apache-2.0 |
| Kích thước | 312.292.102 byte |
| SHA256 | `3ddd9e56396e6029e0e948ac0255c89c803f981f23dcf4c154f50820bd74a6b3` |

## Giấy phép và ghi công

Các mô hình ở đây thuộc về tác giả gốc, không thuộc về dự án Sách lười.

**NeuCodec** — © Neuphonic, phát hành theo giấy phép **Apache License 2.0**. Toàn văn giấy
phép nằm trong file [`LICENSE-neucodec`](LICENSE-neucodec). File được phân phối lại nguyên
vẹn, **không chỉnh sửa gì**.

Apache-2.0 cho phép phân phối lại kèm điều kiện giữ nguyên giấy phép và ghi công — đó đúng
là việc kho này làm.
