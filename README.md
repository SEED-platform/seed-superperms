seed-superperms
==========

## Install

install superperms
<!---
```py
pip install superperms
```
--->
add superperms to your `INSTALLED_APPS`

```py
INSTALLED_APPS = (
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.flatpages',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django.contrib.sites',
    'django.contrib.humanize',
    'django.contrib.admin',

    'superperms.orgs',
)
```

## Configuration Options

 -  ``ALLOW_SUPER_USER_PERMS``: Allows Django super_user class accounts to bypass permissions checks. This is useful mainly for development, but defaults to ``True``.



## Example Usage

- To limit views to people who have member-level roles and above, you could use the following decorator definiition. Users who are ``viewers`` will recieve a Django ``HttpRequestNotAuthorized`` response (e.g. a 403) without ever executing the code inside the view.


```python

from superperms.orgs.decorators import has_perm #  Imports our decorator factory.

# This view will be protected against anybody whose account is "lower"
# than a member. Default role types include ['owner', 'member', 'viewer'].
@has_perm('requires_member')
def protected_view(request):
    pass

```


## Development and Testing

clone the repo and install requirements

```console
$ git clone git@github.com:seed-platform/seed-superperms.git
$ mkvirtualenv superperms
(superperms)$ cd superperms
(superperms)$ pip install -r requirements.txt
```

tests should pass, PEP8 is enforced

```console
(superperms)$ ./test.sh
```

## Copyright
Copyright ©  2014 Building Energy Inc.
