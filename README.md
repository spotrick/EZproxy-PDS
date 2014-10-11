NAME
    ezpticket

DESCRIPTION
    ezpticket is a cgi authentication script used to authenticate access to
    EZproxy, using the CGI Script Authentication method. This is described
    in detail at
    http://oclc.org/support/services/ezproxy/documentation/usr/cgi.en.html

    Briefly, EZproxy will call this script to authenticate the user. The
    script will check with PDS to see if the user has already authenticated.
    If not, PDS will present a form for the user to input username and
    password. PDS will return a pds_handle, which this script uses to call
    PDS back to retrieve user details. The user details are then used to
    determine a Group or Groups for EZproxy to permit access to particular
    resources.

    Once authenticated, the user details are retrieved from Alma, and the
    statistical category used to determine a Group or Groups for EZproxy. A
    mapping from statistical category to Group is included in the separate
    configuration file.

USAGE
    This script needs to be installed as a cgi script on a web server.

    To link EZproxy to this script, you need to make an entry in ezproxy.usr
    that looks like:

        ::CGI=https://library.youruni.edu.au/cgi-bin/ezpticket?url=^R

        ::Ticket
        AcceptGroups STAFF+STUDENT
        TimeValid 10
        MD5 ********
        Expired; Deny reject.html
        /Ticket

    You must list the Groups that EZproxy will accept authentication for,
    and the MD5 password must match the one given in the configuration
    (below).

CONFIGURATION
    Configuration requires two values:

    ezhost : the host URL of our service

    secret : the code used to generate the MD5 portion of the ticket (should
    match the code defined in EZproxy user.txt)

AUTHOR
    Steve Thomas <stephen.thomas@adelaide.edu.au>

VERSION
    This is version 2014.09.25

LICENCE
    Copyright 2014 Steve Thomas

    Permission is hereby granted, free of charge, to any person obtaining a
    copy of this software and associated documentation files (the
    "Software"), to deal in the Software without restriction, including
    without limitation the rights to use, copy, modify, merge, publish,
    distribute, sublicense, and/or sell copies of the Software, and to
    permit persons to whom the Software is furnished to do so, subject to
    the following conditions:

    The above copyright notice and this permission notice shall be included
    in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
    OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
    MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
    IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
    CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
    TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
    SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
