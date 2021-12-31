# HA_Rhasspy

Add Respotory to HA add-on
https://github.com/rhasspy/hassio-addons
Install "Rhasspy Assistant"
Use **nl** in "profile_name" under options to set Dutch profile

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

The system uses 'Sentences' from sentences.ini to understand and trigger event. 
The [HassXXX] are HA built in [intents](https://developers.home-assistant.io/docs/intent_builtin) or custom [intent_script](https://www.home-assistant.io/integrations/intent_script )
The $Rhasspy/lights refers to "Slots" you can find in \\<internal IP>\share\rhasspy\profiles\nl\slots\rhasspy
The [XXXX] are your own intents that are sent to 'inent_script' and handeled by 'intent_script.yaml'

Testing in Rhasspy Web UI (handy if you do not have Audio)
Use 'Recognize' to test the Intent recognition. If you want to sent the event to HA you can use 'Handle'

If you want to get all your device ids and friendly names you can use the code below in 'Template' in HA
'''yaml
  message: >
        {% for state in states %}
          - {{- state.entity_id -}}, {{- state.attributes.friendly_name -}}
        {% endfor %}
'''
