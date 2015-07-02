# pytest-optimal-ordering
Execute pytest test suites in an optimal order.

## Idea
When executing a test suite in parallel using pytest-xdist, you can often run into a situation where slow integration tests are put at the back of the test queue and hold up the completion of the test suite run. Ideally you want your tests ordered slowest to fastest, so the faster tests can fill in the gaps around the slower ones.

Using this plugin, on the first run of the test suite, the standard ordering will be used, The timing of each test will then be taken and written to a file (`.pytest_timing`?). On subsequent test runs, this file will be read, and the timing info will be used to order the tests, slowest to fastest.

## References
- pytest --durations (for timing) https://github.com/pytest-dev/pytest/blob/master/_pytest/runner.py#L27
- pytest-ordering (to sort tests) https://github.com/ftobia/pytest-ordering
