# SvelteKit Node AWS Template

This is a template for running a SvelteKit node on EC2 behind CloudFront.

[![Watch the video](https://img.youtube.com/vi/6SCWBCrs7tU/default.jpg)](https://youtu.be/6SCWBCrs7tU)

## SAM commands
```
sam build
sam deploy --stack-name NAME --guided || sam deploy --stack-name NAME --guided --config-env prod
sam delete --stack-name NAME
```

## Build
```
npm ci --prod
npm run build
aws s3 sync ./build s3://BUCKET-NAME/build --delete
aws s3 sync ./node_modules s3://BUCKET-NAME/node_modules --delete
aws s3 cp ./package.json s3://BUCKET-NAME/package.json
```

## Restart
```
aws autoscaling start-instance-refresh --auto-scaling-group-name NAME
```

## User data log file
```
sudo nano /var/log/cloud-init-output.log
```