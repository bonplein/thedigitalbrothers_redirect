# thedigitalbrothers redirect

A small app used to redirect thedigitalbrothers.ch to hofratsuess.ch

## Preparing the urls

Below is a recipe to extract all urls with the site to be redirected. It's being used after the redirection is in place to check that all links point to their respective new targets.

```bash
# Getting all the links that exist between the 2 websites
wget -r --spider --domains=hofratsuess.ch,thedigitalbrothers.ch http://hofratsuess.ch/ -nv -o links.txt -H

# Isolating thedigitalbrothers urls
cat links.txt | grep "thedigitalbrothers" > links_thedigitalbrothers.txt

# Extract the urls from the log file
cat links_thedigitalbrothers.txt | awk '{gsub("URL\:",""); print}' | awk '{print $3}' | grep -v '^$' | grep 'http://' > urls_thedigitalbrothers.txt
```
