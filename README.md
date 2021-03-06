# Ruby Advisory Database

The Ruby Advisory Database aims to compile all advisories that are relevant to Ruby libraries.

## Goals

1. Provide advisory **metadata** in a **simple** yet **structured** [YAML]
   schema for automated tools to consume.
2. Avoid reinventing [CVE]s.
3. Avoid duplicating the efforts of the [OSVDB].

## Directory Structure

The database is a list of directories that match the names of Ruby libraries on
[rubygems.org]. Within each directory are one or more advisory files
for the Ruby library. These advisory files are typically named using
the advisories [CVE] identifier number.

    gems/:
      rails/:
        2012-1098.yml  2012-2660.yml  2012-2661.yml  2012-3463.yml

If an advisory does not yet have a [CVE], [requesting a CVE][1] is easy.

## Format

Each advisory file contains the advisory information in [YAML] format:

    ---
    gem: actionpack
    framework: rails
    cve: 2013-0156
    url: http://osvdb.org/show/osvdb/89026
    title: |
      Ruby on Rails params_parser.rb Action Pack Type Casting Parameter Parsing
      Remote Code Execution 
    
    description: |
      Ruby on Rails contains a flaw in params_parser.rb of the Action Pack.
      The issue is triggered when a type casting error occurs during the parsing
      of parameters. This may allow a remote attacker to potentially execute
      arbitrary code.
    
    cvss_v2: 10.0
    
    patched_versions:
      - ~> 2.3.15
      - ~> 3.0.19
      - ~> 3.1.10
      - ">= 3.2.11"

### Schema

* `gem` \[String\]: Name of the affected gem.
* `framework` \[String\] (optional): Name of framework gem belongs to.
* `cve` \[String\]: CVE id
* `url` \[String\]: The URL to the full advisory.
* `title` \[String\]: The title of the advisory.
* `description` \[String\]: Multi-paragraph description of the vulnerability.
* `cvss_v2` \[Float\]: The [CVSSv2] score for the vulnerability.
* `unaffected_versions` \[Array\<String\>\] (optional): The version requirements for the
  unaffected versions of the Ruby library.
* `patched_versions` \[Array\<String\>\]: The version requirements for the
  patched versions of the Ruby library.

## Credits

Please see [CONTRIBUTORS.md].

This database also includes data from the [Open Source Vulnerability Database][OSVDB]
developed by the Open Security Foundation (OSF) and its contributors.

[rubygems.org]: https://rubygems.org/
[CVE]: http://cve.mitre.org/
[CVSSv2]: http://www.first.org/cvss/cvss-guide.html
[OSVDB]: http://www.osvdb.org/
[YAML]: http://www.yaml.org/
[CONTRIBUTORS.md]: https://github.com/rubysec/ruby-advisory-db/blob/master/CONTRIBUTORS.md

[1]: http://people.redhat.com/kseifrie/CVE-OpenSource-Request-HOWTO.html
