opsworks-sidekiq
================

Opsworks sidekiq cookbook for Ubuntu and Rails or non-rails sidekiq deploys

## Installation instructions

1) Make sure you have Redis installed.  This cookbook seems decent: https://github.com/brianbianco/redisio

2) Add this cookbook to your list of Custom Cookbooks

3) Add sidekiq::deploy to your Application's Deploy custom recipe. 

4) Configure your sidekiq custom JSON to specify Sidekiq should be deployed with this app:

Currently supported options for Sidekiq are:

* environment: Defaults to production
* require: Defaults to the deploy[:deploy_to]/current directory.  Paths should be relative to the 'current' deploy directory.

Here is an example Custom JSON:

```json
{
  "deploy": {
    "YOURAPPNAME": {
      "sidekiq": {
        "environment": "production",
        "require": "config/boot.rb"
      }
    }
  }
}
```

Or with just using the defaults:
```json
{
  "deploy": {
    "YOURAPPNAME": {
      "sidekiq": {}
    }
  }
}
```



## Assumptions

This recipe assumes you have a config/sidekiq.yml located in root of the App you are deploying.
