require 'bundler/setup'

Bundler.require

desc 'See you next week'
task :see_you_next_week do
  today = Date.today

  return if today.workday? && !HolidayJp.holiday?(today)

  ENV.select { |k, _| k =~ /^SLACK_API_TOKEN_/ }.values.each do |token|
    Slack.configure do |config|
      config.token = token
    end

    client = Slack::Web::Client.new
    now = Time.now
    beginning_of_tomorrow = (now + 1.day).beginning_of_day
    num_minutes = ((beginning_of_tomorrow - now) / 1.minute).to_i

    client.dnd_setSnooze(num_minutes: num_minutes)
  end
end
