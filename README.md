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

# Prerequresites
- [jq](https://stedolan.github.io/jq/)
- [Gcloud command-line tool](https://cloud.google.com/sdk/gcloud)

