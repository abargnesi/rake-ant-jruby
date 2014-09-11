require 'ant'

src_dir = 'src/main/java'
build_dir = 'target'
classes_dir = "#{build_dir}/classes"
jar_file = "#{build_dir}/project.jar"

namespace :ant do
  desc "Compile the code using Ant"
  task :compile do
    puts "Compiling java from #{src_dir} to #{classes_dir}"
    ant.javac :srcdir => src_dir, :destdir => classes_dir do
      classpath do
        FileList["lib/*.jar"].each do |jar|
          pathelement :path => jar
        end
      end
    end
  end

  desc "Create a jar file of the compiled code using Ant"
  task :jar => "ant:compile" do
    puts "Creating #{jar_file}"
    ant.jar :destfile => jar_file, :basedir => classes_dir
  end
end
