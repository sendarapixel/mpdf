mPDF is a PHP library which generates PDF files from UTF-8 encoded HTML.

It is based on FPDF and HTML2FPDF (see CREDITS), with a number of enhancements. mPDF was written by Ian Back and is released under the GNU GPL v2 licence.

Latest Stable Version Total Downloads License

⚠ If you are viewing this file on mPDF GitHub repository homepage or on Packagist, please note that the default repository branch is development which can differ from the last stable release.

Requirements
PHP versions and extensions
mPDF >=7.0 is supported on PHP ^5.6 || ~7.0.0 || ~7.1.0 || ~7.2.0
PHP 7.3 is supported since mPDF v7.1.7
PHP 7.4 is supported since mPDF v8.0.4
PHP 8.0 is supported since mPDF v8.0.10
PHP 8.1 is supported as of mPDF v8.0.13
PHP mbstring and gd extensions have to be loaded.

Additional extensions may be required for some advanced features such as zlib for compression of output and embedded resources such as fonts, bcmath for generating barcodes or xml for character set conversion and SVG handling.

Known server caveats
mPDF has some problems with fetching external HTTP resources with single threaded servers such as php -S. A proper server such as nginx (php-fpm) or Apache is recommended.

Support us
Consider supporting development of mPDF with a donation of any value. Donation button can be found on the main page of the documentation.

Installation
Official installation method is via composer and its packagist package mpdf/mpdf.

$ composer require mpdf/mpdf
Usage
The simplest usage (since version 7.0) of the library would be as follows:

<?php

require_once __DIR__ . '/vendor/autoload.php';

$mpdf = new \Mpdf\Mpdf();
$mpdf->WriteHTML('<h1>Hello world!</h1>');
$mpdf->Output();
This will output the PDF inline to the browser as application/pdf Content-type.

Setup & Configuration
All configuration directives can be set by the $config parameter of the constructor.

It is recommended to set one's own temporary directory via tempDir configuration variable. The directory must have write permissions (mode 775 is recommended) for users using mPDF (typically cli, webserver, fpm).

Warning: mPDF will clean up old temporary files in the temporary directory. Choose a path dedicated to mPDF only.

<?php

$mpdf = new \Mpdf\Mpdf(['tempDir' => __DIR__ . '/tmp']);
By default, the temporary directory will be inside vendor directory and will have write permissions from post_install composer script.

For more information about custom temporary directory see the note on Folder for temporary files in the section on Installation & Setup in the manual.

If you have problems, please read the section on troubleshooting in the manual.

About CSS support and development state
mPDF as a whole is a quite dated software. Nowadays, better alternatives are available, albeit not written in PHP.

Use mPDF if you cannot use non-PHP approach to generate PDF files or if you want to leverage some of the benefits of mPDF over browser approach – color handling, pre-print, barcodes support, headers and footers, page numbering, TOCs, etc. But beware that a HTML/CSS template tailored for mPDF might be necessary.

If you are looking for state of the art CSS support, mirroring existing HTML pages to PDF, use headless Chrome.

mPDF will still be updated to enhance some internal capabilities and to support newer versions of PHP, but better and/or newer CSS support will most likely not be implemented.

Online manual
Online manual is available at https://mpdf.github.io/.

General troubleshooting
For general questions or troubleshooting please use Discussions.

You can also use the mpdf tag at Stack Overflow as the StackOverflow user base is more likely to answer you in a timely manner.

Contributing
Before submitting issues and pull requests please read the CONTRIBUTING.md file.

Unit Testing
Unit testing for mPDF is done using PHPUnit.

To get started, run composer install from the command line while in the mPDF root directory (you'll need composer installed first).

To execute tests, run composer test from the command line while in the mPDF root directory.

Any assistance writing unit tests for mPDF is greatly appreciated. If you'd like to help, please note that any PHP file located in the /tests/ directory will be autoloaded when unit testing.
