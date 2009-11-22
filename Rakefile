#!/usr/bin/env rake
require 'rubygems' # I actually use it, not excess.

SCM_TEMPLATE = File.expand_path('../template', __FILE__)
USR_TEMPLATE = File.expand_path(File.join(Gem.user_home, '.hoe_template'))

SCM_GLOB = File.join(SCM_TEMPLATE, '**', '*')
USR_GLOB = File.join(USR_TEMPLATE, '**', '*')

SCM_FILES = FileList[SCM_GLOB]
USR_FILES = FileList[USR_GLOB]

SCM_FILES.zip(USR_FILES).each do |scm, usr|
  file usr => scm do
    cp scm => usr
  end
end

desc "Copy in files, overwriting if newer"
task :copy => USR_FILES

desc "Diff directories"
task :diff do
  sh "diff #{SCM_TEMPLATE} #{USR_TEMPLATE}"
end

desc "Link user template to repo (good for forks)"
task :link do
  ln_s SCM_TEMPLATE, USR_TEMPLATE
end