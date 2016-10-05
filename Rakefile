require 'asciidoctor'
require 'asciidoctor-revealjs'

#        :backend => 'dzslides',
#        :template_dir => 'asciidoctor-backends/slim/'

desc "Generate html pages using reveal.js"
task :generateReveal, [:filename, :output_dir] do |t, args|
    filename = args[:filename]
    output_dir = args[:output_dir]
    print "Generating Reveal for: \n  " + filename  + "|||"
    #TODO(shearer) use asciidoctor-revealjs directly, not through shell
    sh 'bundle exec asciidoctor-revealjs -a revealjsdir=https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.3.0 ' + filename
end

desc "Generate html pages using just asciidoctor"
task :generateHTML, [:filename, :output_dir] do |t, args|
    filename = args[:filename]
    output_dir = args[:output_dir]
    print "Generating HTML for: \n  " + filename + "|||"
    #TODO(shearer) use asciidoctor-revealjs directly, not through shell
    Asciidoctor.convert_file filename,
        :to_dir => output_dir
    puts ''
end
task :default do
    task(:generateHTML  ).execute( :filename => 'workshop01_settingUpABuildSystem.adoc')
    task(:generateReveal).execute( :filename => 'index.adoc' )
    task(:generateReveal).execute( :filename => 'lecture01_introduction.adoc')
    task(:generateReveal).execute( :filename => 'lecture02.adoc')

end
