require 'echoe'

Echoe.new("memcached") do |p|
  p.author = "Evan Weaver"
  p.project = "fauna"
  p.summary = "An interface to the libmemcached C client."
  p.url = "http://blog.evanweaver.com/files/doc/fauna/memcached/"
  p.docs_host = "blog.evanweaver.com:~/www/bax/public/files/doc/"
  p.rdoc_pattern = /README|TODO|LICENSE|CHANGELOG|exceptions|behaviors|memcached.rb/
end

task :exceptions do
  $LOAD_PATH << "lib"
  require 'memcached'
  Memcached.constants.sort.each do |const_name|
    const = Memcached.send(:const_get, const_name)
    next if const == Memcached::Success or const == Memcached::Stored
    if const.is_a? Class and const < Memcached::Error
      puts "* Memcached::#{const_name}"
    end
  end
end
