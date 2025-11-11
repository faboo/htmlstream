""""""""""
HTMLStream
""""""""""

HTMLStream is a simple stream parser for HTML. Rather than load an entire DOM into memory all at once, HTMLStream reads
a io stream incrementally, resulting in a stream of HTML tags and text. The aim is to be fairly permissible, generating
usable results from even malformed HTML.


========
Examples
========

Find the doc type of a document:


.. code-block:: python

    from htmlstream import Parses, DocType, Text

    def getDocType(filename:str) -> str:
        with open(filename, encoding='utf-8') as file:
            for node in Parser(file):
                if isinstance(node, Text): continue

                if isinstance(node, DocType):
                    return node.doctype
                else:
                    raise Exception('No doctype!')

