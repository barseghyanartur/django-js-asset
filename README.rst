===============================================================================
django-js-asset -- script tag with additional attributes for django.forms.Media
===============================================================================

.. image:: https://travis-ci.org/matthiask/django-js-asset.svg?branch=master
    :target: https://travis-ci.org/matthiask/django-js-asset

Usage
=====

Use this to insert a script tag via ``forms.Media`` containing additional
attributes (such as ``id`` and ``data-*`` for CSP-compatible data
injection.)::

    media.add_js([
        JS('asset.js', {
            'id': 'asset-script',
            'data-answer': '"42"',
        }),
    ])

The rendered media tag (via ``{{ media.js }}`` or ``{{ media }}`` will
now contain a script tag as follows, without line breaks::

    <script type="text/javascript" src="/static/asset.js"
        data-answer="&quot;42&quot;" id="asset-script"></script>

The attributes are automatically escaped. The data attributes may now be
accessed inside ``asset.js``::

    var answer = document.querySelector('#asset-script').dataset.answer;