#!/usr/bin/env ruby
######################################################################
#
# dot
#
# A tiny web server to help serve a directory as quickly as possible.
#
# Author: Naveen Selvadurai
# Date: 2008-05-12
#
######################################################################

require 'webrick'
include WEBrick

path = (ARGV[0] and File.directory?(ARGV[0])) ? ARGV[0] : Dir.pwd
port = (ARGV[1] and ARGV[1].to_i > 0 and ARGV[1].to_i < 65535) ? ARGV[1].to_i : 80

if path and port
	puts "Serving [" + File.expand_path(path)  + "] on port [" + port.to_s + "]"

	s = HTTPServer.new(
		:Port => port,
		:DocumentRoot => path
	)
	
	trap("INT"){ s.shutdown }
  s.start
else
  puts "Usage: dot [document-root] [port]\n"
  puts "\tdocument-root: the directory to serve (optional, default: current directory)\n"
  puts "\tport: the port over which to serve the content (optional, default: 80)\n"
end
