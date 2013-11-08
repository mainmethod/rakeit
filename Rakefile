namespace :git do
  task :default do
    if(!system("command -v git >/dev/null 2>&1"))
      puts "git not found"
    end
    exit
  end
  
  namespace :ignore do
    desc "adds file or path to .gitignore"
    task :add, :entry do |t, args|
      File.open('.gitignore','a+') do |file|
        append = true
        file.each_line do |line|
          append = false if line.strip == args[:entry].strip
        end
        if append
          file.puts args[:entry]
          puts "  #{args[:entry]} added to .gitignore"
        else
          puts "  #{args[:entry]} already exists. nothing added"
        end
      end
    end
    
    desc "removes file or path from .gitignore"
    task :remove, :entry do |t, args|
      lines_array = File.readlines('.gitignore')
      File.open('.gitignore','w') do |file|
        lines_array.each do |line|
          if(line.strip != args[:entry].strip)
            file.puts line.strip
          else
            puts "  #{args[:entry]} removed"
          end
        end
      end
    end
  end
  
end

task :gitignore => 'git:default'
