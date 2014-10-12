# Jasmine JS-Reporter

(Modified with gross hack to work with jasmine 2.0.0 - please use detro/jasmine-jsreporter instead)

This is a Jasmine Reporter, designed to simplify the extraction of test results from the Page.
It's tailored with _Test Reporting Automation_ in mind.

Ideal scenario of use are:

* Use Selenium Web Driver to extract the result out of the page
* Use PhantomJS to do... well, the same as above
* Every time you wish Jasmine produced a JSON to report about the tests

## What does it do?

The Reporter awaits for all the Test to finish, than produces a report that can be retrieved with

```javascript
var JSONReport = jasmine.getJSReport ();
// or
var strJSONReport = jasmine.getJSReportAsString ();
```
and looks like the following:

```JSON
{
    "suites": [
        {
            "description": "Simple test that checks the obvious regarding Truthy-ness and Falsy-ness",
            "durationSec": 0.005,
            "specs": [
                {
                    "description": "should report that a number is truthy, if different than '0', falsy otherwise",
                    "durationSec": 0.004,
                    "passed": true,
                    "skipped": false,
                    "passedCount": 3,
                    "failedCount": 0,
                    "totalCount": 3
                },
                // ... more specs here...
            ],
            "suites": [],
            "passed": true
        }
    ],
    "durationSec": 0.005,
    "passed": true
}
```

After that, you can just extract it from the page.

## How do I download it and check it works

1. Download the code:
    * `git clone http://github.com/detro/jasmine-jsreporter.git`
2. Include the reporter in your page running Jasmine tests with something like:
    * `<script src="path/to/jasmine-jsreporter.js" type="text/javascript"></script>`
3. Open your [WebInspector](http://trac.webkit.org/wiki/WebInspector), [Firebug](http://getfirebug.com/) or whatever you use
4. On the console, type:
    * `jasmine.getJSReport ()`
5. Check that you get an Object back (should look like the above one)
6. You are done!

Now you can setup your Test Infrastructure to _extract test results from the test page_, in the same way I just showed you.

## Examples

I have provided some usage examples:

* `examples/`
    * `phantomjs-javascript/`: Example use with PhantomJS [WORK IN PROGRESS]
    * `selenium-java/`: Example use with Selenium in Java [WORK IN PROGRESS]
    * `spec-runner/`: Example HTML page that uses Jasmine and JS-Reporter - open the WebInspector/Firebug

## License

This code is release under BSD License.

```ascii
Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

  * Redistributions of source code must retain the above copyright
    notice, this list of conditions and the following disclaimer.
  * Redistributions in binary form must reproduce the above copyright
    notice, this list of conditions and the following disclaimer in the
    documentation and/or other materials provided with the distribution.
  * Neither the name of the <organization> nor the
    names of its contributors may be used to endorse or promote products
    derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF
THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

_Would be nice if you mention the **Author** and/or it's **Public Repository** when using it._
