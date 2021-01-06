# Django Messages DRF

[![CircleCi](https://img.shields.io/circleci/project/github/tarsil/django-messages-drf.svg)](https://circleci.com/gh/tarsil/django-messages-drf)
[![codecov](https://codecov.io/gh/tarsil/django-messages-drf/branch/master/graph/badge.svg?token=VfTlWQlGeF)](https://codecov.io/gh/tarsil/django-messages-drf)

---

## Table of Contents

- [About Django Messages DRF](#about-django-messages-drf)
  - [Overview](#overview)
  - [Versions](#supported-django-and-python-versions)
- [Documentation](#documentation)
  - [Installation](#installation)
  - [Reference Guide](#reference-guide)
    - [Matrix](#url–view–template-matrix)
    - [URL Names](#url-names)
    - [Views](#views)
    - [Signals](#signals)
- [CHANGELOG](#changelog)
  - [1.0.2](#102)
  - [1.0.1](#101)
  - [1.0.0](#100)
- [License](#license)

---

## About Django Messages DRF

Django Messages DRF is an alternative of pinax-messages but using
Django Rest Framework making it easier to integrate with your existing project.

Django Messages DRF is based on pinax-messages but applying DRF.

A special thanks to pinax for inspiring me to do this and use some ideas.

### Overview

`django-messages-drf` is an app for providing private user-to-user threaded
messaging.

#### Supported Django and Python Versions

| Django / Python | 3.6 | 3.7 | 3.8 | 3.9
| --------------- | --- | --- | --- | ---
| 2.2  | Yes | Yes | Yes | Yes
| 3.0  | Yes | Yes | Yes | Yes
| 3.1  | Yes | Yes | Yes | Yes

## Documentation

### Installation

To install django-messages:

```shell
    pip install django-messages-drf
```

Add `django_messages_drf` to your `INSTALLED_APPS` setting:

```python
INSTALLED_APPS = [
    # other apps
    "django_messages_drf",
]
```

Run Django migrations to create `django-messages-drf` database tables:

```shell
    python manage.py migrate
```

Add `django_messages_drf.urls` to your project urlpatterns:

```python
    urlpatterns = [
        # other urls
        url(r"^messages-drf/", include("django_messages_drf.urls", namespace="django_messages_drf")),
    ]
```

### Reference Guide

#### URL–View–Template Matrix

| URL Name  | View   |
| :-------- | :----- |
| `django_messages_drf:inbox`               | `InboxListApiView()` |
| `django_messages_drf:thread`      | `ThreadListApiView()` |
| `django_messages_drf:thread-create` | `ThreadCRUDApiView()` |
| `django_messages_drf:thread-send`       | `ThreadCRUDApiView()` |
| `django_messages_drf:thread-delete`       | `ThreadCRUDApiView()` |

#### URL Names

These URL names are available when using django_messages_drf urls.py:

- `django_messages_drf:inbox` — Inbox view.
- `django_messages_drf:thread` — Lists the details of a tread of a User.
Requires a UUID of a thread.
- `django_messages_drf:thread-create` — Create new message to specific user.
Requires a User PK (user to send).
- `django_messages_drf:thread-send` — Replies to a thread. requires thread UUID.
- `django_messages_drf:thread-delete` — Delete message thread, requires thread
UUID.

#### Views

- `InboxListApiView` - Display all message threads
- `ThreadCRUDApiView` - Create a new message thread/Reply to Thread
- `ThreadListApiView` - View specific message thread
- `ThreadCRUDApiView` - Delete specific message thread

#### Signals

`message_sent` — `providing_args = ["message", "thread", "reply"]`

## ChangeLog

### 1.0.2

- Added support for python 3.9

### 1.0.1

- Fixed tests naming conflicts.
- Fixed migration issues.
- Updated README.md to make it clearer.
- Added CircleCI config

### 1.0.0

- Initial release

## License

Copyright (c) 2020-present Tiago Silva and contributors under the [MIT license](https://opensource.org/licenses/MIT).
