# Make - How to fix README.md source missing separator. Stop.

When you got:

```
Makefile:2: *** missing separator.  Stop.
```

or

```
* missing separator (did you mean TAB instead of 8 spaces?). Stop.
```

It's easy to fix it. Use ``Tab`` instead of space in your ``Makefile``.

You can fix it by changing ``Spaces`` to ``Tab`` characters. Simply open your ``Makefile``

```
$ vim Makefile
```

And then run the following command within:

```
:%s/^[ ]\+/^I/
```

This will substitute all the lines begin with one or more ``Spaces`` character with an actual ``Tab``.
