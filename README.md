# send-fcm
Command line tool for Sending Firebase Cloud Messaging messages.

```
Usage: send-fcm.sh -r 'registration-token' -t 'title' -m 'message' [ -u 'data-url' ] [ -c 'type' ] [-h]
Options:
    -t: Push notification message Title(required)
    -m: Push notification Message body(required)
    -r: Destination Registration token(required)
    -u: Optional Url parameter
    -c: Optional type parameter
    -h: Show this Help.
    -d: Dry run mode. Just print curl command without execution.

Environment Variables:
    GOOGLE_APPLICATION_CREDENTIALS: Service account key JSON file. Please download from IAM page on your GCP project page.(required)

```

# Example:
## Send hello world to the registartion token "<REGISTRATION-TOKEN>".
```bash
GOOGLE_APPLICATION_CREDENTIALS=./my-project-ffffffff.json ./send-fcm -t 'sample' -m 'hello world' -r '<REGISTRATION-TOKEN>' -u 'https://www.tech-vein.com/'
```
## You can just generate curl command with dry run (-d) option.
```bash
GOOGLE_APPLICATION_CREDENTIALS=./my-project-ffffffff.json ./send-fcm -d -t 'sample' -m 'hello world' -r '<REGISTRATION-TOKEN>' -u 'https://www.tech-vein.com/'
```

this command generates:
```bash
curl 'https://fcm.googleapis.com/v1/projects/my-project/messages:send' \
   --header 'Authorization: Bearer 'ya29.c.XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' \
   --header Content-Type:application/json \
   -d '{ "message": { "token": "<REGISTRATION-TOKEN>", "notification": { "title": "sample", "body": "hello world"},"android": {"priority": "high"}, "data":{"url": "https://www.tech-vein.com/", "type": ""}}}'
```

# Prerequresites
- These command-line tools are required.
  - [curl](https://curl.se/)
  - [jq](https://stedolan.github.io/jq/)
  - [Gcloud command-line tool](https://cloud.google.com/sdk/gcloud)
- Please download Service account key JSON file from your GCP project page. And then set the file path to GOOGLE_APPLICATION_CREDENTIALS.
