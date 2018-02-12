
Reads rules written in a Snort like syntax (as of Snort 2.9.11) from a rule file, puts parsed rule content in a struct and (optionally) prints the rule. 
It than (optionally) constructs HTTP requests that are sent to the configured host (possibly a webserver) that trigger events related to the parsed rules.
"Snort like" means it accepts Snort rules, but does not require all fields of a Snort rule.

For the moment it only converts hex characters in content patterns that are part of the first 128 readable ASCII characters.
It only parses rules that use one of the following content modifiers: http\_\[method,uri,raw\_uri,stat\_msg,stat\_code,header,raw\header,client\_body,cookie,raw_cookie] or the equivalent modifiers for PCRE content.                                 
It ignores rules that are not triggering an alert or do not contain the 'content' or the 'pcre' or the 'uricontent' keyword.

libcurl is needed for compilation.
Build it by executing "g++ -std=c++11 -lcurl snortRuleParser.cpp"

Run it by executing "./a.out -f \<snortRuleFile\> -s \<webserver\>"
  
For more options run "./a.out -h"
