# gensound
`gensound` has one of the simplest interfaces for synthesizing music with python, making it very fun to use.  
https://github.com/Quefumas/gensound

## Installing
```pwsh
python -m pip install gensound
```

## Playing signals through system audio
Including `simpleaudio` is recommended so that signals can be played directly through the audio driver rather than exporting to a file that is then played by the default media player. I've found installing it at the system level first is preferred, before using it in a venv. Not sure exactly why, but it adds links to driver/system stuff and that probably runs better when it's persisted at the system level.

It also needs C++ development tools installed to be built, and will provide that link in an error if missing.
```pwsh
python -m pip install simpleaudio
```

Once installed add the following to your scripts to use it for `play()`:
```python
from gensound.io import IO
IO.set_io('play', 'simpleaudio')
```

## Challenges
- implement parsing arguments passed to the script
    - one of Sine, Triangle, Square, or Sawtooth to change signal used
    - notes to play
    - volume