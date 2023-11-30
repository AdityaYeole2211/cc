Step1: Install google cloud cli
(New-Object Net.WebClient).DownloadFile("https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe", "$env:Temp\GoogleCloudSDKInstaller.exe")

& $env:Temp\GoogleCloudSDKInstaller.exe

Step2: Initialise cloud sdk
gcloud init

step3: test.py file:
import webapp2

class MainPage(webapp2.RequestHandler):
    def get(self):
        self.response.write("Hello World")

app = webapp2.WSGIApplication([('/', MainPage)], debug = True)

step4: app.yml file :
runtime: python27

api_version: 1
threadsafe: false

handlers:
- url : /
  script: test.app

Step5: run command in cloud sdk shell: 
py google-cloud-sdk\bin\dev_appserver.py <path to folder in which above 2 files are located>

