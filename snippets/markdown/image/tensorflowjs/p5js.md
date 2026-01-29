Open up the code snippet below directly in the [p5.js Web Editor](https://editor.p5js.org/ml5/sketches/ImageModel_TM).

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Deteksi Sampah Organik AI</title>

  <!-- p5.js -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>

  <!-- ml5.js -->
  <script src="https://unpkg.com/ml5@latest/dist/ml5.min.js"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #eaf7f1;
    }
    canvas {
      margin-top: 10px;
      border-radius: 10px;
    }
    h2 {
      margin-top: 20px;
    }
  </style>
</head>

<body>

<h2>♻ Deteksi Sampah Organik Berbasis AI</h2>
<p>Arahkan kamera ke sampah</p>

<script>
  let classifier;
  let video;
  let hasil = "Loading model...";

  // 🔴 GANTI LINK MODEL DI SINI
  let modelURL = "[https://teachablemachine.withgoogle.com/models/XXXXXXX/";
](https://teachablemachine.withgoogle.com/models/[...])
  function preload() {
    classifier = ml5.imageClassifier(modelURL + "model.json");
  }

  function setup() {
    createCanvas(320, 260);
    video = createCapture(VIDEO);
    video.size(320, 240);
    video.hide();
    classify();
  }

  function draw() {
    background(255);
    image(video, 0, 0);

    fill(0);
    textSize(16);
    textAlign(CENTER);
    text(hasil, width / 2, height - 10);
  }

  function classify() {
    classifier.classify(video, hasilDeteksi);
  }

  function hasilDeteksi(error, results) {
    if (error) {
      console.error(error);
      return;
    }

    hasil = results[0].label + 
            " (" + (results[0].confidence * 100).toFixed(2) + "%)";
    classify();
  }
</script>

</body>
</html>
