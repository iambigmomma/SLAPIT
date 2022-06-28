# APIT
Demo repos for anyone wants to have a taste of Sauce Labs API Testing

# Quickstart




## Funtional Testing



## Mocking

```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml
```


#### Logger
```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml \
--logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$hook_id/logger
```

## Contract Testing

```
docker run -v "$(pwd)/specs:/specs" -p 6000:5000 quay.io/saucelabs/piestry -u /specs/myspec.yaml \
--logger https://$SAUCE_USERNAME:$SAUCE_ACCESS_KEY@$SAUCE_API_ENDPOINT/$hook_id/insights/events/_contract
```