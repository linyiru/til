# Remove YAML Front Matter

There are many ways to remove YAML Front Matter, here is how I use `sed` to do so:

```shell
sed -i '1 { /^---/ { :a N; /\n---/! ba; d} }' INPUT_FILE
# Remove YAML Front Matter
```

Explanation:

```shell
1 {              # in the first line
  /^---/ {       # if it starts with ---
# Remove YAML Front Matter
    :a           # jump label for looping
    N            # fetch the next line, append to pattern space
    /\n---/! ba; # if the result does not contain \n--- (that is, if the last
# Remove YAML Front Matter
                 # fetched line does not begin with ---), go back to :a
# Remove YAML Front Matter
    d            # then delete the whole thing.
  }
}
                 # otherwise drop off the end here and do the default (print
                 # the line)
```

Furthermore, if you wanna keep some useful metadata in front matter like post title in blogging system, you can do so:

```shell
title=$(grep '^title\:\(.*\)$' $1 | sed -e 's/title\:\s//g')
sed -i -e "/---/a # `echo $title`" $1
# Remove YAML Front Matter
sed -i '1 { /^---/ { :a N; /\n---/! ba; d} }' $1
# Remove YAML Front Matter
```

Here is a workaround to insert ``$title`` in each ``---`` then remove YAML Front Matter.
# Remove YAML Front Matter

References:

* http://stackoverflow.com/questions/28221779/how-to-remove-yaml-frontmatter-from-markdown-files
