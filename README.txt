The webwork_opaque question type and behaviour
https://moodle.org/plugins/qtype_webwork_opaque

webwork_opaque (http://docs.moodle.org/en/Development:webwork_opaque) is the Open protocol for
accessing question engines.

The webwork_opaque protocol was originally created by sam marshall of the Open
University (http://www.open.ac.uk/) as part of the OpenMark project
(http://java.net/projects/openmark/). The Moodle implementation of webwork_opaque was
done by Tim Hunt.

As well as OpenMark, this question type can also be used to connect to
ounit (http://code.google.com/p/ounit/) and possibly other question systems
we don't know about.

webwork_opaque has been available since Moodle 1.8, but this version is compatible with
Moodle 3.4.

This question behaviour also requires the webwork_opaque question type to be installed.
https://moodle.org/plugins/qbehaviour_webwork_opaque
webwork_opaque
You can install from the Moodle plugins database using the links above.
Or to install using git, type this command in the root of your Moodle install

    git clone git://github.com/moodleou/moodle-qtype_webwork_opaque.git question/type/webwork_opaque
    echo '/question/type/webwork_opaque/' >> .git/info/exclude
    git clone git://github.com/moodleou/moodle-qbehaviour_webwork_opaque.git question/behaviour/webwork_opaque
    echo '/question/behaviour/webwork_opaque/' >> .git/info/exclude

Once installed you need to go to the question type settings page
(Site administration -> Plugins -> Question types -> webwork_opaque) to
set up the URLs of the question engines you wish to use.

https://github.com/moodleou/moodle-local_testopaqueqe can be used to test that
webwork_opaque is working.

To be able to run all the unit tests, you need a working OpenMark install, then you need to add
    define('QTYPE_WEBWORK_OPAQUE_TEST_ENGINE_QE',      'http://example.com/om-qe/services/Om');
    define('QTYPE_WEBWORK_OPAQUE_TEST_ENGINE_TN',      'http://example.com/openmark/!question');
    define('QTYPE_WEBWORK_OPAQUE_TEST_ENGINE_PASSKEY', 'abc123');
    define('QTYPE_WEBWORK_OPAQUE_TEST_ENGINE_TIMEOUT', '5');
to your config.php file. Of these, only the first is required. The remaining
ones are optional. Specify them if your set-up needs them.

To view Hint and Solution in WeBWorK webwork_opaque problem add to questiontype.php at line 87

            $PAGE->requires->js_call_amd('qtype_webwork_opaque/knowl'); 
            $PAGE->requires->js_call_amd('qtype_webwork_opaque/Base64');
            $PAGE->requires->js_call_amd('qtype_webwork_opaque/underscore');
