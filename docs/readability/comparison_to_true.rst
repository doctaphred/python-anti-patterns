Comparing things to `True`
==========================

Per the PEP 8 Style Guide, values should not be compared to ``True``, but instead should be evaluated directly: ``if cond:``. This is more than just a stylistic guidline: using ``==`` or ``is`` can result in incorrect and hard-to-catch behavior if the value in question is a non-boolean object.

Anti-pattern
------------

The statements below are problematic because they use ``==`` and ``is`` to compare a boolean variable to ``True``.

.. code:: python

    flag = 1  # Objects that serve as flags don't have to just be True or False!

    if flag == True:
        print "The number 1 compares equal with True..."
        
    if flag is True:
        pass
    else:
        print "...but it's not the same object!"
        
    container = [1, 2, 3]
    
    if container == True:
        print "Nope."
        
    if container is True:
        print "Not gonna."
        
    if None == True:
        print "Of course this doesn't print."
        
    if None == False:
        print "But this also doesn't!"
    
    if None is False:
        print "This doesn't either!"


Best practices
--------------

The code below uses the PEP 8 preferred pattern of ``if cond:``. This works for any value of ``cond``.

.. code:: python

    flag = True

    if flag:
        print "PEP 8 Style Guide prefers this pattern"
        
    container = [1, 2, 3]
    
    if container:
        print "Yes! This container is not empty."
        
    if empty_container:
        print "Nope, empty_container evaluates False."
    
    for truthy_value in (True, 1, 2, -1, [1, 2, 3], [False], {None}, {False: False}, object()):
        if truthy_value:
            print "Always prints."
        
    for falsey_value in (False, 0, None, [], (), {}, set()):
        if mystery_falsey_value:
            print "Never prints."

References
----------

- pep8 - E712
- `PEP 8 Style Guide - Programming Recommendations <http://legacy.python.org/dev/peps/pep-0008/#programming-recommendations>`_
