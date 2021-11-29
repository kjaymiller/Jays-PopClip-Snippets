# Searchlink Actions #

Copy, Paste, or open the Searchlink url

```yaml
# popclip SearchLink + Multi Actions
name: SearchLink
actions:
- title: SearchLink Copy
  requirements: [text]
  icon: search c
  applescript: do shell script "automator -r -i \"{popclip text}\" ~/Library/Services/SearchLink.workflow|awk '/http/{gsub(/^[ \t]*\"|\"[ \t]*$/,\"\"); print}'|pbcopy"
- title: SearchLink Paste
  requirements: [text, paste]
  icon: search p
  applescript: do shell script "automator -r -i \"{popclip text}\" ~/Library/Services/SearchLink.workflow|awk '/http/{gsub(/^[ \t]*\"|\"[ \t]*$/,\"\"); print}'|pbcopy"
  after: paste
- title: Searchlink Open
  requirements: [text]
  icon: search o
  applescript: do shell script "open $(automator -r -i \"{popclip text}\" ~/Library/Services/SearchLink.workflow | grep -o 'https[^ ]*')"
```