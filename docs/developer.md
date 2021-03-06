# Developer notes

## Testing

Python is required for ReJSON's module test. Install it with `apt-get install python`. You'll also
need to have [redis-py](https://github.com/andymccurdy/redis-py) installed. The easiest way to get
it is using pip and running `pip install redis`.

The module's test can be run against an "embedded" disposable Redis instance, or against an instance
you provide to it. The "embedded" mode requires a path to the `redis-server` executable. The path is
stored in the `REDIS_SERVER_PATH` variable and can be set using CMake's `-D` switch as follows:

```bash
~/rejson$ cmake -D REDIS_SERVER_PATH=/path/to/redis-server --build build
```

Now, you can run the tests:

```bash
~/rejson$ cmake --build build --target test
...
```

Alternatively, to run only the module's unit test against a local instance listening at port 6379:

```bash
~/rejson$ cd build
~/rejson/build$ REDIS_PORT=6379 ctest -R redis_module
...
```

## Making the docs

1. You'll need `mkdocs`, install it with: `pip install mkdocs`
1. You'll also need the theme so: `pip install mkdocs-material`
1. To serve locally do: `mkdocs build && mkdocs serve`
1. To upload to GitHub Pages do: `mkdocs gh-deploy`