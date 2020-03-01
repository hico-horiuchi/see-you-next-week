## see-you-next-week

### References

- [dnd.setSnooze method | Slack](https://api.slack.com/methods/dnd.setSnooze)
- [Heroku Scheduler | Heroku Dev Center](https://devcenter.heroku.com/articles/scheduler)

### How to use

```
$ heroku config:set SLACK_API_TOKEN_WORKSPACE_A=xoxb-abcdefghijklmnopqrstuvwxyz0123456789
$ heroku config:set SLACK_API_TOKEN_WORKSPACE_B=xoxb-abcdefghijklmnopqrstuvwxyz0123456789
$ heroku addons:create scheduler:standard
$ heroku addons:open scheduler
```

![heroku_scheduler_setting.jpg](https://raw.githubusercontent.com/hico-horiuchi/see-you-next-week/master/heroku_scheduler_setting.jpg)
