# RDoc Blog Generator

A lightweight, hackable, and developer-friendly static blog generator powered by Ruby's [RDoc](https://github.com/ruby/rdoc).

Turn your plain text, Markdown, or RDoc files into a clean, searchable, and fast static blog.

## Features

*   **Zero Dependencies**: Uses standard RDoc (with a tiny monkey patch) to generate your site.
*   **Plain Text Posts**: Write in `.rdoc`, `.md`, or `.txt`.
*   **Developer Friendly**: It's just Ruby. Hack it, patch it, extend it.
*   **Fast & Clean**: Generates static HTML. No database, no complex build pipeline.
*   **Built-in Search**: Full-text search for your blog posts (excluding classes/methods).
*   **Themable**: Supports standard RDoc themes (Darkfish, Aliki).
*   **One-Command Install**: Get started in seconds.

## Quick Start

### Installation

You can install the RDoc Blog Generator using our standalone installer. Run this in your terminal:

```bash
curl -L https://github.com/metacritical/rdoc_blog/releases/latest/download/install.rb | ruby
```


The installer is interactive and will ask you where to create your new blog.

### Manual Installation

1.  Clone this repository:
    ```bash
    git clone git@github.com:metacritical/rdoc_blog.git
    cd rdoc_blog
    ```
2.  Run the generator:
    ```bash
    bin/rdoc-blog
    ```

## Usage

### 1. Configuration

Edit `config.yml` in your blog directory:

```yaml
title: "My Tech Blog"
theme: "darkfish" # or "aliki"
posts_dir: "posts"
output_dir: "public"
```

### 2. Writing Posts

Create a new file in the `posts/` directory. You can use `.rdoc`, `.md`, or `.txt` extensions.

**Example (`posts/hello_world.rdoc`):**

```rdoc
Title: "Hello World"

Author:: Jane Doe
Date:: 2024-01-20

== Welcome

This is my first post using RDoc Blog! It supports *bold*, _italic_, and +code+.

  def ruby_code
    puts "Hello!"
  end
```

**Important**: The `Title: "..."` directive at the top of the file is required to set the page title in the navigation.

### 3. Generating the Site

Run the build script:

```bash
bin/rdoc-blog
```

This will generate your static site in the `public/` directory (or whatever you configured as `output_dir`).

### 4. Deployment

Simply upload the contents of the `public/` directory to any static site host (GitHub Pages, Netlify, Vercel, Amazon S3, etc.).

## Customization

The core logic lives in `lib/rdoc_blog/monkey_patch.rb`. This file patches RDoc to:
1.  Extract the `Title:` directive.
2.  Clean up the sidebar (removing Classes/Methods).
3.  Customize the search index to only include pages.

Feel free to modify this file to add your own features!

## License

MIT
