---
title: wrench - API Reference
---

# wrench - API Reference (Version 0.1.0) {#section-title}

Welcome to the API reference page for the *wrench* library.

Please keep in mind that all *0.x.y* releases are subject to unannounced backwards-incompatible changes to the API. Use these pre-release builds at your own risk!

## Page Contents

### [Enums](#section-enums)

- [wr_CallbackReturn](#api-wr_CallbackReturn)
- [wr_Directive](#api-wr_Directive)
- [wr_ErrorCode](#api-wr_ErrorCode)
- [wr_SuiteResult](#api-wr_SuiteResult)

### [Functions](#section-functions)

- [wr_attach](#api-wr_attach)
- [wr_enableplan](#api-wr_enableplan)
- [wr_enableskip](#api-wr_enableskip)
- [wr_enabletodo](#api-wr_enabletodo)
- [wr_errtostr](#api-wr_errtostr)
- [wr_getattach](#api-wr_getattach)
- [wr_getattachct](#api-wr_getattachct)
- [wr_getdesc](#api-wr_getdesc)
- [wr_gettestno](#api-wr_gettestno)
- [wr_newsuite](#api-wr_newsuite)
- [wr_newtest](#api-wr_newtest)
- [wr_regsetup](#api-wr_regsetup)
- [wr_regteardown](#api-wr_teardown)
- [wr_runsuite](#api-wr_runsuite)
- [wr_setrem](#api-wr_setrem)
- [wr_setsuiteprediags](#api-wr_setsuiteprediags)
- [wr_setsuitepostdiags](#api-wr_setsuitepostdiags)
- [wr_settestprediags](#api-wr_testprediags)
- [wr_settestpostdiags](#api-wr_testpostdiags)

### [Macros](#section-macros)

- [wr_ASSERTEQ](#api-wr_ASSERTEQ)
- [wr_ASSERTFALSE](#api-wr_ASSERTFALSE)
- [wr_ASSERTGT](#api-wr_ASSERTGT)
- [wr_ASSERTGTEQ](#api-wr_ASSERTGTEQ)
- [wr_ASSERTLT](#api-wr_ASSERTLT)
- [wr_ASSERTLTEQ](#api-wr_ASSERTLTEQ)
- [wr_ASSERTNEQ](#api-wr_ASSERTNEQ)
- [wr_ASSERTNOTNULL](#api-wr_ASSERTNOTNULL)
- [wr_ASSERTNULL](#api-wr_ASSERTNULL)
- [wr_ASSERTSTREQ](#api-wr_ASSERTSTREQ)
- [wr_ASSERTSTRGT](#api-wr_ASSERTSTRGT)
- [wr_ASSERTSTRGTEQ](#api-wr_ASSERTSTRGTEQ)
- [wr_ASSERTSTRLT](#api-wr_ASSERTSTRLT)
- [wr_ASSERTSTRLTEQ](#api-wr_ASSERTSTRLTEQ)
- [wr_ASSERTSTRNEQ](#api-wr_ASSERTSTRNEQ)
- [wr_ASSERTTRUE](#api-wr_ASSERTTRUE)
- [wr_BAILOUT](#api-wr_BAILOUT)
- [wr_SKIP](#api-wr_SKIP)
- [wr_TODO](#api-wr_TODO)

### [Types](#section-types)

- [wr_Callback](#api-wr_Callback)
- [wr_Suite](#api-wr_Suite)
- [wr_Test](#api-wr_Test)
- [wr_TestContext](#api-wr_TestContext)

---

## Enums {#section-enums}

---

### enum *wr_CallbackReturn* {#api-wr_CallbackReturn}

This enum contains all values that may be returned by a *wrench* callback function.

#### ENUMERATORS

##### *wr_RETOK* {#api-wr_RETOK}
Indicates that the given test callback passed. Should only be returned by test callbacks.

##### *wr_RETNOK* {#api-wr_RETNOK}
Indicates that the given test callback failed. Should only be returned by test callbacks.

##### *wr_RETBAIL* {#api-wr_RETBAIL}
Indicates that the entire test suite should be “bailed out” of; that is, the test suite should be immediately aborted and no further tests should be performed. May be returned by any wrench callback.

##### *wr_RETSUOK* {#api-wr_RETSUOK}
Indicates that the given setup function completed successfully. Should only be returned by setup callbacks.

##### *wr_RETSUNOK* {#api-wr_RETSUNOK}
Indicates that the given setup function did not complete successfully. This will cause the subsequent test to be skipped. The teardown function, if given, will still be called. Should only be returned by setup callbacks.

##### *wr_RETSUNOKSKIPTD* {#api-wr_RETSUNOKSKIPTD}
Indicates that the given setup function did not complete successfully, and that both the test AND teardown functions should be skipped. Should only be returned by setup callbacks.

##### *wr_RETTDOK* {#api-wr_RETTDOK}
Indicates that the given teardown function completed successfully. Should only be returned by teardown callbacks.

##### *wr_RETTDNOK* {#api-wr_RETTDNOK}
Indicates that the given teardown function did not complete successfully. Should only be returned by teardown callbacks.

---

### enum *wr_Directive* {#api-wr_Directive}

This enum contains all of the values used to indicate which (if any) directives should be applied to the output of a given test.

#### ENUMERATORS

##### *wr_DIRNONE* {#api-wr_DIRNONE}
No directives will be applied to the output of the given test.

##### *wr_DIRTODO* {#api-wr_DIRTODO}
The TODO directive will be applied to the output of the given test.

##### *wr_DIRSKIP* {#api-wr_DIRSKIP}
The SKIP directive will be applied to the output of the given test.

---

### enum *wr_ErrorCode* {#api-wr_ErrorCode}

This enum contains all values which may be returned by a function in the wrench API. These values indicate either the succes of the function returning them, or what type of error occurred during the function’s execution.

#### ENUMERATORS

##### *wr_ERROK* {#api-wr_ERROK}
The function complted execution successfully. No error occurred.

##### *wr_ERRMEM* {#api-wr_ERRMEM}
An error occurred while attempting to allocate or reallocate heap memory.

##### *wr_ERRIO* {#api-wr_ERRIO}
An error occurred attempting to access a local file.

##### *wr_ERREMPTY* {#api-wr_ERREMPTY}
An attempt to run an empty suite was made.

---

### enum *wr_SuiteResult* {#api-wr_SuiteResult}

This enum contains values which indicate the status of an entire test suite after its completion.

#### ENUMERATORS

##### *wr_SRESOK* {#api-wr_SRESOK}
All tests in the suite either passed, or were skipped.

##### *wr_SRESNOK* {#api-wr_SRESNOK}
At least one test failed.

##### *wr_SRESBAIL* {#api-wr_SRESBAIL}
The suite was bailed out of before it could complete.

---

## Functions {#section-functions}

> NOTE: All *wrench* functions return a [wr_ErrorCode](#api-wr_ErrorCode) which indicates any errors that may have occurred during execution of the function. All functions that would otherwise return non-void data do so by accepting the final parameter *ret*, which is a pointer to where this data will be written to.

---

### [wr_ErrorCode](#api-wr_ErrorCode) *wr_attach*([wr_TestContext](#api-wr_TestContext) instance, void \*obj) {#api-wr_attach}

Add a single attachment to a test context. This allows the user to able to pass any arbitrary data between the setup function, the test implementation, and the teardown function, allowing a continuous state to be maintained throughout the test fixture.

#### PARAMETERS

##### *instance*
The context of the test the attachment is being added to.

##### *obj*
Points to the data in which this attachment refers.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The attachment was successfully added to the given context.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate/reallocate memory for the attachment.

---

### [wr_ErrorCode](#api-wr_ErrorCode) *wr_enableplan*([wr_Suite](#api-wr_Suite) instance) {#api-wr_enableplan}

Calling this function will have the effect of causing the plan for the given suite to be written to output when it is run. Plans are always written before the first test result.

#### PARAMETERS

##### *instance*
The suite for which plan output will be enabled.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
Plan print was successfully enabled for the given suite.

---

### [wr_ErrorCode](#api-wr_ErrorCode) *wr_enableskip*([wr_TestContext](#api-wr_TestContext) instance) {#api-wr_enableskip}

Set the directive for the given test context to [wr_DIRSKIP](#api-wr_DIRSKIP).

Normally, this function would not be called directly by the user, but would be called by the [wr_SKIP](#api-wr_SKIP) macro.

#### PARAMETERS

##### *instance*
The test context for which the directive attribute will be updated.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The given test context’s directive attribute was successfully updated.

---

### [wr_ErrorCode](#api-wr_ErrorCode) *wr_enabletodo*([wr_TestContext](#api-wr_TestContext) instance) {#api-wr_enabletodo}

Set the directive attribute for the given test context to [wr_DIRTODO](#api-wr_DIRTODO).

The preferred method of changing the directive attribute of a given test context is not to call this method directly, but rather to use the [wr_TODO](#api-wr_TODO) macro instead.

#### PARAMETERS

##### *instance*
The test context for which the directive attribute will be updated.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The given test context’s directive attribute was successfully updated.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_errtostr([wr_ErrorCode](#api-wr_ErrorCode) code, char \*\*ret) {#api-wr_errtostr}

Convert an error code into a string which describes the meaning of the code.

> NOTE: The memory for the return data is allocated using *malloc* and must be freed by the user!

#### PARAMETERS

##### *code*
The error code which is being converted.

##### *ret*
Pointer to the return data.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The description of the given error code was successfully written to *ret*.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the return data.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_getattach([wr_TestContext](#api-TestContext) instance, int index, void \*\*ret) {#api-getattach}

Fetch an attachment from a given test context.

> HINT: Use [wr_getattachct()](#api-wr_getattachct) to determine the upper limit for values that may be passed to *index*.

#### PARAMETERS

##### *instance*
The test context from which the attachment is being fetched.

##### *index*
The index of the attachment being fetched.

##### *ret*
Pointer to the return data.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The attachment was successfully fetched.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_getattachct([wr_TestContext](#api-wr_TestContext) instance, int \*ret) {#api-wr_getattachct}

Fetch the number of attachments that have been added to a given test context.

#### PARAMETERS

##### *instance*
The test context from which the attachment count is being fetched.

##### *ret*
Pointer to the return data.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The attachment count was successfully fetched.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_getdesc([wr_TestContext](#api-wr_TestContext) instance, char \*\*ret) {#api-wr_getdesc}

Fetch the description from a given test context.

#### PARAMETERS

##### *instance*
The test context from which the description is being fetched.

##### *ret*
Pointer to the return data.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The description was successfully fetched.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_gettestno([wr_TestContext](#api-wr_TestContext) instance, int \*ret)

Fetch the test number from a given test context.

> NOTE: Test numbers are one-indexed, not zero-indexed. This is so that the first test that is written to output is test 'one'.

#### PARAMETERS

##### *instance*
The test context from which the test number is being fetched.

##### *ret*
Pointer to the return data.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The test number was successfully fetched.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_newsuite([wr_Test](#api-wr_Test) \*roster, int count, char \*outfile, [wr_Suite](#api-wr_Suite) \*ret) {#api-wr_newsuite}

Create a new test suite.

#### PARAMETERS

##### *roster*
Pointer to the first element in an array of [wr_Test](#api-wr_Test). This array comprises the roster of individual tests which will be run when the new suite is run.

##### *count*
The number of tests from *roster* which will be run.

##### *outfile*
The path to the file where the new suite’s output will be written to.

##### *ret*
Pointer to the return data, which is the new suite.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The new suite was successfully created and returned.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the return data.

##### [wr_ERREMPTY](#api-wr_ERREMPTY)
*count* is less than *1*.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_newtest([wr_Callback](#api-wr_Callback) callback, char \*desc, [wr_Test](#api-wr_Test) \*ret) {#api-wr_ErrorCode}

Create a new test.

#### PARAMETERS

##### *callback*
The function containing this test’s implementation.

##### *desc*
A description of the test. This is the description that will be used for the suite’s output.

##### *ret*
Pointer to the return data, which is the new test.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The new test was successfully created and returned.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the return data.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_regsetup([wr_Suite](#api-wr_Suite) instance, [wr_Callback](*api-wr_Callback) callback) {#api-wr_regsetup}

Register a callback function to be used as the setup function for a given suite.

#### PARAMETERS

##### *instance*
The suite for which the setup function is being registered.

##### *callback*
The function which will be used as the setup function.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The setup function was successfully registered.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_regteardown([wr_Suite](#api-wr_Suite) instance, [wr_Callback](#api-wr_Callback) callback) {#api-wr_regteardown}

Register a callback function to be used as the teardown function for a given suite.

#### PARAMETERS

##### *instance*
The suite for which the teardown function is being registered.

##### *callback*
The function which will be used as the teardown function.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The teardown function was successfully registered.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_runsuite([wr_Suite](#api-wr_Suite) instance, [wr_SuiteResult](#api-wr_SuiteResult) \*ret) {#api-wr_runsuite}

Run a test suite.

#### PARAMETERS

##### *instance*
The suite which is to be run.

##### *ret*
Pointer to the return data, which is a [wr_SuiteResult](#api-wr_SuiteResult) that indicates the status of the suite run as of its completion.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The test was successfully run. Please keep in mind that receiving this error code does not imply any particular result from running the suite–-to determine if the suite passed or failed, you must examine the value written to *ret*.

##### [wr_ERRIO](#api-wr_ERRIO)
An error occurred while attempting to open the suite’s output file with write access.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for a test context.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_setrem([wr_TestContext](#api-wr_TestContext) instance, char \*rem) {#api-wr_setrem}

Add a remark to a given test context.

For tests with a directive, the remark will be the explainatory text which follows the directive. For tests without a directive, the remark will appear within a parenthentical directly after the test’s description.

> WARNING: This function will not *free* the test’s existing remark if it has already been assigned. Thus, it is only safe to call this function **once** per test context.

#### PARAMETERS

##### *instance*
The test in which the remark will be assigned.

##### *rem*
The string which will be assigned as the test’s remark.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The remark was successfully added.

##### [wr_ERRMEM](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the remark.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_setsuiteprediags([wr_Suite](#api-wr_Suite) instance, char \*dirs) {#api-wr_setsuiteprediags}

Assign a string to be used as prefix diagnostics for a given suite.

The prefix diagnostics are written to the output before the results of any tests are written. The given string will be split into separate diagnostics at each occurrence of the newline '\\n' character.

> WARNING: This function will not *free* the suite’s existing prefix diagnostics if they have already been assigned. Thus, it is only safe to call this function **once** per suite.

#### PARAMETERS

##### *instance*
The suite in which the prefix diagnostics will be assigned.

##### *dirs*
The string which will be assigned as the given suite’s prefix diagnostics.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The prefix diagnostics were successfully assigned.

##### [wr_ERROK](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the diagnostics.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_setsuitepostdiags([wr_Suite](#api-wr_Suite) instance, char \*dirs) {#api-wr_setsuitepostdiags}

Assign a string to be used as suffix diagnostics for a given suite.

The suffix diagnostics are written to the output after the results of any tests are written. The given string will be split into separate diagnostics at each occurrence of the newline '\\n' character.

> WARNING: This function will not *free* the suite’s existing suffix diagnostics if they have already been assigned. Thus, it is only safe to call this function **once** per suite.

#### PARAMETERS

##### *instance*
The suite in which the suffix diagnostics will be assigned.

##### *dirs*
The string which will be assigned as the given suite’s suffix diagnostics.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The suffix diagnostics were successfully assigned.

##### [wr_ERROK](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the diagnostics.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_settestprediags([wr_TestContext](#api-wr_TestContext) instance, char \*dirs) {#api-wr_settestprediags}

Assign a string to be used as prefix diagnostics for a given test context.

The prefix diagnostics are written to the output before the test results are written. The given string will be split into separate diagnostics at each occurrence of the newline '\\n' character.

> WARNING: This function will not *free* the test context’s existing prefix diagnostics if they have already been assigned. Thus, it is only safe to call this function **once** per test context.

#### PARAMETERS

##### *instance*
The test context for which the prefix diagnostics will be assigned.

##### *dirs*
The string which will be assigned as the given test context’s prefix diagnostics.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The prefix diagnostics were successfully assigned.

##### [wr_ERROK](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the diagnostics.

---

### [wr_ErrorCode](#api-wr_ErrorCode) wr_settestpostdiags([wr_TestContext](#api-wr_TestContext) instance, char \*dirs) {#api-wr_settestprediags}

Assign a string to be used as suffix diagnostics for a given test context.

The suffix diagnostics are written to the output after the test results are written. The given string will be split into separate diagnostics at each occurrence of the newline '\\n' character.

> WARNING: This function will not *free* the test context’s existing suffix diagnostics if they have already been assigned. Thus, it is only safe to call this function **once** per test context.

#### PARAMETERS

##### *instance*
The test context for which the suffix diagnostics will be assigned.

##### *dirs*
The string which will be assigned as the given test context’s suffix diagnostics.

#### RETURN VALUES

##### [wr_ERROK](#api-wr_ERROK)
The suffix diagnostics were successfully assigned.

##### [wr_ERROK](#api-wr_ERRMEM)
An error occurred while attempting to allocate memory for the diagnostics.