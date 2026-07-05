# Meta Business Suite Voice Note Extension

A lightweight, powerful Google Chrome Extension that integrates a seamless Voice Note recording feature directly into Meta Business Suite and Facebook Messenger.

## Key Features

- **Native UI Integration**: Adds a sleek microphone button right next to the attachment icon in Facebook Messenger and Meta Business Suite.
- **High-Quality AAC Encoding**: Uses modern **WebCodecs API (`AudioEncoder`)** to record and encode voice notes in crisp AAC-LC format (44.1kHz, Stereo, 64kbps) directly on your device's hardware, ensuring immediate processing without heavy WebAssembly libraries.
- **Cross-Platform Compatibility**: The exported `.m4a` files are perfectly compatible with Android, PC Web, and strictly adhere to **iOS Instagram** voice note format requirements.
- **Live Visualizer**: Displays a dynamic, real-time audio waveform visualizer while recording.
- **Floating Controls**: Intuitive UI to cancel or send voice notes on the fly.
- **No External Servers**: 100% client-side processing ensuring total privacy and maximum speed.

## How It Works

1. **Audio Capture**: The extension uses `getUserMedia` to capture raw PCM audio from your microphone.
2. **WebCodecs Encoding**: `AudioData` frames are passed into the browser's native `AudioEncoder` configured for the `mp4a.40.2` (AAC-LC) codec.
3. **Muxing**: The raw AAC chunks are muxed into an MP4 container in real-time using `mp4-muxer` (~73KB footprint).
4. **Sending**: The final `.m4a` file is seamlessly injected into the chat's file attachment input and dispatched automatically.

## Installation

### Developer Mode (Local)
1. Clone or download this repository.
2. Open Google Chrome and navigate to `chrome://extensions/`.
3. Enable **"Developer mode"** in the top right corner.
4. Click **"Load unpacked"** and select the folder containing this extension.
5. Open Facebook Messenger or Meta Business Suite and look for the new microphone icon in the chat bar!

## Technical Specifications
- **Format**: `audio/mp4` (Container: MP4, Codec: AAC-LC)
- **Dependencies**: [mp4-muxer](https://github.com/Vanilagy/mp4-muxer) (Extremely lightweight MP4 container muxer)
- **Minimum Browser Requirement**: Google Chrome v104+ (Required for WebCodecs API support)

## Permissions Required
- `activeTab`: To interact with the current Facebook/Meta tab.
- `scripting`: To inject the recording logic and UI into the page.
- `microphone` (Host permission): To record audio natively.

## License
MIT License