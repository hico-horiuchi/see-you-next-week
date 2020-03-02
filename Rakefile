require 'bundler/setup'

Bundler.require

desc 'See you next week'
task :see_you_next_week do
  today = Date.today

  if today.workday? && !HolidayJp.holiday?(today)
    puts "#{today} is workday"
    next
  end

  ENV.select { |k, _| k =~ /^SLACK_API_TOKEN_/ }.each do |env, token|
    Slack.configure do |config|
      config.token = token
    end

    client = Slack::Web::Client.new
    now = Time.now
    beginning_of_tomorrow = (now + 1.day).beginning_of_day
    num_minutes = ((beginning_of_tomorrow - now) / 1.minute).to_i

    begin
      result = client.dnd_setSnooze(num_minutes: num_minutes)

      puts "#{env} #{result}"
    rescue => e # rubocop:disable Style/RescueStandardError
      puts "#{env} #{e}"
    end
  end
end
