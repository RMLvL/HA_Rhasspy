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
--> Use "Send intents to Home Assistant" add intent: & intent_script: to your HA configuration file https://www.home-assistant.io/integrations/intent_script 
https://developers.home-assistant.io/docs/intent_builtin/#:~:text=Home%20Assistant%20comes%20with%20a%20couple%20of%20built-in,with%20user%20defined%20intents.%20Turn%20an%20entity%20off.

The system uses 'Sentences' from sentences.ini to understand and trigger event. 
The [HassXXX] are HA built in intents https://developers.home-assistant.io/docs/intent_builtin/#:~:text=Home%20Assistant%20comes%20with%20a%20couple%20of%20built-in,with%20user%20defined%20intents.%20Turn%20an%20entity%20off.
The [XXXX] are your own intents that are sent to 'inent_script' and handeled by 'intent_script.yaml'

Testing in Rhasspy Web UI (handy if you do not have Audio)
Use 'Recognize' to test the Intent recognition. If you want to sent the event to HA you can use 'Handle'
