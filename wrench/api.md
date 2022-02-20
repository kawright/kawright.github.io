---
title: wrench - API Reference
---

# wrench - API Reference {#section-title}

---

## Enums {#section-enums}

---

### enum *wr_CallbackReturn* {#api-wr_CallbackReturn}

This enum contains all values that may be returned by a *wrench* callback function.

#### Enumerators

##### *wr_RETOK* {#api-wr_RETOK}
: Indicates that the given test callback passed. Should only be returned by test callbacks.

##### *wr_RETNOK* {#api-wr_RETNOK}
: Indicates that the given test callback failed. Should only be returned by test callbacks.

##### *wr_RETBAIL* {#api-wr_RETBAIL}
: Indicates that the entire test suite should be “bailed out” of; that is, the test suite should be immediately aborted and no further tests should be performed. May be returned by any wrench callback.

##### *wr_RETSUOK* {#api-wr_RETSUOK}
: Indicates that the given setup function completed successfully. Should only be returned by setup callbacks.

##### *wr_RETSUNOK* {#api-wr_RETSUNOK}
: Indicates that the given setup function did not complete successfully. This will cause the subsequent test to be skipped. The teardown function, if given, will still be called. Should only be returned by setup callbacks.

##### *wr_RETSUNOKSKIPTD* {#api-wr_RETSUNOKSKIPTD}
: Indicates that the given setup function did not complete successfully, and that both the test AND teardown functions should be skipped. Should only be returned by setup callbacks.

##### *wr_RETTDOK* {#api-wr_RETTDOK}
: Indicates that the given teardown function completed successfully. Should only be returned by teardown callbacks.

##### *wr_RETTDNOK* {#api-wr_RETTDNOK}
: Indicates that the given teardown function did not complete successfully. Should only be returned by teardown callbacks.

---

### enum *wr_Directive* {#api-wr_Directive}

This enum contains all of the values used to indicate which (if any) directives should be applied to the output of a given test.

#### Enumerators

##### *wr_DIRNONE* {#api-wr_DIRNONE}
: No directives will be applied to the output of the given test.

##### *wr_DIRTODO* {#api-wr_DIRTODO}
: The TODO directive will be applied to the output of the given test.

##### *wr_DIRSKIP* {#api-wr_DIRSKIP}
: The SKIP directive will be applied to the output of the given test.

---

### enum *wr_ErrorCode* {#api-wr_ErrorCode}

This enum contains all values which may be returned by a function in the wrench API. These values indicate either the succes of the function returning them, or what type of error occurred during the function’s execution.

#### Enumerators

##### *wr_ERROK* {#api-wr_ERROK}
: The function complted execution successfully. No error occurred.

##### *wr_ERRMEM* {#api-wr_ERRMEM}
: An error occurred while attempting to allocate or reallocate heap memory.

##### *wr_ERRIO* {#api-wr_ERRIO}
: An error occurred attempting to access a local file.

##### *wr_ERREMPTY* {#api-wr_ERREMPTY}
: An attempt to run an empty suite was made.

---

### enum *wr_SuiteResult* {#api-wr_SuiteResult}

This enum contains values which indicate the status of an entire test suite after its completion.

#### Enumerators

##### *wr_SRESOK* {#api-wr_SRESOK}
: All tests in the suite either passed, or were skipped.

##### *wr_SRESNOK* {#api-wr_SRESNOK}
: At least one test failed.

##### *wr_SRESBAIL* {#api-wr_SRESBAIL}
: The suite was bailed out of before it could complete.

---