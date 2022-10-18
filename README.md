# Spotify-project
#from tkinter import*
#import pyglet
#from pydub import AudioSegment
#from pydub.playback import play
#from playsound import playsound
import pandas as pd
import json 
import requests
import spotipy
import urllib.request
from PIL import Image
from spotipy.oauth2 import SpotifyClientCredentials
cid = '9da4c59bc7734c8497c03e96644406dd'
secret = 'b59e06c48e4245b2b2fa5e4c7e256e32'
artist_info = requests.get('https://api.spotify.com/v1/search')
from IPython.display import display, HTML
from ipywidgets import interact_manual, widgets
from string import punctuation
width = 200
height = 200
display(HTML("<H1>Can You Please Enter Your Username So I can view your playlist :) I Need New Music :( Thanks for your help! </h1>"))
@interact_manual(username=widgets.Text())
def main(username):
        print(username)

from base64 import b64encode
# USE YOUR OWN CREDENTIALS THESE ARE EXAMPLES
cid = '9da4c59bc7734c8497c03e96644406dd'
secret = 'b59e06c48e4245b2b2fa5e4c7e256e32'

# Step one, get the access token
payload = { 'grant_type' : 'client_credentials'}
response = requests.post("https://accounts.spotify.com/api/token", auth=(cid,secret),data=payload)
token = response.json()['access_token']
print(f"Access token: {token}")
#toke. will come from this first code
#call your api using cid and secret 
url = f"https://api.spotify.com/v1/users/mara.uben/playlists"
query_string = { 'limit': '13'}
header = {"Authorization" : f"Bearer {token}"}
response = requests.get(url, headers=header, params = query_string)
data = response.json() #deserialize
data
for i in data['items']:
    print(i['owner']['display_name'])
    print(i['name'])
    print(i['description'])
    (i['public'])
    if (i ['public'] ) == True:
        print('This is a public playlist, enjoy :)')
    print(i['external_urls'])
    print(i['tracks'])
    #print(i['total'])
    #print(i['images'][0]['url'])
    urllib.request.urlretrieve((i['images'][0]['url']),"gfg.png")
    #img.resize((20, 20))#trying to make my images smaller, not sure why it wont work. 
    newsize = (60, 80)
    #img = img.resize(newsize)
    img = Image.open("gfg.png")
    width, height = img.size
    img.show()
#Try nd resize image its too big    
df = pd.DataFrame(data['items'])
df
playlists_s = (i['name'])
Tracks = (i['tracks'])
url_links = (i['external_urls']['spotify'])
display(HTML(f"<h3> Please take the following quiz to help us better advance our project. </h3>"))
display(HTML(f"<h3> Choose a playlist and then total to recieve the amount of songs on a playlist and the playlist url.  </h3>"))
@interact_manual(Playlist=playlists_s, Songs=Tracks, URL_Link=url_links)
def analyze(Playlist,Songs,URL_Link):
    print(Playlist,Songs,url)
while True:
    user = ('')
    playlist_qr  = ('')
    x = 10
    spoty = input("Do you have a spotify account? ")
    if spoty != 'Yes':
        break
    elif user == input("what is your username on spotify? :"): 
        print("Great Thanks!")
    elif playlist_qr == input("How many playlist do you have? :"):
        break
        print("Thankyou for taking the quiz!")
        break
#add youtoub video        
#from tkinter import*
#import pyglet
#Okay so in this section I wanted to add a song from my mp3 files play but I clearly ran out of time because 
#it is 3am and I have an 8am final. I wanted import a song from spotify but did not know how so settles for the mp3
#root = Tk()

#player = pyglet.media.Player()
#song = "er.mp3"
#src = pyglet.media.load(song)
#player.queue(src)

#def play():
    #player.play()

#def pause():
    #player.pause()

#button_1 = Button(root,text = "Play", command = play)
#button_1.pack()
#button_2 = Button(root,text = "Pause", command = pause)
#button_2.pack()

#root.mainloop()

#playsound("MyPath\\03 Alabama (feat. Sampha & Jazmine Sullivan).mp3")
