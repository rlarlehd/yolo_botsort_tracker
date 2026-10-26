# 02. 객체 추적 (YOLOv8 + BoT-SORT)

| 파일 | 설명 |
|---|---|
| `botsort_test.ipynb` | `yolov8s.pt`로 RTSP 영상을 30초간 추적(`model.track(persist=True)`, 기본 BoT-SORT). 사람(class 0)만 골라 ID·박스와 최근 30프레임 궤적을 그려 `tracking_video.mp4`로 저장 |
| `yolo_track.ipynb` | `MultiStreamTracker` 클래스: 2채널을 캡처/추론/표시 스레드와 `Queue`로 분리해 동시에 추적하고, 객체 특징 벡터를 채널 간 L2 거리로 비교. `stream1_<시간>.mp4`, `stream2_<시간>.mp4`로 녹화 |

- 가중치(`yolov8n.pt`, `yolov8s.pt`)는 `.gitignore`로 제외되며, `ultralytics`가 첫 실행 시 자동으로 받습니다.
- 실행 전에 RTSP 주소의 `<USER>:<PASSWORD>@<CAMERA_IP>`를 바꾸세요.

## 참고
- `botsort_test.ipynb`: 추적 대상이 없는 프레임에서는 `results[0].boxes.id`가 `None`이라 `.int()` 호출에서 오류가 납니다.
- `stream*_20250218_011712.mp4`는 44바이트짜리 빈 파일입니다(녹화 실패분).
