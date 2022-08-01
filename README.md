# rspamd_rules

UPDATE August 01 2022:
Our deployment of Rspamd has caused too much user confusion, and we are finally reverting it back to SpamAssassin. This repo will likely remain unaltered moving forward.

When making edits to lists (maps), please follow the current syntax used, and avoid additional regex. The current method of capturing strings for each map is being taken and converted to SpamAssassin rules for our older servers automatically. This relies on continued consistency, for now. Adding new maps, however, may be appropriate if regex or more complex strings are needed.

/lists/  
body-spam.map = Text identified in email body that is known to be spam  
subject-spam.map = Text identified in email subject that is known to be spam  
tlds.txt = TLDs with high probability of being spam  
blacklisted-sender-strings.map = Strings in "From" header that should have zero false positives  
mxcheck_exclude.inc = Whitelisted domains that do not require MX records to pass our spam filter (their business domain and sending domain likely do not match)

/local.d/  
force_actions.conf = Override actions  
multimap.conf = Definitions for maps we use (See maps: https://rspamd.com/doc/modules/multimap.html )  
mx_check.conf = Checking if sender has valid MX records  
neural.conf = Enabling rspamd neural learning  
redis.conf = Defining location of redis server

/override.d/  
actions.conf = Default actions  
metrics.conf = Defining or overriding scores. If we make our own rules we define their scores here. If we find a rule needs to have it's score increased or decreased, we re-define it here.

These rspamd rules have no license because we do not consider it to in any way be intellectual property. Everything in this project is publicly available to anyone, it is merely lists of domains and phrases, none of which we can claim any ownership of.
