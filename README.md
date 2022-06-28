# APIT
Demo repos for anyone wants to have a taste of Sauce Labs API Testing

# Quickstart

TBD



## Funtional Testing
TBD


## Mocking

Rn the following commands to start a local  Piestry mocking server
```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml
```

Execute below example commands to hit the mocking server
```
curl localhost:6000/api/v1/release-notes

curl -u "example:1234" localhost:6000/api/v1/user/

curl -u "example:1234" localhost:6000/api/v1/user/foobar

curl -u "example:1234" localhost:6000/api/v1/user/dumbbar

curl -u "example:1234" localhost:6000/api/v1/user/drawbar
```

#### Logger
By adding the ```--logger``` together with your Sauce Labs API Testing endpoint, the endpoint hitting records could also visible on the platform
```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml \
--logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$hook_id/logger
```

## Contract Testing

```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml \
--logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$hook_id/insights/events/_contract
```