# AI Real-Time Gym Trainer

AI Real-Time Gym Coach is a Streamlit-based fitness assistant that uses live webcam video, MediaPipe pose detection, exercise-specific form analysis, rep counting, workout progress tracking, SQLite history storage, and AI-generated voice coaching.

The app is designed for real-time workout guidance with support for multiple exercises such as squats, push-ups, biceps curls, shoulder press, and lunges.

## Features

- Real-time webcam-based pose tracking
- Exercise-specific landmark and angle analysis
- Automatic rep counting
- Sets and reps workout planning
- Live workout progress metrics
- Form feedback for supported exercises
- AI coach feedback using Groq
- Text-to-speech voice output using gTTS
- SQLite-based workout history
- Custom Streamlit UI styling
- Login by username for local workout history tracking

## Supported Exercises

- Squats
- Push-ups
- Biceps Curls (Dumbbell)
- Shoulder Press
- Lunges

## Tech Stack

- Python
- Streamlit
- streamlit-webrtc
- MediaPipe
- OpenCV
- Pandas
- SQLite
- Groq API
- gTTS
- python-dotenv

## Project Structure

```text
GymTrainer/
├── main.py
├── requirements.txt
├── .streamlit/
│   └── config.toml
├── core/
│   └── base_exercise.py
├── detectors/
│   ├── squat.py
│   ├── pushup.py
│   ├── biceps_curl.py
│   ├── shoulder_press.py
│   └── lunges.py
├── ml_models/
│   └── pose_landmarker_full.task
├── services/
│   ├── auth/
│   │   └── login_wall.py
│   ├── coaching/
│   │   ├── llm.py
│   │   ├── tts.py
│   │   └── voice_pipeline.py
│   ├── config/
│   │   └── workout_config.py
│   ├── persistence/
│   │   └── exercise_repository.py
│   ├── state/
│   │   └── session_defaults.py
│   ├── tracking/
│   │   └── metrics.py
│   ├── ui/
│   │   └── style_loader.py
│   └── vision/
│       └── exercise_video.py
└── static/
    ├── style.css
    └── AdobeClean.otf
