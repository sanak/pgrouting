..
   ****************************************************************************
    pgRouting Manual
    Copyright(c) pgRouting Contributors

    This documentation is licensed under a Creative Commons Attribution-Share
    Alike 3.0 License: https://creativecommons.org/licenses/by-sa/3.0/
   ****************************************************************************

|

.. index::
   single: Flow Family ; edmondsKarp
   single: edmondsKarp

``pgr_edmondsKarp``
===============================================================================

``pgr_edmondsKarp`` — Calculates the flow on the graph edges that maximizes the
flow from the sources to the targets using Edmonds Karp Algorithm.

.. figure:: images/boost-inside.jpeg
   :target: https://www.boost.org/libs/graph/doc/push_relabel_max_flow.html

   Boost Graph Inside

.. Rubric:: Availability

* Version 3.2.0

  * New **proposed** signature

    * ``pgr_edmondsKarp`` (`Combinations`_)

* Version 3.0.0

  * **Official** function

* Version 2.5.0

  * Renamed from ``pgr_maxFlowEdmondsKarp``
  * **Proposed** function

* Version 2.3.0

  * New **Experimental** function


Description
-------------------------------------------------------------------------------

.. include::  flow-family.rst
    :start-after: characteristics_start
    :end-before: characteristics_end

* Running time: :math:`O( V * E ^ 2)`

Signatures
-------------------------------------------------------------------------------

.. rubric:: Summary

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, **start vid**, **end vid**)
   | pgr_edmondsKarp(`Edges SQL`_, **start vid**, **end vids**)
   | pgr_edmondsKarp(`Edges SQL`_, **start vids**, **end vid**)
   | pgr_edmondsKarp(`Edges SQL`_, **start vids**, **end vids**)
   | pgr_edmondsKarp(`Edges SQL`_, `Combinations SQL`_)

   | Returns set of |result-flow|
   | OR EMPTY SET

.. index::
    single: edmondsKarp ; One to One

One to One
...............................................................................

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, **start vid**, **end vid**)

   | Returns set of |result-flow|
   | OR EMPTY SET

:Example: From vertex :math:`11` to vertex :math:`12`

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q1
   :end-before: -- q2

.. index::
    single: edmondsKarp ; One to Many

One to Many
...............................................................................

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, **start vid**, **end vids**)

   | Returns set of |result-flow|
   | OR EMPTY SET

:Example: From vertex :math:`11` to vertices :math:`\{5, 10, 12\}`

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q2
   :end-before: -- q3

.. index::
    single: edmondsKarp ; Many to One

Many to One
...............................................................................

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, **start vids**, **end vid**)

   | Returns set of |result-flow|
   | OR EMPTY SET

:Example: From vertices :math:`\{11, 3, 17\}` to vertex :math:`12`

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q3
   :end-before: -- q4

.. index::
    single: edmondsKarp ; Many to Many

Many to Many
...............................................................................

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, **start vids**, **end vids**)

   | Returns set of |result-flow|
   | OR EMPTY SET

:Example: From vertices :math:`\{11, 3, 17\}` to vertices :math:`\{5, 10, 12\}`

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q4
   :end-before: -- q5

.. index::
    single: edmondsKarp ; Combinations - Proposed on v3.2

Combinations
...............................................................................

.. admonition:: \ \
   :class: signatures

   | pgr_edmondsKarp(`Edges SQL`_, `Combinations SQL`_)

   | Returns set of |result-flow|
   | OR EMPTY SET

:Example: Using a combinations table, equivalent to calculating result from
          vertices :math:`\{5, 6\}` to vertices :math:`\{10, 15, 14\}`.

The combinations table:

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q5
   :end-before: -- q51

The query:

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q51
   :end-before: -- q6

Parameters
-------------------------------------------------------------------------------

.. include:: dijkstra-family.rst
    :start-after: dijkstra_parameters_start
    :end-before: dijkstra_parameters_end

Inner Queries
-------------------------------------------------------------------------------

Edges SQL
...............................................................................

.. include:: pgRouting-concepts.rst
    :start-after: flow_edges_sql_start
    :end-before: flow_edges_sql_end

Combinations SQL
...............................................................................

.. include:: pgRouting-concepts.rst
    :start-after: basic_combinations_sql_start
    :end-before: basic_combinations_sql_end

Result columns
-------------------------------------------------------------------------------

.. include:: flow-family.rst
    :start-after: result_flow_start
    :end-before: result_flow_end

Additional Examples
-------------------------------------------------------------------------------

:Example: Manually assigned vertex combinations.

.. literalinclude:: edmondsKarp.queries
   :start-after: -- q6
   :end-before: -- q7

See Also
-------------------------------------------------------------------------------

* :doc:`flow-family`

  * :doc:`pgr_boykovKolmogorov`
  * :doc:`pgr_pushRelabel`

* https://www.boost.org/libs/graph/doc/edmonds_karp_max_flow.html
* https://en.wikipedia.org/wiki/Edmonds%E2%80%93Karp_algorithm

.. rubric:: Indices and tables

* :ref:`genindex`
* :ref:`search`

