# swisscore-pyTTS
Easy to use python Text To Speech (TTS) library.

<a href="https://pypi.org/project/swisscore-pyTTS"><img src="https://img.shields.io/pypi/v/swisscore-pyTTS.svg"></a>
<a href="https://pypi.org/project/swisscore-pyTTS"><img src="https://img.shields.io/pypi/pyversions/swisscore-pyTTS.svg"></a>
<a href="https://github.com/psf/black"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-000000.svg"></a>

Currently supported API's:
* <a href="https://www.voicerss.org/api/">Voice RSS</a> (api key needed)

***Note: More API's might beeing added in the future.***

## Installation
### pip (recommended)
***Note: If you are on macOS or Linux you may have to use `pip3`.***
```
pip install swisscore-pyTTS
```
### from source
***Note: If you are on macOS or Linux you may have to use `pip3`.***
```
pip install git+https://github.com/SwissCorePy/swisscore-pyTTS/
```

## Quick Start
```python
import os
from pathlib import Path

# Import VoiceRSS API
from pytts import VoiceRSS

# To avoid writing your API key in source code, you can set it in an environment
# variable API_KEY, then read the variable in your Python code:
api_key = os.getenv("API_KEY")

# The text to turn into speech
text = "Hello. Thank you for downloading this package."

# Setup API instance with default values
tts = VoiceRSS(
    api_key,
    hl=VoiceRSS.hl.en_us,  # Set English (United States) as default language
    v=VoiceRSS.v.en_us.John,  # Set John as default voice
    c=VoiceRSS.c.MP3,  # Set MP3 as default codec
    f=VoiceRSS.f.stereo_16khz_16bit,  # Set 16khz, 16bit, stereo as default format
)

# The outupt file path
out = Path(__file__).parent / "test.mp3"

# Turn the text into a file
if file := tts.to_file(text, out):
    print(f"Success! Now you can do with {file.name} whatever you want.")
    pass

```

