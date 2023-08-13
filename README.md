# Developing_a_Voice_Assisant
we will be developing a virtual AI Voice assisant which will perform several tasks with just a voice command



# Time Line of the Project:

  . Importing Libraries
  . Developing Voice for AI
  . Developing greeting functions
  . Developing Command functions


# importing Libraries

    pip install pyttsx3

To install PyAudio : https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyaudio


    import pyttsx3  ## for the ai to speck, ### text to speech library
    import datatime 
    import speech_recognition as sr ## for getting input voices ## speech to text library
    import wikipedia ###for surfind wikipedia
    import os ##for opening local files
    import webbrowser  ## for surfing the internet


# Imoporting the voice for our AI

    engine = pyttsx3.init('sapi5')
    voices = engine.getProperty('voice')
    engine.setProperty('voice',voice[0].id)

    #print(voice[1].id)

# Developing a greeting function

    def speck(audio): 
         engine.say(audio)
         engine.runAndWait()

    def greet(): 

         hour = int(datetime.datatime.now().hour)
         if hour>=0 and hour<12:
            speak("good afternoon sir ! ")
        elif hour>=12 and hour<18:
             speak("Hope you had your brunch, Good Afternoon sir !")

        else:
              speak("The wather is lovely, Good Evening sir !")

        speak("Hello How are you? I am your personal AI Assistance prabha! how can i help you")


          #greet()


  # Developing a command function

       def command():

       r = sr.Recognizer()
       with sr.Microphone() as source:

            print("Listening...")
            r.paush_threshold =1.2
            audio = r.listen(source)

      try:
            print("Recognizing...")
            query = r.recognize_google(audio,language='en-in')  ##speech to text
            print(f"you said: {query}\n")

    except Exception as e:

           print(" I can not get you, please speak again")
           return "None"
    return query



# Writing different tasks for AI to perform

     if __name__ == " __main__ ":
          greet()
          #while true
          if 1:
              query = command().lower()

              # Logic for executing tasks based on query

              if 'wikipedia' in query:
                  speak('searching wikipedia...')
                  query = query.replace("wikipedia","")
                  results = wikipedia.summary(f'{query}',sentences=2)
                  speak("According to wikipedia")
                  print(results)
                  speak(results)

              elif 'open instagram' in query:
                  webbrowser.open("instagram.com")
              elif 'open youtube' in query:
                   webbrowser.open("youtube.com")
              elif 'open google' in query:
                    webbrowser.open("google.com")
              elif 'the weather'in query:
                    webbrowser.open("weather.com")
              elif 'the score' in query:
                    webbrowser.open("cricbuzz.com")
              elif 'play music' in query:
                    music_dir = 'sound\\fold'
                    songs = os.listdir(music_dir)
                    print(songs)
                    os.startfile(os.path.join(music_dir,songs[0]))
             elif 'the time' in query:
                   strTime = dateTime.datetime.now().strftime("%H:%H:%S")
                   speak(f"sir, the time is (strtime)")

              


          
