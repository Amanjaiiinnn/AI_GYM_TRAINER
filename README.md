## Demo

Hugging Face Space:  
`https://gymaitrainer.streamlit.app/`

[Try the App](https://gymaitrainer.streamlit.app/)

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
```
## Project Explanation

AI Real-Time Gym Coach is a computer vision-based fitness assistant that helps users track workouts through their webcam. The app uses MediaPipe to detect human body landmarks in real time and then analyzes joint angles to understand exercise movement, form, and repetitions.

The user first enters a username, selects an exercise, and sets a workout goal by choosing the number of sets and reps. Once the workout starts, the webcam stream is processed frame by frame. The app detects body landmarks such as shoulders, elbows, hips, knees, and ankles, then passes those landmarks to exercise-specific detector classes.

Each detector contains logic for one exercise. For example, the squat detector checks knee angle, back angle, and squat depth. The push-up detector checks elbow angle, body alignment, and hip position. Similar logic is implemented for biceps curls, shoulder press, and lunges.

The app keeps track of total reps, current set reps, completed sets, and exercise-specific form metrics. When a set or workout is completed, the data is saved locally using SQLite so the user can view workout history.

The project also includes an AI coaching layer. Groq is used to generate short coaching feedback based on workout events or detected form issues. The generated feedback is converted into speech using gTTS, allowing the app to provide voice-based workout guidance.

Overall, this project combines real-time computer vision, exercise biomechanics, AI feedback, voice coaching, and local data persistence into one interactive Streamlit application.

---
How It Works
The user logs in with a username.
The user selects an exercise, target sets, and reps.
Streamlit starts the webcam using streamlit-webrtc.
MediaPipe detects body landmarks from each video frame.
Exercise detector classes calculate joint angles and form metrics.
Reps and workout progress are updated in Streamlit session state.
Completed workout data is saved in SQLite.
Groq generates short coaching feedback.
gTTS converts feedback into voice output.
Database
The app uses SQLite for local workout history.

A data.db file is created automatically when the app runs.

Main tables:

users
exercises
Do not commit data.db to GitHub if you want to keep local user data private.
