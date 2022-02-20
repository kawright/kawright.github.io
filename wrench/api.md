---
title: wrench - API Reference
---

wrench - API Reference
======================

Enums
-----

**enum** *wr_CallbackReturn*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This enum contains all values that may be returned by a `wrench` callback function.

- **enumerator** *wr_RETOK*: Indicates that the given test callback passed. Should only be returned by test callbacks.
- **enumerator** *wr_RETNOK*: Indicates that the given test callback failed. Should only be returned by test callbacks.
- **enumerator** *wr_RETBAIL*: Indicates that the entire test suite should be “bailed out” of; that is, the test suite should be immediately aborted and no further tests should be performed. May be returned by any wrench callback.
- **enumerator** *wr_RETSUOK*: Indicates that the given setup function completed successfully. Should only be returned by setup callbacks.
- **enumerator** *wr_RETSUNOK*: Indicates that the given setup function did not complete successfully. This will cause the subsequent test to be skipped. The teardown function, if given, will still be called. Should only be returned by setup callbacks.
- **enumerator** *wr_RETSUNOKSKIPTD*: Indicates that the given setup function did not complete successfully, and that both the test AND teardown functions should be skipped. Should only be returned by setup callbacks.
- **enumerator** *wr_RETTDOK*: Indicates that the given teardown function completed successfully. Should only be returned by teardown callbacks.
- **enumerator** *wr_RETTDNOK*: Indicates that the given teardown function did not complete successfully. Should only be returned by teardown callbacks.