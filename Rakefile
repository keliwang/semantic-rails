#!/usr/bin/env rake


ASSETS_FILE_LIST = ["packaged/css/semantic.min.css",
                    "packaged/javascript/semantic.min.js"]
ASSETS_DIR_LIST = ["packaged/fonts", "packaged/images"]

desc "Default task"
task :default => :create_release

desc "Create a temp directory for build release"
task :init_tmp_dir => :remove_tmp_dir do
  sh %{mkdir tmp}
end

desc "Remove temp directory"
task :remove_tmp_dir do
  sh %{rm -rf tmp}
end

desc "Download Semantic-UI release package"
task :download_semantic do
  sh %{wget http://semantic-ui.com/build/semantic.zip -O tmp/semantic.zip}
end

desc "Create release files"
task :create_release => [:init_tmp_dir, :download_semantic] do
  sh %{unzip -q tmp/semantic.zip -d tmp/}
  ASSETS_FILE_LIST.each do |file|
    sh %{cp tmp/#{file} .}
  end
  ASSETS_DIR_LIST.each do |dir|
    sh %{cp -r tmp/#{dir} .}
  end
end

desc "Clean up"
task :clean => [:remove_tmp_dir] do
end
