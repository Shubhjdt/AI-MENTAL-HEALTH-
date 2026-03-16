!pip install SpeechRecognition
import numpy as np
import matplotlib.pyplot as plt
import speech_recognition as sr

# -------------------------
# Prediction Function
# -------------------------

def predict(text):

    text = text.lower()

    depression_words = ["sad","lonely","tired","depressed","hopeless","cry"]

    score = 0

    for word in depression_words:
        if word in text:
            score += 1

    probability = min(0.2 + score*0.2, 0.95)

    if probability > 0.5:
        label = "Depression Detected"
    else:
        label = "Normal Mental State"

    return label, probability


# -------------------------
# TEXT INPUT
# -------------------------

text = input("Enter text: ")

label, prob = predict(text)

print("\nPrediction:", label)
print("Probability:", round(prob,2))


# -------------------------
# GRAPH OUTPUT
# -------------------------

labels = ["Normal","Depression"]
values = [1-prob, prob]

plt.bar(labels, values)

plt.ylabel("Probability")
plt.title("Mental Health Prediction")

plt.show()


# -------------------------
# VOICE INPUT
# -------------------------

choice = input("\nDo you want to use voice input? (y/n): ")

if choice == "y":

    r = sr.Recognizer()

    with sr.Microphone() as source:

        print("Speak now...")
        audio = r.listen(source)

    try:

        voice_text = r.recognize_google(audio)

        print("You said:", voice_text)

        label, prob = predict(voice_text)

        print("\nPrediction:", label)
        print("Probability:", round(prob,2))

    except:

        print("Could not understand audio")
