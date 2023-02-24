---
layout: post
title: "This is my first blog"
categories: [python,blog]
---

Hello world! This is my first blog all of time.

These code blocks examples for me:

{% highlight python %}
	"""This is my first blog.
	"""
{% endhighlight %}

Here's the code to go along with it:

{% highlight python %}
	from email.mime import audio
	import speech_recognition as sr
	from pynput.keyboard import Key, Controller
	import time
	import pyttsx3


	engine = pyttsx3.init()


	# Set properties _before_ you add things to say
	engine.setProperty('rate', 150)    # Speed percent (can go over 100)
	engine.setProperty('volume', 1)  # Volume 0-1
	engine.say("WELCOME")

	# Flush the say() queue and play the audio
	engine.runAndWait()

	# Program will not continue execution until
	# all speech is done talking
	keyboard = Controller()


	def spotify_exe():
		keyboard.press(Key.cmd_l)
		keyboard.release(Key.cmd_l)
		time.sleep(3)
		keyboard.type('Spotify')
		time.sleep(3)
		keyboard.press(Key.enter)
		keyboard.release(Key.enter)

	def main():
		r = sr.Recognizer()

		with sr.Microphone() as source:
			r.adjust_for_ambient_noise(source)
			print("Please say something.")
			audio = r.listen(source)

			try:
				print("You have said : \n" + r.recognize_google(audio))
				text = r.recognize_google(audio)
				if("Spotify" in text):
					engine.say("opening"+text)
					engine.runAndWait()
					spotify_exe()
					print("Opening.")
					time.sleep(3)
					keyboard.press(Key.media_play_pause)
					keyboard.release(Key.media_play_pause)
					
			except Exception as e:
				print("Error : "+str(e))

	if __name__ == "__main__":
		main()
{% endhighlight %}
