# EchoSight-An-AI-Driven-Wearable-Device

**EchoSight** is an assistive AI system designed to help visually impaired individuals by providing real-time voice feedback of detected faces and objects along with their proximity. It uses YOLOv4-tiny for object detection, facial recognition for known individuals, and WebSocket communication to fetch distance data from an ultrasonic sensor (NodeMCU).

## 🔧 Features

- 🎯 Real-time face recognition using dlib and OpenCV
- 📦 Object detection with YOLOv4-tiny and COCO dataset
- 🔊 Audio feedback using `pyttsx3` text-to-speech engine
- 📡 Distance measurement via WebSocket from an ultrasonic sensor (NodeMCU)
- 🧠 Recognizes known individuals from the `images/` folder and greets them
- 🦺 Announces detected objects along with distance in cm

## 📁 Project Structure

```
EchoSight/
├── dlib/
├── images/
│   └── your_face.jpg
├── main.py
├── SimpleFaceRecognition.py
├── yolov4-tiny.cfg
├── yolov4-tiny.weights
├── coco.names
├── README.md
└── __pycache__/
```

## 🧰 Requirements

Install the following Python libraries:

```bash
pip install opencv-python numpy pyttsx3 websocket-client
```

Also ensure you have dlib and face_recognition:

```bash
pip install dlib face_recognition
```

⚠️ **Note**: Installing dlib may require CMake and compatible Visual Studio build tools on Windows.

## 🚀 How to Run

1. Clone or download the project folder.
2. Make sure your webcam and NodeMCU (for ultrasonic distance) are connected.
3. Add known faces (JPEG or PNG) to the `images/` directory. The filename (excluding extension) will be used as the name.
4. Ensure the IP address in the code matches your NodeMCU WebSocket IP:
   ```python
   ws = websocket.WebSocketApp("ws://<Your_NodeMCU_IP>:81", on_message=on_message)
   ```
5. Run the main script:
   ```bash
   python main.py
   ```
6. Press `Esc` key to exit the program.

## 🧠 How it Works

- **Face Recognition**: Uses dlib's face embeddings to match against known faces stored in the `images/` folder.
- **Object Detection**: Utilizes YOLOv4-tiny to identify everyday objects from the COCO dataset.
- **Distance Detection**: Fetches distance data in real-time via WebSocket from a NodeMCU connected to an ultrasonic sensor.
- **Speech Output**: Announces newly detected people or objects and their distance using the TTS engine.

## 📷 Sample Output

When a face or object is detected:

```
Hello, Dheeraj
There is a person at 45 cm
There is a bottle at 30 cm
```

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
