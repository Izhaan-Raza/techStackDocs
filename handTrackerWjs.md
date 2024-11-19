

# Handtrack.js Hand Detection Example


## Introduction

Handtrack.js is a JavaScript library for detecting hands in real-time directly in the browser using a webcam. This example demonstrates how to use Handtrack.js to set up a webcam feed, detect hands, and display bounding boxes around detected hands.

## Installation

To use Handtrack.js, include the following CDN link in your HTML file:

```html
<script src="https://cdn.jsdelivr.net/npm/handtrackjs@latest/dist/handtrack.min.js"></script>
```

## Usage

### 1. Importing the Library

Include Handtrack.js in your HTML file to access its functions and models:

```html
<script src="https://cdn.jsdelivr.net/npm/handtrackjs@latest/dist/handtrack.min.js"></script>
```

### 2. Loading the Model

Use `handTrack.load()` to load the hand detection model. This function returns a promise that resolves with a model object, which you can use for detection.

```javascript
let model;
handTrack.load().then(loadedModel => {
    model = loadedModel;
    console.log("Handtrack.js model loaded");
});
```

### 3. Starting Video

To start the webcam video, use `handTrack.startVideo()`. This function prompts the user for webcam access and starts the video feed if permission is granted.

```javascript
const webcamVideo = document.querySelector('.webcamVideo');

handTrack.startVideo(webcamVideo).then(status => {
    if (status) {
        console.log("Webcam started");
    } else {
        console.log("Please enable webcam access");
    }
});
```

### 4. Detecting Hands

After starting the video and loading the model, use `model.detect()` to get predictions on each frame. This method returns an array of predictions with bounding box information.

```javascript
function detectHands() {
    model.detect(webcamVideo).then(predictions => {
        console.log("Predictions: ", predictions);
    }).catch(err => {
        console.error("Error during hand detection:", err);
    });
}
```

### 5. Drawing Bounding Boxes

To visualize detection results, draw bounding boxes on a canvas element overlaying the video feed.

```javascript
const canvas = document.querySelector('.canvas');
const context = canvas.getContext('2d');

function detectAndDrawHands() {
    model.detect(webcamVideo).then(predictions => {
        context.clearRect(0, 0, canvas.width, canvas.height);

        predictions.forEach(prediction => {
            const [x, y, width, height] = prediction.bbox;
            context.strokeStyle = 'red';
            context.lineWidth = 2;
            context.strokeRect(x, y, width, height);
            context.fillStyle = 'red';
            context.fillText(prediction.label, x, y - 10);
        });
    });
}
```

### 6. Continuous Detection

To detect hands continuously, you can use `setInterval` or `requestAnimationFrame` to call the detection function at regular intervals.

```javascript
function startDetectionLoop() {
    webcamVideo.addEventListener('loadeddata', () => {
        canvas.width = webcamVideo.videoWidth;
        canvas.height = webcamVideo.videoHeight;
        setInterval(detectAndDrawHands, 100); // Adjust interval as needed
    });
}
```

## Complete Example

Here is the complete HTML and JavaScript code for setting up hand detection with Handtrack.js:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Handtrack.js Example</title>
    <style>
        .webcamVideo, .canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            object-fit: cover;
        }
    </style>
</head>
<body>
    <video class="webcamVideo" autoplay></video>
    <canvas class="canvas"></canvas>

    <script src="https://cdn.jsdelivr.net/npm/handtrackjs@latest/dist/handtrack.min.js"></script>
    <script>
        let model;
        const webcamVideo = document.querySelector('.webcamVideo');
        const canvas = document.querySelector('.canvas');
        const context = canvas.getContext('2d');

        // Load the Handtrack.js model
        handTrack.load().then(loadedModel => {
            model = loadedModel;
            console.log("Handtrack.js model loaded");

            // Start video
            handTrack.startVideo(webcamVideo).then(status => {
                if (status) {
                    console.log("Webcam started");
                    startDetectionLoop();
                } else {
                    console.log("Please enable webcam access");
                }
            });
        });

        // Detect hands and draw bounding boxes
        function detectAndDrawHands() {
            model.detect(webcamVideo).then(predictions => {
                context.clearRect(0, 0, canvas.width, canvas.height);

                predictions.forEach(prediction => {
                    const [x, y, width, height] = prediction.bbox;
                    context.strokeStyle = 'red';
                    context.lineWidth = 2;
                    context.strokeRect(x, y, width, height);
                    context.fillStyle = 'red';
                    context.fillText(prediction.label, x, y - 10);
                });
            });
        }

        // Start the detection loop
        function startDetectionLoop() {
            webcamVideo.addEventListener('loadeddata', () => {
                canvas.width = webcamVideo.videoWidth;
                canvas.height = webcamVideo.videoHeight;
                setInterval(detectAndDrawHands, 100); // Adjust as needed
            });
        }
    </script>
</body>
</html>
```

## Functions Reference

- **`handTrack.load()`**: Loads the hand tracking model.
- **`handTrack.startVideo(videoElement)`**: Starts video from the webcam.
- **`model.detect(videoElement)`**: Detects hands in the provided video element and returns an array of predictions.

Each prediction object contains:
- `bbox`: Bounding box `[x, y, width, height]`
- `label`: Detected object label (e.g., "open" or "closed" for hand)
- `score`: Confidence score for the prediction

## Notes

- **Browser Compatibility**: Handtrack.js works in modern browsers with WebRTC support.
- **Performance**: Running continuous detection may be CPU-intensive. Use lower detection intervals or resize the video feed for smoother performance.

