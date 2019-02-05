folders are "testsuites"
files are "testsuites" too!
sections within files are "testcases", a.k.a "tests"
checks within text case are "testactions"

--randomize
  * All (everything)
  * suites (just the suites, but not their innards)
  * tests (just the testcases, but not the suites)
  * none (disable all configured randomization)

pybot --randomize suites mytestsuites

convention: use underscores in all filenames
convention: put a # followed by two underscores in front of filenames to determine the order of the tests
