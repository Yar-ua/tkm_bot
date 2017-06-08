# tkm_bot app

This app uses [telegram-bot](https://github.com/telegram-bot-rb/telegram-bot) gem.

This application developed for resieving weather.

Next planes - add following for the Nova Poshta packages.



## Commands

< ... in process ... >

## Setup

- Create bot with [@BotFather](https://telegram.me/BotFather) `unless has_test_bot?`
- Clone repo.
- run `./bin/setup`.
- Update `config/secrets.yml` with your bot's token.

## Run

### Development

```
bin/rake telegram:bot:poller
```

### Production

One way is just to run poller. You don't need anything else, just check
your production secrets & configs. But there is better way: use webhooks.

__You may want to use different token: after you setup the webhook,
you need to unset it to run development poller again.__

First you need to setup the webhook. There is rake task for it,
but you're free to set it manually with API call.
To use rake task you need to set host in `routes.default_url_options`
for production environment (`config.routes` for Rails < 5).
There is already such line in the repo in `production.rb`.
Uncomment it, change the values, and you're ready for:

```
bin/rake telegram:bot:set_webhook RAILS_ENV=production
```

Now deploy your app in any way you like. You don't need run anything special for bot,
but `rails server` as usual. Your rails app will receive webhooks and bypass them
to bot's controller.

### Testing

```
bin/rspec
```

## Advanced

### Async mode

- Uncomment `async: true` in `secrets.yml`.
- Run and check the logs out.
- More info about [async mode](https://github.com/telegram-bot-rb/telegram-bot#async-mode).

### Botan

- Get token at [botan.io](http://botan.io/).
- Uncomment `botan` section in `secrets.yml` and update token.
- Run.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/telegram-bot-rb/telegram_bot_app.
