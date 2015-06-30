# TelegramBot

A charismatic ruby client for [Telegram's Bot API](https://core.telegram.org/bots).

Write your own Telegram Bot using Ruby! Yay!

Currently under heavy development.
Please [collaborate](https://github.com/eljojo/telegram_bot/issues/new) with your questions, ideas or problems!

## Installation

Add this line to your application's Gemfile (currently under development):

```ruby
gem 'telegram_bot', github: 'eljojo/telegram_bot'
```

And then execute:

    $ bundle

## Usage

Here's an example:

```ruby
require 'telegram_bot'

bot = TelegramBot.new('[YOUR TELEGRAM BOT TOKEN GOES HERE]')
bot.get_updates do |message|
  puts "@#{message.from.username}: #{message.text}"
  command = message.get_command_for(bot)

  message.reply do |reply|
    case command
    when /greet/i
      reply.text = "Hello, #{message.from.first_name}!"
    else
      reply.text = "#{message.from.first_name}, have no idea what #{command.inspect} means."
    end
    puts "sending #{reply.text.inspect} to @#{message.from.username}"
    reply.send_with(bot)
  end
end
```

Here's a sample output:

```
$ bundle exec ruby bot.rb
@eljojo: greet
sending "Hello, José!" to @eljojo
@eljojo: heeeeeeeeya!
sending "José, have no idea what \"heeeeeeeeya!\" means." to @eljojo
```

![Example](http://i.imgur.com/VF8X4CQ.png)

## How do I get a Bot Token

Talk to the [@BotFather](https://telegram.me/botfather).
You can find more info [here](https://core.telegram.org/bots).

![How to get Token](http://i.imgur.com/90ya4Oe.png)

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/eljojo/telegram_bot. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
