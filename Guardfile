guard :shell do
#guard 'rake', :task => 'build:stylesheets' do
  watch(%r{^stylesheets/.+\.scss$}) { `rake build:stylesheets` }
end

guard :shell do
#guard 'rake', :task => 'build:pages' do
  watch(%r{^layout.html.haml$}) { `rake build:pages` }
  watch(%r{^pages/.+\.html\.}) { `rake build:pages` }
end

guard 'livereload' do
  watch(%r{^site(/.+)}) { |path| path }
end
