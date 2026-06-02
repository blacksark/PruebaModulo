# U6 - Multimèdia en Flutter

## 1. Introducció al multimèdia

### Història i evolució
- Anys 70-80: primers experiments amb àudio digital.
- Anys 90:
  - WAV (1991)
  - MP3 (1995)
  - JPEG (1992)
  - PNG (1996)
  - MPEG
- Anys 2000:
  - MP4, DivX, MKV
  - YouTube (2005)
- Actualitat:
  - H.265 (HEVC)
  - Opus
  - Realitat virtual i augmentada
  - HLS

### Tipus de multimèdia
- Multimèdia lineal
- Multimèdia no lineal

### Flutter com a entorn multimèdia
- Motor Impeller (predeterminat)
- Paquets:
  - audioplayers
  - video_player
- Limitacions en processament multimèdia intensiu.

---

## 2. Gestió de continguts d'àudio amb Audioplayers

### Instal·lació

```yaml
dependencies:
  audioplayers: ^6.5.1
```

```bash
flutter pub add audioplayers
```

### Ús bàsic

```dart
final player = AudioPlayer();
await player.play(UrlSource('https://example.com/audio.mp3'));
await player.pause();
await player.stop();
await player.setVolume(0.5);
await player.seek(Duration(seconds: 30));
```

### Fonts d'àudio
- URL
- AssetSource
- DeviceFileSource
- BytesSource

### Exemple complet
Reproductor amb:
- Play
- Pause
- Stop
- Slider de progrés
- Gestió de durada i posició

---

## 3. Gestió de vídeo amb video_player

### Instal·lació

```yaml
dependencies:
  video_player: ^2.10.0
```

### Inicialització

```dart
final VideoPlayerController controller =
    VideoPlayerController.networkUrl(
      Uri.parse('https://example.com/video.mp4'));
```

### Operacions bàsiques

```dart
await controller.initialize();

controller.play();
controller.pause();

controller.seekTo(Duration(seconds: 30));

controller.dispose();
```

### Components importants
- VideoPlayer
- AspectRatio
- VideoProgressIndicator

---

## 4. Captura d'imatge i vídeo

### Llibreries

```yaml
dependencies:
  camera: ^0.11.3
  image_picker: ^1.2.0
```

### Camera

```dart
CameraController(
  cameras[0],
  ResolutionPreset.high,
);
```

### Captura d'imatges

```dart
final image = await controller.takePicture();
```

### Captura de vídeo

```dart
await controller.startVideoRecording();

final video =
    await controller.stopVideoRecording();
```

### Image Picker

```dart
final img =
    await picker.pickImage(
      source: ImageSource.gallery);
```

```dart
final video =
    await picker.pickVideo(
      source: ImageSource.gallery);
```

### Processament d'imatges

#### Redimensionar

```dart
img.copyResize(image,
  width: 300,
  height: 300);
```

#### Rotar

```dart
img.copyRotate(image, 90);
```

---

## 5. Animacions

### Animacions implícites
- AnimatedContainer
- AnimatedOpacity
- AnimatedAlign

Exemple:

```dart
AnimatedContainer(
  duration: Duration(seconds: 1),
  width: 200,
  height: 200,
);
```

### Animacions controlades

Components:
- AnimationController
- Tween
- Curves

```dart
_controller = AnimationController(
  duration: Duration(seconds: 2),
  vsync: this,
);
```

### Hero

```dart
Hero(
  tag: 'hero-image',
  child: Container(),
);
```

### Lottie

```yaml
dependencies:
  lottie: ^1.4.3
```

```dart
Lottie.asset(
  'assets/animations/sample_animation.json'
);
```

## Resum

Continguts principals:
1. Multimèdia en Flutter
2. Audioplayers
3. Video Player
4. Camera i Image Picker
5. Processament d'imatges
6. Animacions implícites
7. Animacions controlades
8. Hero
9. Lottie
