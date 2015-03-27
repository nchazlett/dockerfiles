FROM bcroq/stackless:2.7.9

RUN apt-get update \
        && apt-get install -y mercurial

RUN set -x \
        && mkdir /var/tmp/pypi \
        && hg clone http://hg.nagare.org/core nagare -r "0.4.1" \
        && apt-get purge -y mercurial 'python.*' \
        && rm -rf /var/lib/apt/lists/* \
        && cd nagare \
        && python setup.py sdist \
        && mv dist/* /var/tmp/pypi \
        && cd .. \
        && rm -rf nagare \
    && easy_install -Z --find-links=/var/tmp/pypi nagare

ENTRYPOINT ["nagare-admin"]
