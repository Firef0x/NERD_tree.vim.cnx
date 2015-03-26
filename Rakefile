#!/usr/bin/env rake
# encoding: utf-8

########################

require 'auto-correct'

task :default => [:check]

task :correct do
  script_dir = File.expand_path(File.dirname(__FILE__)) + "/"

  if File.exist?(script_dir + "doc/NERD_tree.cnx")
    orig = File.open(script_dir + "doc/NERD_tree.cnx","r")
    crrt = File.open(script_dir + "NERD_tree.cnx","w")
    orig.each do |line|
      crrt.puts line.auto_correct!
    end
    orig.close
    crrt.close
  end
end

task :check do
  script_dir = File.expand_path(File.dirname(__FILE__)) + "/"
  fileno = 0
  flag = false

  if File.exist?(script_dir + "doc/NERD_tree.cnx")
    orig = File.open(script_dir + "doc/NERD_tree.cnx","r")
    orig.each do |line|
      fileno += 1
      newline = line.clone.auto_correct!
      if line.eql?(newline) === false
        puts "#{fileno}: #{line}"
        flag = true
      end
    end
    orig.close
    if flag
      raise "Fails on spacing check!"
    end
  end
end

