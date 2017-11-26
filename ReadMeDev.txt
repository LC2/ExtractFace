ExtractFace
Description		: Dump Facebook stuff for analysis or reporting purposes.
Author				: Alain Rioux (admin@le-tools.com)
WebSite				: http://le-tools.com/ExtractFace.html
Documentation	: http://le-tools.com/ExtractFaceDoc.html
SourceForge		: https://sourceforge.net/p/extractface
GitHub				: https://github.com/arioux/ExtractFace


Development
-----------

ExtractFace has been developped using ActivePerl 5.16.3 with the following modules installed:

- Encode (v2.56)
- Excel-Writer-XLSX (v0.83)
- File-Copy-Recursive (v0.38)
- File-Path (v2.09)
- HTML-Parser (v3.71)
- Image-Info (v1.36)
- LWP (v6.05)
- Module-Pluggable-Fast (v0.19)
- MozRepl (v0.06)
- MozRepl-RemoteObject (v0.39)
- threads (v1.96)
- threads-shared (v1.46)
- DBI (v1.631)
- Time-HiRes (v1.9726)
- DateTime (v1.28)
- DateTime-Format-Strptime (v1.68)
- DateTime-TimeZone (v2.00)
- URI-Escape-JavaScript (v0.04)
- Win32-API (v0.75)
- Win32-GUI (v1.08)
- Win32-Process (v0.16)
- WWW-Mechanize-Firefox (v0.78)


To do
-----

- More Dump functions!


Packaging
---------

Executable has been packaged using PerlApp v.9.2.1 (ActiveState). For alternative to PerlApp, see 
http://www.nicholassolutions.com/tutorials/perl-PAR.htm.

Before packaging this tool, you can modify WWW::Mechanize::Firefox (around line 1630):

sub uri {
    my ($self) = @_;
    my $loc = $self->tab->MozRepl::RemoteObject::Methods::dive(qw[
        linkedBrowser
        currentURI
        asciiSpec ]);
    $loc = '' if $loc =~ /^about:/; # New tab in Firefox, prevent crashing   <-- Add this line
    return URI->new( $loc );
};

Some additional modules may be required or manually added before packaging.
