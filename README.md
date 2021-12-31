# HA_Rhasspy
## Table of contents
* [General info](#general-info)
* [Installation](#Installation)
* [Setup](#setup)
* [Use](#use)

# general-info

## Installation
### Add Respotory to HA add-on
https://github.com/rhasspy/hassio-addons
Install "Rhasspy Assistant"
Use **nl** in "profile_name" under options to set Dutch profile

## Setup
### Configuration Rhasspy
In the Rhasspy webinterface (Open Web UI)
Settings:
- Audio Recording --> arecord --> default (use config on HA-Rhasspy Assistant to set audio)
- Wake Word --> Porcupine
- Speech to Text --> Kaldi
- Intent Recognition --> Fsticuffs
- Text to Speech --> Espeak ##it looks like speech goes to the HA TTS system (https://www.home-assistant.io/integrations/google_translate/)
- Audio Player --> aplay (default device)
- Dialogue Management --> Rhasspy
- Intent Handeling --> Home Assistant 
--> While using HA add-on us "Hass URL" http://hassio/homeassistant/
--> No Access Token
--> Use "Send intents to Home Assistant" add intent: & intent_script: to your HA configuration file

## Use
### Add Sentences
The system uses 'Sentences' from ![sentences.ini](./sentences.ini) to understand and trigger event. 
The [HassXXX] are HA built in [intents](https://developers.home-assistant.io/docs/intent_builtin)
The [XXXX] are your own intents that are sent to [intent_script](https://www.home-assistant.io/integrations/intent_script ) and handeled by ![intent_script.yaml](./intent_script.yaml)
The $Rhasspy/xxx (example  [$Rhasspy/switch](./slots/rhasspy/switch))  refers to "Slots" you can find in \\<internal IP>\share\rhasspy\profiles\nl\slots\rhasspy

### Testing
Testing in Rhasspy Web UI (handy if you do not have Audio)
Use 'Recognize' to test the Intent recognition. If you want to sent the event to HA you can use 'Handle'

### Extra - Get HA device IDs and Friendly-Names
If you want to get all your device IDs and friendly names you can use the code below in 'Template' in HA

  ```YAML
  message: >
        {% for state in states %}
          - {{- state.entity_id -}}, {{- state.attributes.friendly_name -}}
        {% endfor %}
  ```
