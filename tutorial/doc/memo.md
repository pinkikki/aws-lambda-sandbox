# memo

packaging
```bash
zip -r9 thumbnail.zip *
zip -g xxx.zip xxx.py
```
s3にupload
```bash
aws s3 cp ./thumbnail.zip s3://[バケット名]
```
※直接--zip-fileでzipファイルをデプロイだとサイズが大きすぎて？？できなかったので、一旦s3にupload

deploy(e.g.)
```bash
aws lambda create-function
 --region ap-northeast-1
 --function-name thumbnail
 --role [roleのarn]
 --handler thumbnail.handler
 --runtime python3.6
 --profile default
 --timeout 10
 --memory-size 1024
 --code S3Bucket=[バケット名],S3Key=[ファイル名]
```