# SharedMemory

Blog about tech stuff

Visit [sharedmemory!!!](https://braunbearded.github.io/sharedmemory/)

## Requirements

- install hugo for your os

## Usage

1. Clone Repo
2. Modify/Create the markdown files
3. Run `hugo`
4. from the root directory of this repo
5. commit changes, especially files in the docs folder
6. ???
7. profit

# Create a new post

If you want to create a new post do the following:

1. move to the root directory of this repo
2. run `hugo new hacks/0x00_quick-local-file-sharing.md`
3. set the correct `weight` and `title` in the header of the new markdown file
4. if you want to publish it remove `draft: true` from the header and check the `date`

## Hosting it locally

You can check your changes locally first:

```
hugo server
```

and visit `http://localhost:1313/sharedmemory/`

## Publish

If you happy with your changes then generate the html files in `doc` folder with:

```
hugo
```

Then commit the changes
