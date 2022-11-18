# Hydejack Starter Kit

A quicker, cleaner way to get started blogging with [Hydejack](https://hydejack.com/).

## Quick Start
### Running locally
1. Clone repository (git users), or [download] and unzip.
2. Open terminal, `cd` into root directory (where `_config.yml` is located)
3. Run `bundle install` [^1]
4. Run `bundle exec jekyll serve`
5. Open <http://localhost:4000/hydejack-starter-kit/>

## What's next?
* Open files and read the comments
* Read the [docs](https://hydejack.com/docs/)
* Buy the [PRO version](https://hydejack.com/download/) to get the project and resume layout, newsletter subscription box, custom forms, and more.

[^1]: Requires Bundler. Install with `gem install bundler`.

[download]: https://github.com/hydecorp/hydejack-starter-kit/archive/master.zip



```ruby
# touch -r 2018-02-19-illusion-of-requirements.markdown ~/workspace/hydejack-starter-kit/_posts/2018-02-19-illusion-of-requirements.markdown

old_directory = "/Users/tsedano/workspace/octopress/sedano.org/source/_posts"
new_directory = "/Users/tsedano/workspace/hydejack-starter-kit/_posts"
files = Dir["#{old_directory}/**/*.markdown"]
files.each do |file|
    file_name = file.split("/").last
    command = "touch -r #{old_directory}/#{file_name} #{new_directory}/#{file_name}"
    puts command
    `#{command}`
end
```
