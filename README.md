# README

## Building this site locally

1. `git clone https://github.com/dgmd/snippet.love`
2. `cd snippet.love`
3. `git checkout gh-pages`
4. `jekyll serve`
5. Navigate to [`http://localhost:4000`](http://localhost:4000) to see the site.

## Adding a snippet

What follows is a brief outline of how to add a snippet.  Please read through it in its entirety before creating a snippet, there are some subtleties in capturing a screencast and writing up your snippet to be aware of.

First: Create a new folder within `/snippets`; name it something short-but-summarizing, like `css-positioning`.  Everything below is included within this folder:

+ `background.png` — a _square_ PNG file.  This file will be used as the background to represent your snippet on the homepage.
+ `screencast.mp4` — an `mp4` file _less than 100MB_ in size
+ `code.html` — the entry point for the actual snippet (it may be the only file for the snippet).  If you have multiple files to include in your snippet, please be sure to look at the required YAML front-matter for `index.md`.
+ `extensions.md` — A numbered list of suggested extensions, ordered by increasing complexity.  Include any references which are uniquely pertinent to an extension here.
+ `readings.md` — A selection of references, videos, or related readings covering the same topic as the snippet.
+ `index.md` — An empty markdown file containing only YAML front-matter.  The front-matter should define at least the following variables:
  * `title`
  * `subtitle`
  * `layout: snippet-summary`
  * `category: snippet`
  * `screencast` should be `true` if there is a screencast to embed or `false` otherwise
  * `demoDescription` should contain a short, one sentence description of how to use the demo/what it does.
  * `files` should only be included if you have multiple files to include.  `files` should be a YAML Collection of filenames (see [Example 2.3 here](http://yaml.org/spec/1.0/#id2489726))

### Making `screencast.mp4`

When you record your screencast, you can do so using QuickTime Player:

1. Open QuickTime Player, select `File > New Screen Recording`
2. Make sure that the proper microphone is selected from the dropdown menu/arrow next to the red, record button.
3. Select the region of your screen _excluding_ the menu bar for recording.
4. Record your screencast, keeping it to less than fifteen minutes.
5. Use the `Edit > Trim` capacity to trim the screencast to just the time you need after ensuring it looks and sounds reasonable.
6. Save your screencast as `screencast.mov` file.
7. `brew install ffmpeg` if you don't have it already
8. Convert the MOV file to an MP4 (unfortunately, the QuickTime `mov` files produced do not cooperate with Google Chrome) by running the command `ffmpeg -i screencast.mov -acodec copy -vcodec copy converted-screencast.mp4` to convert the file to an MP4.
9. Download [Handbrake](https://handbrake.fr/), open your `converted-screencast.mp4` file, select the "Web-optimized" option, and use Handbrake to re-encode the MP4 and save it as `screencast.mp4`.
10. **Ensure `screencast.mp4` is less than 100MB** (it should be much less, ~25MB); GitHub doesn't permit larger files, and it's a pain to remove too-large files from a repository's history.
11. Place `screencast.mp4` in your snippet folder.

Note that if you're testing this site locally, `jekyll` will choke on large movie files and refuse to serve them.  This will present as a `<video>` tag failing to load, but throwing no error (_i.e._ the play button will be ghosted).

### Wrapping comments in `code.html`

`code.html` is the snippet itself.  For boring reasons, lines should be wrapped to ensure that they aren't longer than 80 characters.\

For multiline comments, this means that the comments need to be "hard-wrapped"—_i.e._ a newline character must be inserted at 80 characters.  Fortunately, you don't need to do this by hand.

If you're using Sublime Text, you can follow these steps:
1. Install the [`Sublime-Wrap-Plus`](https://github.com/ehuss/Sublime-Wrap-Plus) plugin _via_ PackageControl.
2. Write your comments as your normally would (you'll notice that in the includion of `code.html`, the multiline comments don't wrap).
3. After you're done with your comments, put your cursor in each comment and run `Wrap Lines` (you can do this _via_ `Cmd+Shift+P > Wrap Lines` or _via_ the default keyboard shortcut, `Cmd+alt+q`).

### GitHub-Flavored Markdown

All the files you create ending in `.md` will be interpreted as [`GitHub Flavored Markdown`](http://github.github.com/github-flavored-markdown/)

### Ready to deploy?

After you have added all of these files, please be sure to build and test the site locally by running `jekyll serve` from the top level of the directory and navigating to [`http://localhost:4000`](http://localhost:4000) to see that the site behaves as you expect.

After you've verified that it does, **please package your snippet addition as a single commit** and then `git push` them to preview them on the live site.

---

## Filing an issue

If you find an issue with a snippet, please [email us](mailto:dgmde15@gmail.com) and [file an issue](https://github.com/dgmd/snippet.love/issues).