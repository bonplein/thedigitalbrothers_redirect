# thedigitalbrothers redirect

A small app used to redirect thedigitalbrothers.ch to hofratsuess.ch

## Preparing the urls

```bash
# Getting all the links that exist between the 2 websites
wget -r --spider --domains=hofratsuess.ch,thedigitalbrothers.ch http://hofratsuess.ch/ -nv -o links.txt -H

# Isolating thedigitalbrothers urls
cat links.txt | grep "thedigitalbrothers" > links_thedigitalbrothers.txt

# Extract the urls from the logs files
cat links_thedigitalbrothers.txt | awk '{gsub("URL\:",""); print}' | awk '{print $3}' | grep -v '^$' > urls_thedigitalbrothers.txt
```
