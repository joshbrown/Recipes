desc 'Create New Recipe'
task :recipe, :name do |t, args|
  
  #set some variables
  name, slug, hdashes = process_name(args.name)
  file = File.join(File.dirname(__FILE__), slug + '.markdown')
  # Write new file
  FileUtils.mkpath(File.dirname(file))
  File.open(file, "w") do |f|
    f << <<-EOS.gsub(/^      /, '')
      #{name}
      #{hdashes}
    EOS
  end
  
  # Open in editor
  system ("mate #{file}")
end


def process_name(name)
  if !name
    puts "USAGE: rake recipe name='post title'"
    exit(1)
  end
  
  header_str = ''
  name.length.times { header_str << "-" }
  return [name, "#{name.gsub(/[^\w]+/, '-')}", header_str]
end