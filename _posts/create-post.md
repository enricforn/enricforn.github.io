 Steps to create a new post and debug in your local machine:

- Create new file.md and new folder in post

- Install Jekyll from ruby gem (https://jekyllrb.com/docs/installation/windows/):

    · Install ruby with devkit (https://rubyinstaller.org/downloads/) or choco install ruby.

    · Run ridk install.

    · Install Jekyll gem by running command: gem install jekyll bundler.

    · Check if Jekyll is properly installed: jekyll -v

- Go to root path jekyll blog.

- Run: bundle install

- Run: jekyll build

- Run: jekyll serve --trace --watch --incremental --future --draft

Recomendations:

- Start writing posts from the draft folder.