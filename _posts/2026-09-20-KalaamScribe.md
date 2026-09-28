---
title: "Kalaam Scribe: a fully on-device android dictation app."
date: 2026-09-20
tags: [Projects]
excerpt: "A native Android app that turns speech into text entirely on-device, covering 99 languages and built for Urdu and Roman-Urdu."
toc: false
---

I'd rather dictate text than send voice messages. Most dictation apps send your audio to the cloud, and they do poorly on low-resource languages like Urdu. Roman-Urdu is usually ignored, even though that is the script Urdu speakers type in when they chat.

Kalaam Scribe is a personal project. It is a native Android app in Kotlin with Jetpack Compose. Tap the mic, speak, tap stop, and the app copies the transcript to your clipboard so you can paste it wherever you want. Transcription runs on the phone. The only internet access is the one-time model download, and after that it works offline.

You can pick between two transcription modes in settings. Batch decodes the whole clip in one go after you stop. Simulated streaming decodes as you speak, so the transcript grows while you talk.

## Language coverage

Whisper's multilingual models cover 99 languages, so English, German, and the rest work out of the box. For Urdu there is a fine-tuned model for Roman-Urdu, and Dolphin attention ASR handles Urdu script. The picker recommends a model per language, and models download in-app from HuggingFace.

<video class="align-center" src="https://github.com/user-attachments/assets/076d2ffd-8cc1-4c58-b366-7154bc6482da" controls width="360"></video>

## Try it

The app is not on the Play Store yet. It ships as a single signed APK, so you will have to allow "Install from unknown sources" when Android asks.

- Repository: [Faizan-E-Mustafa/kalaam-scribe](https://github.com/Faizan-E-Mustafa/kalaam-scribe)
- Download the latest release from [here](https://github.com/Faizan-E-Mustafa/kalaam-scribe/releases/latest)

The app needs Android 8.0 or newer, and about 300 MB of free space for a model. Right now the transcript goes to your clipboard and you send it yourself. Two potential changes I want to make next are inserting text straight into the focused keyboard field, and saving transcripts and clips.
