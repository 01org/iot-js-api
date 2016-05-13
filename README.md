# OCF Test Suite
This suite provides tests for the [OCF JS API][].

## Usage:

```JS
// Load the test suite
var ocfTestSuite = require( "ocf-test-suite" );

// At your option you may modify the set of default logging callbacks before you run the suite.
ocfTestSuite.defaultCallbacks.log = ( function( originalLog ) {
	return function() {

		// Do something and then chain up to the original log() function
		console.log( "The test suite has just made an assertion" );
		return originalLog.apply( this, arguments );
	}
} )( ocfTestSuite.defaultCallbacks.log );

// Run the test suite
ocfTestSuite( options );
```

where ```options``` is a hash wherein the following properties are recognized:
<dl>

<dt><code>location</code></dt>
<dd>A string which will be passed to <code>require()</code> in order to load the OCF device. If this option is present, the options <code>clientLocation</code> and 
<code>serverLocation</code> will be ignored. On the other hand, if this option is absent, both <code>clientLocation</code> and <code>serverLocation</code> must be present.</dd>

<dt><code>clientLocation</code></dt>
<dd>A string which will be passed to <code>require()</code> in order to load the OCF device that will serve as the client.</dd>

<dt><code>serverLocation</code></dt>
<dd>A string which will be passed to <code>require()</code> in order to load the OCF device that will serve as the server.</dd>

<dt><code>callbacks</code></dt>
<dd>An optional hash containing callbacks to call upon test events. The names and semantics of the callbacks are the same as http://api.qunitjs.com/category/callbacks/. The callbacks will be called in the context of the <code>QUnit</code> object. Information will be nicely formatted and printed to standard ouput by default.</dd>

<dt><code>tests</code></dt>
<dd>An optional array containing the list of tests to run. By default all tests will be run.</dd>

<dt><code>environment</code></dt>
<dd>A hash containing environment key value pairs, similar to [process.env][].</dd>

</dl>


[OCF JS API]: https://github.com/solettaproject/soletta/blob/v1_beta19/doc/js-spec/oic.md
[process.env]: https://nodejs.org/api/process.html#process_process_env