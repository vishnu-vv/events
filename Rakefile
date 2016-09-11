task :entry do
  info = get_info(title: 'Title: (eg: KRUG Meetup)',
                  date: 'Date: YYYY-MM-DD',
                  categories: 'eg: Local Metetup/Hackathon/Open Source Saturday',
                  comments: 'true/false')

  text = "---
layout: post
title: #{info[:title]}
date: #{info[:date]}
categories: #{info[:categories]}
comments: #{info[:comments]}
---
"

  filename = "#{info[:date]}-#{info[:title].downcase.gsub(' ', '-')}.md"
  path = File.join('_posts', filename)
  File.open(path, 'w') { |f| f << text }
end

task :deploy do
  `git push origin master`
end

def get_info(qns)
  qns.map { |k, qn|
    [k, ask("#{qn}: ")]
  }.to_h
end

def ask(qn)
  STDOUT.print qn
  STDIN.gets.chomp
end
