namespace :thesis do
  desc 'build basic thesis formats'
  task :build do

    begin
      version_string = ENV['TRAVIS_TAG'] || `git describe --tags`.chomp
      if version_string.empty?
        version_string = '0'
      end
      date_string = Time.now.strftime("%Y-%m-%d")
      params = "--attribute revnumber='#{version_string}' --attribute revdate='#{date_string}' --destination-dir output -r asciidoctor-bibliography"

      puts "Converting to HTML..."
      `bundle exec asciidoctor #{params} thesis.asc`
      puts " -- HTML output at output/thesis.html"

      # puts "Converting to EPub..."
      # `bundle exec asciidoctor-epub3 #{params} thesis.asc`
      # puts " -- Epub output at output/thesis.epub"

      # puts "Converting to Mobi (kf8)..."
      # `bundle exec asciidoctor-epub3 #{params} -a ebook-format=kf8 thesis.asc`
      # puts " -- Mobi output at output/thesis.mobi"

      # puts "Converting to PDF... (this one takes a while)"
      # `bundle exec asciidoctor-pdf #{params} thesis.asc 2>/dev/null`
      # puts " -- PDF output at output/thesis.pdf"

    end
  end
end

task :default => "thesis:build"
