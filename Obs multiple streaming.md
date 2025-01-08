### Bung cấu hình đã tinh chỉnh

- Mở "Run" gõ `%appdata%`, thư mục "Roaming" mở ra;
- Bung file nén "Obs studio config.7z" vào thư mục "Roaming" đó


### Chỉnh giọng nói trong livestream, cài thêm tập tin VST

- Kho các VST miễn phí: https://plugins4free.com
- Tạo thư mục chứa plugin VST: "C:\Program Files\VSTPlugins"
- Tải các VST cần thiết rồi thả vào thư mục tạo bên trên


### Bật livestream đa kênh

Để live được đa nền tảng cần cài thêm plugin [Obs multi rtmp](https://github.com/sorayuki/obs-multi-rtmp/releases). Nếu chưa biết dùng, xem hướng dẫn này [youtube.com](https://www.youtube.com/watch?v=z8r2ScBSEyU)

Chỉnh màn hình dọc:
- Mở `Settings`, cột bên trái chọn `Stream`, ấn vào ô `Ignore streaming service setting recommendations`
- Vẫn trong `Settings`, cột bên trái chọn `Video`, thay đổi tỉ lệ dọc ví dụ "1080x1920"


### Cấu hình đầu ra cho loại CPU & GPU

Mở `Settings`, cột bên trái chọn `Ouputs`, ấn vào tab `Streaming`:
1. Cho AMD Radeon:
    - Video encoder: `AMD HW H.264`
    - Rate control: `CBR`
    - Bitrate: `6000 Kbps`
    - Keyframe interval (0 = auto): `2`
    - Preset: `Quality`
    - Profile: `High`
    - Max B-frames: `1`
    - AMF/FFmpeg Options:
`MaxNumRefFrames=4 HighMotionQualityBoostEnable=1 EnableVBAQ=false RateControlPreanalysisEnable=0 BReferenceEnable=true AdaptiveMiniGOP=false RateControlSkipFrameEnable=false EnablePreAnalysis=true PASceneChangeDetectionEnable=false PAHighMotionQualityBoostMode=1 PATemporalAQMode=1 PAFrameSadEnable=true HalfPixel=True QuarterPixel=True DeBlockingFilter=True FillerDataEnable=True`
1. Cho Nvidia Geforce:
    - Video encoder: `NVIDIA NVENC H.264`
    - Rate control: `Constant Bitrate`
    - Bitrate: `6000 Kbps`
    - Keyframe interval (0 = auto): `2`
    - Preset: `P6: Slower (Better Quality)`
    - Tuning: `High Quality`
    - Multipass Mode: `Two Passes (Full Resolution)`
    - Profile: `High`
    - Look-ahead: unchecked
    - B-frames: `1`


Mở `Settings`, cột bên trái chọn `Ouputs`, ấn vào tab `Recording`:
1. Cho Intel Iris:
    - Video encoder: `QuickSync H.264`
    - Rate control: `ICQ`
    - ICQ quality: `18`
    - Target usage: `TU1: Slowest (Best quality)`
    - Profile: `High`
    - Key: `0`
    - Latency: `ultra-low`
    - B-frames: `0`

> `Keyframe interval`: 0 đến 2, không quan trọng nếu đang ghi<br/>
> `ICQ quality` có giá trị từ 0 đến 50, 0 là lossless, tỉ lệ nén tốt nhất từ 18-25 cho hình không bị xấu<br/>
> `B-frames` giúp giảm kích thước video lợi cho đường truyền nhưng làm phức tạp bộ mã hóa và tăng độ trễ (latency) khi phát live, nên để tối đa không quá `2` hoặc `0`<br/>
> Tham khảo rõ hơn về B-frames: https://www.linkedin.com/pulse/b-frames-ultra-low-latency-encoding-parking-lot-rules<br/>
> (Nvidia) `Lookahead`: Unchecked, chỉ hữu dụng với phát live nội dung có low-motion<br/>
> (Nvidia) `Adaptive Quantization/Psychovisual Tuning`: Unchecked, không cần thiết cho Recording


#### Kênh livestream

##### Shopee
- Tạo phiên live: [https://live.shopee.vn/pc/setup](https://live.shopee.vn/pc/setup)
