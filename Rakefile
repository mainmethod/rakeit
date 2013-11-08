namespace :git do
  task :default do
    if(!system("command -v git >/dev/null 2>&1"))
      puts "git not found"
    end
    exit
  end
  
  namespace :ignore do
    task :add, :entry do |t, args|
      File.open('.gitignore','a+') do |file|
        append = true
        file.each_line do |line|
          append = false if line.strip == args[:entry].strip
        end
        file.puts args[:entry] if append
      end
    end
    
    task :remove, :entry do |t, args|
      lines_array = File.readlines('.gitignore')
      File.open('.gitignore','w') do |file|
        lines_array.each do |line|
          file.puts line.strip if line.strip != args[:entry].strip
        end
      end
    end
  end
  
end

task :gitignore => 'git:default'
