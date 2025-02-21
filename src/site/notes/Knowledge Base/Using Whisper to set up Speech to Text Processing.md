---
{"created":"2025-02-21","time":"Friday, February 21st, 2025 @ 1:06:22pm","tags":["KnowledgeBase"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/knowledge-base/using-whisper-to-set-up-speech-to-text-processing/","dgPassFrontmatter":true}
---


# Whisper Speech to Text
https://github.com/openai/whisper

You can engage your GPU to do speech to text on your home computer using OpenAI's Whisper.

[[attachments/6a51cd74d96a2ac6ee03b134a60b1fad_MD5.jpeg|Open: Pasted image 20250221131831.png]]
![attachments/6a51cd74d96a2ac6ee03b134a60b1fad_MD5.jpeg](/img/user/attachments/6a51cd74d96a2ac6ee03b134a60b1fad_MD5.jpeg)

I did this using WSL on my Windows desktop. In theory this will also work just fine on a regular Linux host. It might also work to run it from Windows directly, but I didn't try that. WSL is easy for me to use.

This was amazingly easy. Here is my quick-start on how I set it up and got text from an audio recording in a few minutes on Linux/WSL:

```bash
sudo apt install pip ffmpeg
pip install -U openai-whisper
cd Dev
mkdir Whisper
cd Whisper
python3 -m venv .
./bin/pip install -U openai-whisper
```
Note my use of a `venv` for Python to keep things neat.

Now copy a file into the folder and run Whisper!
```bash
cp /mnt/c/Folder/Voice\ Recordings/250221_1210.mp3 .
./bin/whisper 250221_1210.mp3
```
This will display the text on screen and **also save a .txt file** along with a bunch of other versions that include timestamps.

I'm just using the .txt files, but you can look at the others to see if they may help you.

The first time you run it, it will download the model, but after that it should have it and not need to do that.

If you don't have `ffmpeg` it will not work, so I included that in the install.

## Alternate models
You can also specify the language, which should help, although it will guess.
You can also specify the model. In theory the "Medium English" model is slower but more precise?
```bash
./bin/whisper 250221_1210.mp3 --language English --model medium.en
```
I haven't compared the results yet.

This is all explained on the git repository linked at the top.
## Command Line Arguments
To see what other options you can pass to it run:
```bash
./bin/whisper -h
```
For instance you can skip all of the alternate output formats by specifying `--output_format txt`
# Other Options than Whisper?
There are other things out there like "faster-whisper", but this did the job for me just fine, so I'm sticking with it.

For me, speed is not important, I will just start it and walk away while it does the work.
