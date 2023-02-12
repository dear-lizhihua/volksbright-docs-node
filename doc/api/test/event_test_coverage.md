### Event: `'test:coverage'`

* `data` {Object}
  * `summary` {Object} An object containing the coverage report.
    * `files` {Array} An array of coverage reports for individual files. Each
      report is an object with the following schema:
      * `path` {string} The absolute path of the file.
      * `totalLineCount` {number} The total number of lines.
      * `totalBranchCount` {number} The total number of branches.
      * `totalFunctionCount` {number} The total number of functions.
      * `coveredLineCount` {number} The number of covered lines.
      * `coveredBranchCount` {number} The number of covered branches.
      * `coveredFunctionCount` {number} The number of covered functions.
      * `coveredLinePercent` {number} The percentage of lines covered.
      * `coveredBranchPercent` {number} The percentage of branches covered.
      * `coveredFunctionPercent` {number} The percentage of functions covered.
      * `uncoveredLineNumbers` {Array} An array of integers representing line
        numbers that are uncovered.
    * `totals` {Object} An object containing a summary of coverage for all
      files.
      * `totalLineCount` {number} The total number of lines.
      * `totalBranchCount` {number} The total number of branches.
      * `totalFunctionCount` {number} The total number of functions.
      * `coveredLineCount` {number} The number of covered lines.
      * `coveredBranchCount` {number} The number of covered branches.
      * `coveredFunctionCount` {number} The number of covered functions.
      * `coveredLinePercent` {number} The percentage of lines covered.
      * `coveredBranchPercent` {number} The percentage of branches covered.
      * `coveredFunctionPercent` {number} The percentage of functions covered.
    * `workingDirectory` {string} The working directory when code coverage
      began. This is useful for displaying relative path names in case the tests
      changed the working directory of the Node.js process.
  * `nesting` {number} The nesting level of the test.

Emitted when code coverage is enabled and all tests have completed.
