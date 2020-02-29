require 'bundler/setup'

Bundler.require

Slack.configure do |config|
  config.token = ENV['SLACK_API_TOKEN']
end

desc 'See you next week'
task :see_you_next_week do
  today = Date.today

  return if today.workday? && !HolidayJp.holiday?(today)

  client = Slack::Web::Client.new
  now = Time.now
  beginning_of_tomorrow = (now + 1.day).beginning_of_day
  num_minutes = (beginning_of_tomorrow - now).to_i / 1.minute

  client.dnd_setSnooze(num_minutes: num_minutes)
end
