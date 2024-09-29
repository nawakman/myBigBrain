[[INTERESTING]]
Create a file that ends with the .vbs extension. Inside paste
```
Dim speaks, speech
speaks="whatever you want it to say"
Set speech=CreateObject("sapi.spvoice")
Set speech.Voice=speech.GetVoices().Item(0)'you can change the voice by changing the index
speech.Speak speaks
```
Then just click the file

Oh, and completely unrelated: you can toggle windows narrator with `windows+Ctrl+enter`