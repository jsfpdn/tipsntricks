# Installing dependencies

## Installing virtualenv, virtualenvwrapper

```bash
> sudo easy_install pip
> pip install virtualenv
> pip install virtualenvwrapper
```

## Switching between python3.6 and python3.7 with brew

```bash
> brew unlink python
> brew install --ignore-dependencies https://raw.githubusercontent.com/Homebrew/homebrew-core/f2a764ef944b1080be64bd88dca9a1d80130c558/Formula/python.rb
```

* to switch between different version use `brew switch python3.x.y`

## Fix ``dyld: Library not loaded: @executable_path/../.Python``

* all symlinks in `pyenv` directorie are invalid,
  you need to delete all of them and create new ones:

```bash
> find ~/.virtualenvs/my-virtual-env l # this shows the symlinks
> find ~/.virtualenvs/my-virtual-env l -delete
> virtualenv ~/.virtualenvs/my-virtual-env
```

## Libs

* psycopg2: `env LDFLAGS="-I/usr/local/opt/openssl/include -L/usr/local/opt/openssl/lib" pip3 --no-cache install psycopg2`
  * add `LDFLAGS` to `.zshrc` to make it work when installing deps from tox 

## Testing

* show available fixtures: `pytest --fixtures test_simplefactory.py`

* `unittest` supports distinguishing test iterations (will not exit on first failed test), i.e.:

```python
class NumbersTest(unittest.TestCase):

    def test_even(self):
        """
        Test that numbers between 0 and 5 are all even.
        """
        for i in range(0, 6):
            with self.subTest(i=i):
                self.assertEqual(i % 2, 0)
```

will produce

```bash
======================================================================
FAIL: test_even (__main__.NumbersTest) (i=1)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "subtests.py", line 32, in test_even
    self.assertEqual(i % 2, 0)
AssertionError: 1 != 0

======================================================================
FAIL: test_even (__main__.NumbersTest) (i=3)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "subtests.py", line 32, in test_even
    self.assertEqual(i % 2, 0)
AssertionError: 1 != 0

======================================================================
FAIL: test_even (__main__.NumbersTest) (i=5)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "subtests.py", line 32, in test_even
    self.assertEqual(i % 2, 0)
AssertionError: 1 != 0
```
