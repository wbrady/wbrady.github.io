desc "Deploy"
task :deploy do
  puts "Building site"
  `bundle exec jekyll build`

  puts "## Deploying to Github Pages.."

  (Dir["deploy/*"]).each { |f| rm_rf(f) }

  puts "## Copying _site/ to deploy/"
  cp_r "_site/.", 'deploy'

  cd "deploy" do
    system "git add ."
    system "git add -u"

    puts "## Commiting: Site updated at #{Time.now.utc}"
    message = "Site updated at #{Time.now.utc}"
    system "git commit -m \"#{message}\""

    puts "## Pushing generated deploy website"
    system "git push origin master --force"

    puts "## Deploy Complete!"
  end
end
