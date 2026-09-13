# Sách lười — mô hình đi kèm

Nơi giữ bản sao các file mô hình mà [Sách lười](https://github.com/ducvd89/sach-luoi)
tải về lúc chạy. Không có mã nguồn nào ở đây, chỉ là chỗ tải ổn định.

**Vì sao cần:** nguồn gốc trên HuggingFace có thể bị khoá hoặc gỡ bất cứ lúc nào — và đã
xảy ra: `neuphonic/neucodec-onnx-decoder-int8` chuyển sang chế độ hạn chế truy cập, khiến
mọi người dùng Sách lười không tải nổi engine VieNeu v2 nữa.

Từng file mô hình được giữ **nguyên vẹn, không sửa một byte nào**. Việc duy nhất kho này
làm là gói chúng lại thành file `.zip` để tải một lượt thay vì chín lượt — bung ra là được
lại đúng file gốc. Gói giọng Piper thì để nguyên `.tar.bz2` như bản của sherpa-onnx.

## Tệp

Bảng dưới là của bản phát hành [`v1`](../../releases/tag/v1). SHA256 tính trên chính file
`.zip`/`.tar.bz2` hoặc từng file mô hình tải về.

### Engine VieNeu-TTS v3 Turbo

| Gói | Byte | SHA256 |
|---|---|---|
| `vieneu-v3.zip` | 152.508.042 | `19dbe3d0d4ab4f24a9d7709892d597a1fee37890b5d26807e2e9e461785a15ab` |
| `vieneu-v3-enroll.zip` | 73.637.992 | `4f44b6851daf4fc91fa55cd1270ae9620a187e52f3a5aef4d5dbd0e69942607c` |

`vieneu-v3.zip` gồm mạng sinh âm (`model/`) và bộ giải mã âm MOSS-Audio-Tokenizer-Nano
(`codec/`). `vieneu-v3-enroll.zip` chỉ cần khi thêm giọng: bộ mã hoá người nói và bộ mã
hoá âm.

Nguồn: [pnnbao-ump/VieNeu-TTS-v3-Turbo](https://huggingface.co/pnnbao-ump/VieNeu-TTS-v3-Turbo)
và [OpenMOSS-Team/MOSS-Audio-Tokenizer-Nano-ONNX](https://huggingface.co/OpenMOSS-Team/MOSS-Audio-Tokenizer-Nano-ONNX).

### Engine VieNeu-TTS v2

| Gói | Byte | SHA256 |
|---|---|---|
| `vieneu-v2.zip` | 501.451.219 | `7de9ff0fe85be7563be783a98b88f5142aed7180a5d752976c08159167ba9eff` |
| `vieneu-v2-encoder.zip` | 518.615.976 | `fac6e26d1fca7393d6b2ce24d1ad261b2f1cc9ed83f36e3059b97ea5feaa8eea` |

`vieneu-v2.zip` gồm mô hình ngôn ngữ Q4 dạng GGUF, bộ giải mã NeuCodec int8
(`neucodec_decoder_int8.onnx`, 312.292.102 byte) và hồ sơ giọng.
`vieneu-v2-encoder.zip` là bộ **mã hoá** NeuCodec, chỉ cần khi thêm giọng.

Nguồn: [pnnbao-ump/VieNeu-TTS-v2](https://huggingface.co/pnnbao-ump/VieNeu-TTS-v2),
[neuphonic/neucodec-onnx-decoder-int8](https://huggingface.co/neuphonic/neucodec-onnx-decoder-int8)
(nay đã hạn chế truy cập) và [neuphonic/distill-neucodec](https://huggingface.co/neuphonic/distill-neucodec).

### Giọng Piper

| Gói | Byte | SHA256 |
|---|---|---|
| `vits-piper-vi_VN-vais1000-medium.tar.bz2` | 67.154.040 | `fa1367710767d36ed5cf13b4a449e20c35ffd12791c2e47c2e64142bfa55551a` |
| `vits-piper-vi_VN-25hours_single-low.tar.bz2` | 67.059.380 | `8aa8bbe88a1cb26ef4f33de56fced1720e72ec00491d23a3551de25a53c75149` |
| `vits-piper-vi_VN-vivos-x_low.tar.bz2` | 33.409.065 | `bee4ce76bdf4cc82c17b451c40d6244c5e87d2e847703ab4986c3243c43f8a5d` |

Nguồn: bản phát hành của [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx/releases).

### Kiểm âm wav2vec2 tiếng Việt

Hai file giữ nguyên nội dung từ revision `ded9b63317d3efdb0d0422fd05592efb43cdee10`
của [galamkhoahoc/wav2vec2-vi-phone-ONNX](https://huggingface.co/galamkhoahoc/wav2vec2-vi-phone-ONNX).
Theo manifest ONNX, mô hình gốc là
[tuanio/wav2vec2-base-finetune-vi_phone-non_freeze-spec_aug-500epoch](https://huggingface.co/tuanio/wav2vec2-base-finetune-vi_phone-non_freeze-spec_aug-500epoch).
Ứng dụng dùng bản int8 để nhận dạng âm vị và đếm âm tiết, chạy offline.

| File trên release v1 | Byte | SHA256 |
|---|---|---|
| `wav2vec2-vi-phone-model_quantized.onnx` | 122.435.778 | `c4c7503ce9c0ab43cdb31fb8b5a6cb1fc1d0693281ac9bc473cdf6cee09e8a29` |
| `wav2vec2-vi-phone-phonemes.json` | 1.636 | `71616f1fad5bb7224c45852eaa629837635523f8c02d9dedcf89ea3c2b737181` |

Tên gốc lần lượt là `onnx/model_quantized.onnx` và `phonemes.json`. Tiền tố trên release
chỉ tránh trùng tên với mô hình khác; app lưu lại thành `model_quantized.onnx` và
`phonemes.json`, kiểm dung lượng và SHA256 trước khi dùng.

## Một lưu ý cho ai dựng lại các gói này

Đường dẫn bên trong file zip **phải dùng dấu `/`**, không dùng dấu gạch ngược. Đặc tả zip
(APPNOTE mục 4.4.17.1) quy định vậy, nhưng vài công cụ nén trên Windows vẫn ghi dấu gạch
ngược — và khi ấy Android coi cả cụm `model\config.json` là *tên file* nằm ở thư mục gốc.
Bung không báo lỗi gì, chỉ là bung xong rồi vẫn thiếu file. Windows không lộ ra vì ở đó
dấu gạch ngược cũng là dấu phân cách, nên lỗi chỉ hiện trên điện thoại.

## Giấy phép và ghi công

Các mô hình ở đây thuộc về tác giả gốc, không thuộc về dự án Sách lười.

**NeuCodec** — © Neuphonic, phát hành theo giấy phép **Apache License 2.0**. Toàn văn giấy
phép nằm trong file [`LICENSE-neucodec`](LICENSE-neucodec).

**VieNeu-TTS** — © pnnbao-ump, phát hành theo giấy phép **CC BY-NC 4.0**: phi thương mại
và phải ghi công tác giả.

**MOSS-Audio-Tokenizer** — © OpenMOSS Team, Apache-2.0.

**Piper / VITS** — mô hình do k2-fsa đóng gói, giấy phép theo từng giọng ghi trong chính
gói tải về.

**wav2vec2 âm vị tiếng Việt** — nguồn ONNX: galamkhoahoc; mô hình huấn luyện: tuanio.
Hai kho nguồn chưa công bố giấy phép tại thời điểm tích hợp. Không gán cho các trọng số
này giấy phép của ứng dụng hay giấy phép của các mô hình khác trong kho.
