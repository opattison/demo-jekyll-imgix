require 'bundler'
require 's3_website'

desc "custom Jekyll serve for local development (with imgix)"
task :serve do
  system "JEKYLL_ENV=production bundle exec jekyll serve"
end

# don’t try running this – it won’t work for you!
desc "build and deploy scripts, images and site to production servers via s3_website"
task :deploy do
  system "JEKYLL_ENV=production bundle exec jekyll build"
  system "s3_website push"
  puts "## Deployed site to S3 ##"
end
