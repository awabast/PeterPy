"""Run the EasyInstall command"""

if __name__ == '__main__':
    from setuptools.command.easy_install import main
    main()
#!/usr/bin/env python
# coding=utf-8
"""
PeterPy setup file.
"""
import os
import sys
import platform
import configparser
from setuptools import setup


if sys.version_info[0] < 3:
    raise Exception(
        'You are tying to install PeterPy on Python version {}.\n'
        'Please install PeterPy in Python 3 instead.'.format(
            platform.python_version()
        )
    )

config = configparser.ConfigParser()

current_directory = os.path.dirname(os.path.abspath(__file__))
config_file_path = os.path.join(current_directory, 'setup.cfg')

config.read(config_file_path)

VERSION = config['PeterPy']['version']
AUTHOR = config['PeterPy']['author']
AUTHOR_EMAIL = config['PeterPy']['email']
URL = config['PeterPy']['url']

with open('README.md') as f:
    LONG_DESCRIPTION = f.read()

REQUIREMENTS = []
DEPENDENCIES = []

with open('requirements.txt') as requirements:
    for requirement in requirements.readlines():
        if requirement.startswith('git+git://'):
            DEPENDENCIES.append(requirement)
        else:
            REQUIREMENTS.append(requirement)


setup(
    name='PeterPy',
    version=VERSION,
    url=URL,
    download_url='{}/tarball/{}'.format(URL, VERSION),
    project_urls={
        'Documentation': 'https://chatterbot.readthedocs.io',
    },
    description='PeterPy is a machine learning, conversational dialog engine.',
    long_description=LONG_DESCRIPTION,
    long_description_content_type='text/markdown',
    author=AUTHOR,
    author_email=AUTHOR_EMAIL,
    packages=[
        'PeterPy',
        'PeterPy.storage',
        'PeterPy.logic',
        'PeterPy.ext',
        'PeterPy.ext.sqlalchemy_app',
        'PeterPy.ext.django_PeterPy',
        'PeterPy.ext.django_PeterPy.migrations',
    ],
    package_dir={'chatterbot': 'PeterPy'},
    include_package_data=True,
    install_requires=REQUIREMENTS,
    dependency_links=DEPENDENCIES,
    python_requires='>=3.4, <=3.8',
    license='BSD',
    zip_safe=True,
    platforms=['any'],
    keywords=['ChatterBot', 'PeterPy', 'chat', 'bot'],
    classifiers=[
        'Development Status :: 4 - Beta',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: BSD License',
        'Environment :: Console',
        'Environment :: Web Environment',
        'Operating System :: OS Independent',
        'Topic :: Software Development :: Libraries :: Python Modules',
        'Topic :: Communications :: Chat',
        'Topic :: Internet',
        'Programming Language :: Python',
        'Programming Language :: Python :: 3',
        'Programming Language :: Python :: 3.4',
        'Programming Language :: Python :: 3.5',
        'Programming Language :: Python :: 3.6',
        'Programming Language :: Python :: 3.7',
        'Programming Language :: Python :: 3.8',
        'Programming Language :: Python :: 3 :: Only',
    ],
    test_suite='tests'
)
[wheel]
universal = 1

[bdist_wheel]
universal = 1

[metadata]
license_file = LICENSE

[nosetests]
verbosity = 2
nocapture = true
exclude = (?:^tests_django$)
with-coverage = true
cover-package = PeterPy
cover-erase = true
cover-min-percentage = 40

[flake8]
# H306: imports not in alphabetical order (time, os)
ignore = H306
max_line_length = 175
exclude = .eggs, .git, .tox, build,

[PeterPy]
version = 1.0.8
author = awabast
email = awabast@gmail.com
url = https://github.com/awabast/PeterPy
[tox]
skipsdist = True

[testenv]
passenv = DJANGO_SETTINGS_MODULE PYTHONPATH HOME DISPLAY
setenv = PYTHONDONTWRITEBYTECODE=1
deps =
  django111: Django>=1.11,<1.12
  django20: Django>=2.0,<2.1
  -rrequirements.txt
  -rdev-requirements.txt
commands_pre =
  python -m spacy link en_core_web_sm en
  python -m spacy link de_core_news_sm de

[testenv:docs]
commands = sphinx-build -nW -b html ./docs/ {envtmpdir}/build/

[testenv:lint]
deps = flake8
commands_pre =
commands = flake8

[testenv:test]
commands =
  nosetests

[testenv:django111]
commands =
  python setup.py develop --no-deps
  python runtests.py
  python examples/django_app/manage.py test examples/django_app/

[testenv:django20]
commands =
  python setup.py develop --no-deps
  python runtests.py
  python examples/django_app/manage.py test examples/django_app/
# encoding: utf-8
# module typing.io
# from (pre-generated)
# by generator 1.147
""" Wrapper namespace for IO generic classes. """

# imports
import typing as __typing


# no functions
# classes

class IO(__typing.Generic):
    """
    Generic base class for TextIO and BinaryIO.
    
        This is an abstract, generic version of the return of open().
    
        NOTE: This does not distinguish between the different possible
        classes (text vs. binary, read vs. write vs. read/write,
        append-only, unbuffered).  The TextIO and BinaryIO subclasses
        below capture the distinctions between text vs. binary, which is
        pervasive in the interface; however we currently do not offer a
        way to track the other distinctions in the type system.
    """
    def close(self): # reliably restored by inspect
        # no doc
        pass

    def fileno(self): # reliably restored by inspect
        # no doc
        pass

    def flush(self): # reliably restored by inspect
        # no doc
        pass

    def isatty(self): # reliably restored by inspect
        # no doc
        pass

    def read(self, n=-1): # reliably restored by inspect
        # no doc
        pass

    def readable(self): # reliably restored by inspect
        # no doc
        pass

    def readline(self, limit=-1): # reliably restored by inspect
        # no doc
        pass

    def readlines(self, hint=-1): # reliably restored by inspect
        # no doc
        pass

    def seek(self, offset, whence=0): # reliably restored by inspect
        # no doc
        pass

    def seekable(self): # reliably restored by inspect
        # no doc
        pass

    def tell(self): # reliably restored by inspect
        # no doc
        pass

    def truncate(self, size=None): # reliably restored by inspect
        # no doc
        pass

    def writable(self): # reliably restored by inspect
        # no doc
        pass

    def write(self, s): # reliably restored by inspect
        # no doc
        pass

    def writelines(self, lines): # reliably restored by inspect
        # no doc
        pass

    def __enter__(self): # reliably restored by inspect
        # no doc
        pass

    def __exit__(self, type, value, traceback): # reliably restored by inspect
        # no doc
        pass

    def __init__(self, *args, **kwargs): # real signature unknown
        pass

    closed = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    mode = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    name = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default


    __orig_bases__ = (
        typing.Generic[~AnyStr],
    )
    __parameters__ = (
        None, # (!) real value is '~AnyStr'
    )
    __slots__ = ()


class BinaryIO(__typing.IO):
    """ Typed version of the return of open() in binary mode. """
    def write(self, s): # reliably restored by inspect
        # no doc
        pass

    def __enter__(self): # reliably restored by inspect
        # no doc
        pass

    def __init__(self, *args, **kwargs): # real signature unknown
        pass

    __orig_bases__ = (
        typing.IO[bytes],
    )
    __parameters__ = ()
    __slots__ = ()


class TextIO(__typing.IO):
    """ Typed version of the return of open() in text mode. """
    def __enter__(self): # reliably restored by inspect
        # no doc
        pass

    def __init__(self, *args, **kwargs): # real signature unknown
        pass

    buffer = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    encoding = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    errors = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    line_buffering = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default

    newlines = property(lambda self: object(), lambda self, v: None, lambda self: None)  # default


    __orig_bases__ = (
        typing.IO[str],
    )
    __parameters__ = ()
    __slots__ = ()


# variables with complex values

__all__ = [
    'IO',
    'TextIO',
    'BinaryIO',
]

__weakref__ = None # (!) real value is "<attribute '__weakref__' of 'typing.io' objects>"


