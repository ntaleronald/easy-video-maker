
Audio To Slideshow 
=======

Automatically converts :speech_balloon: speech in an audio file into a :video_camera: video with accompanying relevant images.

## Usage
Ensure you have subscribed to IBM Watson's Speech to Text service and Flickr API.
```
cd ./audio_to_slideshow
echo '
IAM_AUTHENTICATOR={ibm_iam_authenticator}
IBM_URL={speech_to_text_watson_instance_url}
FLICKR_KEY={flickr_key}
FLICKR_SECRET={flickr_secret}
' > .env
```

#### Method 1: Dockerfile (Recommended)

Ensure Docker engine is running
```
docker build -t audio_to_images:1.0 .

# Ensure .mp3 file exists at ./input (A sample is there)
docker run --rm --env-file ./.env -v ${pwd}/input:/app/input -v ${pwd}:/app/output audio_to_images:1.0

# The output video file will be at the current directory
```
#### Method 2: Pipfile

Ensure Pipenv is installed
```
pipenv install
pipenv shell
cd ./app
mkdir input output

# Ensure .mp3 file exists at ./app/input

pipenv run python main.py
```

