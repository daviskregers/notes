# Deploying models to Real-time systems

## How do I use my model in an app?

- Your external apps can't justr run a notebook
- Separate your training from your predictions
    - Train the model periodically offline
    - Push the model - or it's results - to a web service
    - Your app calls the web service

## Example: Google Cloud ML

- Dump your trained classifier using sklearn.externals
    - from sklearn.externals import joblib
    - joblib.dump(clf, 'model.joblib')
- Upload model.joblib to Google Cloud storage, specifying the scikit-learn framework
- Cloud ML Engine exposes ar REST API that you call to make predictions in real-time

## Example: AWS (recommender system)

- Server logs ->
- Amazon Kinesis Data Firehose ->
- Amazon S3 ->
- Amazon EMR ->
- Amazon DynamoDB ->
- AWS Lambda ->
- Amazon API Gateway ->
- Client app

## Other approaches

- Roll your own web service with Flask or another framework
    - Then you have servers to provision and maintain.
- Go all-in with a platform
    - Amazon SageMaker
    - Amazon Comprehend
    - Amazon Lex
    - Amazon Polly
    - Amazon Rekognition
    - Amazon Rekognition Image
    - Amazon Rekognition Video
    - Amazon Translate
    - Amazon Transcribe
    - AWS Deep Learning APIs
    - AWS DeepLens
