
<!-- rnb-text-begin -->

---
title: "Initial data analysis with nflverse packages"
output: html_notebook
---



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeSh0aWR5dmVyc2UpXG5gYGAifQ== -->

```r
library(tidyverse)
```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoi4pSA4pSAIEF0dGFjaGluZyBjb3JlIHRpZHl2ZXJzZSBwYWNrYWdlcyDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIAgdGlkeXZlcnNlIDIuMC4wIOKUgOKUgFxu4pyUIGRwbHlyICAgICAxLjEuNCAgICAg4pyUIHJlYWRyICAgICAyLjEuNVxu4pyUIGZvcmNhdHMgICAxLjAuMCAgICAg4pyUIHN0cmluZ3IgICAxLjUuMVxu4pyUIGdncGxvdDIgICAzLjUuMSAgICAg4pyUIHRpYmJsZSAgICAzLjIuMVxu4pyUIGx1YnJpZGF0ZSAxLjkuMyAgICAg4pyUIHRpZHlyICAgICAxLjMuMVxu4pyUIHB1cnJyICAgICAxLjAuMiAgICAg4pSA4pSAIENvbmZsaWN0cyDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIAgdGlkeXZlcnNlX2NvbmZsaWN0cygpIOKUgOKUgFxu4pyWIGRwbHlyOjpmaWx0ZXIoKSBtYXNrcyBzdGF0czo6ZmlsdGVyKClcbuKcliBkcGx5cjo6bGFnKCkgICAgbWFza3Mgc3RhdHM6OmxhZygpXG7ihLkgVXNlIHRoZSBcdTAwMWJdODs7aHR0cDovL2NvbmZsaWN0ZWQuci1saWIub3JnL1x1MDAwN2NvbmZsaWN0ZWQgcGFja2FnZVx1MDAxYl04OztcdTAwMDcgdG8gZm9yY2UgYWxsIGNvbmZsaWN0cyB0byBiZWNvbWUgZXJyb3JzXG4ifQ== -->

```
── Attaching core tidyverse packages ────────────────────────────────────────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.3     ✔ tidyr     1.3.1
✔ purrr     1.0.2     ── Conflicts ──────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the ]8;;http://conflicted.r-lib.org/conflicted package]8;; to force all conflicts to become errors
```



<!-- rnb-output-end -->

<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeShuZmx2ZXJzZSlcbmBgYCJ9 -->

```r
library(nflverse)
```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiUmVnaXN0ZXJlZCBTMyBtZXRob2Qgb3ZlcndyaXR0ZW4gYnkgJ2RhdGEudGFibGUnOlxuICBtZXRob2QgICAgICAgICAgIGZyb21cbiAgcHJpbnQuZGF0YS50YWJsZSAgICAgXG7ilIDilIAgQXR0YWNoaW5nIHBhY2thZ2VzIOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgCBuZmx2ZXJzZSAxLjAuMyDilIDilIBcbuKclCBuZmxmYXN0UiA0LjYuMSAgICAg4pyUIG5mbHJlYWRyIDEuNC4xXG7inJQgbmZsc2VlZFIgMS4yLjAgICAgIOKclCBuZmxwbG90UiAxLjQuMFxu4pyUIG5mbDR0aCAgIDEuMC40ICAgICBcbldhcm5pbmc6IHBhY2thZ2Ug4oCYbmZscGxvdFLigJkgd2FzIGJ1aWx0IHVuZGVyIFIgdmVyc2lvbiA0LjQuMeKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgCBSZWFkeSB0byBnbyEg4pSA4pSAXG4ifQ== -->

```
Registered S3 method overwritten by 'data.table':
  method           from
  print.data.table     
── Attaching packages ────────────────────────────────────────────────────────────────────────── nflverse 1.0.3 ──
✔ nflfastR 4.6.1     ✔ nflreadr 1.4.1
✔ nflseedR 1.2.0     ✔ nflplotR 1.4.0
✔ nfl4th   1.0.4     
Warning: package ‘nflplotR’ was built under R version 4.4.1────────────────────────────────────────────────────────────────────────────────────────────────── Ready to go! ──
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheWVyX3N0YXRzIDwtIG5mbHJlYWRyOjpsb2FkX3BsYXllcl9zdGF0cyhzZWFzb25zID0gbW9zdF9yZWNlbnRfc2Vhc29uKCkpXG5cbmBgYCJ9 -->

```r
player_stats <- nflreadr::load_player_stats(seasons = most_recent_season())

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiTm90ZTogbmZscmVhZHIgY2FjaGVzIChpLmUuLCBzdG9yZXMgYSBzYXZlZCB2ZXJzaW9uKSBkYXRhIGJ5IGRlZmF1bHQuXG5JZiB5b3UgZXhwZWN0IGRpZmZlcmVudCBvdXRwdXQgdHJ5IG9uZSBvZiB0aGUgZm9sbG93aW5nOlxu4oS5IFJlc3RhcnQgeW91ciBSIFNlc3Npb24gb3JcbuKEuSBSdW4gYG5mbHJlYWRyOjouY2xlYXJfY2FjaGUoKWAuXG5UbyBkaXNhYmxlIHRoaXMgd2FybmluZywgcnVuIGBvcHRpb25zKG5mbHJlYWRyLnZlcmJvc2UgPSBGQUxTRSlgIG9yIGFkZCBpdCB0byB5b3VyIC5ScHJvZmlsZVxuIn0= -->

```
Note: nflreadr caches (i.e., stores a saved version) data by default.
If you expect different output try one of the following:
ℹ Restart your R Session or
ℹ Run `nflreadr::.clear_cache()`.
To disable this warning, run `options(nflreadr.verbose = FALSE)` or add it to your .Rprofile
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`nflreadr::load_player_stats()`. Arguments include:

* `seasons=`: numeric vector, or use the `most_recent_season()` function
* `stat_type=`: takes "offense", "defense", or "kicking"
*  `file_type=`: takes "rds" (default), "qs", "csv", or "parquet"


From the book:

> As an example, let’s say you need to get Patrick Mahomes’ total passing yard and attempts from the 2022 season. You could do so via load_pbp() but, if you do not need further context (such as down, distance, quarter, etc.), using load_player_stats() is much more efficient.

Below, I'm taking the weekly, box-score level receiving stats, and summarizing them for the pass catchers for the Steelers.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheWVyX3N0YXRzICU+JSBuYW1lcygpXG5cbmBgYCJ9 -->

```r
player_stats %>% names()

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiIFsxXSBcInBsYXllcl9pZFwiICAgICAgICAgICAgICAgICAgIFwicGxheWVyX25hbWVcIiAgICAgICAgICAgICAgICAgXCJwbGF5ZXJfZGlzcGxheV9uYW1lXCIgICAgICAgIFxuIFs0XSBcInBvc2l0aW9uXCIgICAgICAgICAgICAgICAgICAgIFwicG9zaXRpb25fZ3JvdXBcIiAgICAgICAgICAgICAgXCJoZWFkc2hvdF91cmxcIiAgICAgICAgICAgICAgIFxuIFs3XSBcInJlY2VudF90ZWFtXCIgICAgICAgICAgICAgICAgIFwic2Vhc29uXCIgICAgICAgICAgICAgICAgICAgICAgXCJ3ZWVrXCIgICAgICAgICAgICAgICAgICAgICAgIFxuWzEwXSBcInNlYXNvbl90eXBlXCIgICAgICAgICAgICAgICAgIFwib3Bwb25lbnRfdGVhbVwiICAgICAgICAgICAgICAgXCJjb21wbGV0aW9uc1wiICAgICAgICAgICAgICAgIFxuWzEzXSBcImF0dGVtcHRzXCIgICAgICAgICAgICAgICAgICAgIFwicGFzc2luZ195YXJkc1wiICAgICAgICAgICAgICAgXCJwYXNzaW5nX3Rkc1wiICAgICAgICAgICAgICAgIFxuWzE2XSBcImludGVyY2VwdGlvbnNcIiAgICAgICAgICAgICAgIFwic2Fja3NcIiAgICAgICAgICAgICAgICAgICAgICAgXCJzYWNrX3lhcmRzXCIgICAgICAgICAgICAgICAgIFxuWzE5XSBcInNhY2tfZnVtYmxlc1wiICAgICAgICAgICAgICAgIFwic2Fja19mdW1ibGVzX2xvc3RcIiAgICAgICAgICAgXCJwYXNzaW5nX2Fpcl95YXJkc1wiICAgICAgICAgIFxuWzIyXSBcInBhc3NpbmdfeWFyZHNfYWZ0ZXJfY2F0Y2hcIiAgIFwicGFzc2luZ19maXJzdF9kb3duc1wiICAgICAgICAgXCJwYXNzaW5nX2VwYVwiICAgICAgICAgICAgICAgIFxuWzI1XSBcInBhc3NpbmdfMnB0X2NvbnZlcnNpb25zXCIgICAgIFwicGFjclwiICAgICAgICAgICAgICAgICAgICAgICAgXCJkYWtvdGFcIiAgICAgICAgICAgICAgICAgICAgIFxuWzI4XSBcImNhcnJpZXNcIiAgICAgICAgICAgICAgICAgICAgIFwicnVzaGluZ195YXJkc1wiICAgICAgICAgICAgICAgXCJydXNoaW5nX3Rkc1wiICAgICAgICAgICAgICAgIFxuWzMxXSBcInJ1c2hpbmdfZnVtYmxlc1wiICAgICAgICAgICAgIFwicnVzaGluZ19mdW1ibGVzX2xvc3RcIiAgICAgICAgXCJydXNoaW5nX2ZpcnN0X2Rvd25zXCIgICAgICAgIFxuWzM0XSBcInJ1c2hpbmdfZXBhXCIgICAgICAgICAgICAgICAgIFwicnVzaGluZ18ycHRfY29udmVyc2lvbnNcIiAgICAgXCJyZWNlcHRpb25zXCIgICAgICAgICAgICAgICAgIFxuWzM3XSBcInRhcmdldHNcIiAgICAgICAgICAgICAgICAgICAgIFwicmVjZWl2aW5nX3lhcmRzXCIgICAgICAgICAgICAgXCJyZWNlaXZpbmdfdGRzXCIgICAgICAgICAgICAgIFxuWzQwXSBcInJlY2VpdmluZ19mdW1ibGVzXCIgICAgICAgICAgIFwicmVjZWl2aW5nX2Z1bWJsZXNfbG9zdFwiICAgICAgXCJyZWNlaXZpbmdfYWlyX3lhcmRzXCIgICAgICAgIFxuWzQzXSBcInJlY2VpdmluZ195YXJkc19hZnRlcl9jYXRjaFwiIFwicmVjZWl2aW5nX2ZpcnN0X2Rvd25zXCIgICAgICAgXCJyZWNlaXZpbmdfZXBhXCIgICAgICAgICAgICAgIFxuWzQ2XSBcInJlY2VpdmluZ18ycHRfY29udmVyc2lvbnNcIiAgIFwicmFjclwiICAgICAgICAgICAgICAgICAgICAgICAgXCJ0YXJnZXRfc2hhcmVcIiAgICAgICAgICAgICAgIFxuWzQ5XSBcImFpcl95YXJkc19zaGFyZVwiICAgICAgICAgICAgIFwid29wclwiICAgICAgICAgICAgICAgICAgICAgICAgXCJzcGVjaWFsX3RlYW1zX3Rkc1wiICAgICAgICAgIFxuWzUyXSBcImZhbnRhc3lfcG9pbnRzXCIgICAgICAgICAgICAgIFwiZmFudGFzeV9wb2ludHNfcHByXCIgICAgICAgICBcbiJ9 -->

```
 [1] "player_id"                   "player_name"                 "player_display_name"        
 [4] "position"                    "position_group"              "headshot_url"               
 [7] "recent_team"                 "season"                      "week"                       
[10] "season_type"                 "opponent_team"               "completions"                
[13] "attempts"                    "passing_yards"               "passing_tds"                
[16] "interceptions"               "sacks"                       "sack_yards"                 
[19] "sack_fumbles"                "sack_fumbles_lost"           "passing_air_yards"          
[22] "passing_yards_after_catch"   "passing_first_downs"         "passing_epa"                
[25] "passing_2pt_conversions"     "pacr"                        "dakota"                     
[28] "carries"                     "rushing_yards"               "rushing_tds"                
[31] "rushing_fumbles"             "rushing_fumbles_lost"        "rushing_first_downs"        
[34] "rushing_epa"                 "rushing_2pt_conversions"     "receptions"                 
[37] "targets"                     "receiving_yards"             "receiving_tds"              
[40] "receiving_fumbles"           "receiving_fumbles_lost"      "receiving_air_yards"        
[43] "receiving_yards_after_catch" "receiving_first_downs"       "receiving_epa"              
[46] "receiving_2pt_conversions"   "racr"                        "target_share"               
[49] "air_yards_share"             "wopr"                        "special_teams_tds"          
[52] "fantasy_points"              "fantasy_points_ppr"         
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->




<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NywibmNvbCI6MzAsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiNyDDlyAzMCJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUE4MVhYMndVUlJoZmpydTJuTFk1NklGWGFvOEZqQ2ttUGYrY0VrU2JuVklFd29QUVd0cWFrR3lHdmJsMlpXOTMyZDByRmwvNm9NOCs2NE14Z1FlTlNSTVRIekF4M0NvK1NJSUpQZ2crR1dwOElNR1ltZ2hCVWVyc3pEZmIyMkdMeHZqZ0pMdmZmSDkrMzUrWitXN254dmRQVi9QVGVVVlIxaXZaTEgzbjZGVEpIWnM0TUxSSFViSVp5cXhUc3NxR2lMNU8xYjEwVXFaUGdUNmRvT2c1U0J4dmhxaEhUZU1rc1gwaFBZb0Q5WUJIVE9JMW1zRXNTQjkrR2I5R2lIb0llNTRwTEx0SHNUVm4ydXBJMHc5TVd3Z25zYTBlSnZVNjhYeEhDRGVQT2w2TlFvbGwwWEE0Q05xVjNZZnh2RVZzZFNveXNLVWNNMVBqWWpieGtwaU43N3RmdXpwYjFkSVpyU2Z5aG9vS0cyZ2owQ3luMmg5QWZ6OC9kdk90OG5udDF5UWY0NThGM05OQUh3UDZLTkJpT28zeEE1SytKNWtIeWgwZnZQWEYyOGZsZkdMOE1OaUpQQ3BTSG1wNlBqRitMT1R5MFFWT253TTdEWEU2Q1B4Mm9EcytpTkxaRmVOUEFkNEEvREd3MHdHL0QvZ1JvQzhtNHd0R3U2SWtoc3luakNSK1djSkwvRnI0ZnhEbndmaS9qL08vam84bTMyY00yclBBYUxpRks5SHpJYWQ3UDZLbmJld24xTS9sb1l5ZkEvdzA0SGNEL2xYQVR3RC9BdUJMRWw2YzB5ckhvOTJJMHllQjN6NlZIM2JQWGtOOVlQZTRkUDcyZy93VnNKOEUvQkhnOTRwNmdJNUk4YnRBRGtMdE90QmxvTitXbzRiYkZzdUJqL0dpUDlTa0gxUkkrb245TDB2eDg2eTlkMmwzeml3ZFhDeSswZnJ3bldpOGl6TEEzMkh0UGg1MmNkcGFsUHIvaVozWDZBS2RRNlU2RzYzTDNCL2F3ZkhoSnZvK3MzUW9MQUgrSzA0VnFYLyt4ZmhQOE5xTnN5eC83VzZWamJEQTg5TitodC9kNzR1c0VPM3VJcHUwL3VUMXhQVjM4VHBSUDY4N2ZJcmpVUS9nYi9OMVFROXh2RGpmY2Z4dmJyTHpyVjNpNjY1OUR2eW53RjhBUDUvQlBuM0M0OFg0WDZoMDhOWkY3VWFrSHJ5dExRSHVPK0N2OHZnYTdJdjJ0UnNWZkNyR1h3YzdpTnQ2RCtKOXllUEU5R1BRdjVtTWo1UWx0aURhRDhQTWNVdmsrU05Rc1g0WCtmcTJ6Z2w4NGlxUXMzR0QrRXFHZldMTElPeDFMVHhQUEwxbSt0Rk1qMnhBMWVVNnZobVk4YWU2cjBHd3JYdkVJQ2I5OE0rd21SdnB4WldnNURjYkQ5SnZrUndFbUY1QUFxSGRuRVFubFVVSk9vKzltdEQxSm9IdHFrMXl4Rml6VVlwV1d5dkplck54d2lKckpKbFU5cWREZGN2eEF6RFptb3B2dHloSlRyRHBKVXA2Sk9sQlZxdHBDNlhqT3IxMDZRWU9ESEdsMjVheWFDbG1XK1dTVE04UDlKcHpPdDdVUHFtaSt3emtQU0F1VHQrRFZVVlpnanpqQnJyaDJIUDA0dGgybkFhUzhIU2pYdm5RWXNNVGlVbkhkVlVqYnlRL2k3by9pejJTdnBFcEZuSVI4VTRsckFiVzJFNHdTbmJ3QnM4NVhlRmRURy9POU1rczBOZkt5c3B2Y3FzYkZ2WWpvMEtiTUYvREFhN1V2YWpERmVXZUJPbDBvRmVWVFBSM29VTUNyL01rUWFGcFI1blVob3pacG4xeXFGcVY5T3RkZXlZS3lrUjhkTU84czIxZTVtbGtWZ0RlQWZBT1lzK1l0bGlsbklWUEVFdDRycEU1OFhlRkxnaGJqNHJybWJab29UeVYrcFhBQ2JDQTVBM0hFaEpXdW5MdkwycE05bkpFRFFBQSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["player_display_name"],"name":[1],"type":["chr"],"align":["left"]},{"label":["position"],"name":[2],"type":["chr"],"align":["left"]},{"label":["mean_receiving_receptions"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_receptions"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_targets"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_targets"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_yards"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_yards"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_tds"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_tds"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_fumbles"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_fumbles"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_fumbles_lost"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_fumbles_lost"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_air_yards"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_air_yards"],"name":[16],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_yards_after_catch"],"name":[17],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_yards_after_catch"],"name":[18],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_first_downs"],"name":[19],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_first_downs"],"name":[20],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_epa"],"name":[21],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_epa"],"name":[22],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_2pt_conversions"],"name":[23],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_2pt_conversions"],"name":[24],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_racr"],"name":[25],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_racr"],"name":[26],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_target_share"],"name":[27],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_target_share"],"name":[28],"type":["dbl"],"align":["right"]},{"label":["mean_receiving_air_yards_share"],"name":[29],"type":["dbl"],"align":["right"]},{"label":["sum_receiving_air_yards_share"],"name":[30],"type":["dbl"],"align":["right"]}],"data":[{"1":"George Pickens","2":"WR","3":"5.00","4":"20","5":"7.25","6":"29","7":"71.00","8":"284","9":"0.00","10":"0","11":"0.25","12":"1","13":"0.25","14":"1","15":"90.50","16":"362","17":"10.00","18":"40","19":"3.00","20":"12","21":"3.27","22":"13.07","23":"0","24":"0","25":"0.77","26":"3.06","27":"0.28","28":"1.11","29":"0.53","30":"2.11"},{"1":"Pat Freiermuth","2":"TE","3":"4.25","4":"17","5":"5.00","6":"20","7":"39.00","8":"156","9":"0.25","10":"1","11":"0.00","12":"0","13":"0.00","14":"0","15":"24.50","16":"98","17":"19.50","18":"78","19":"2.00","20":"8","21":"1.53","22":"6.10","23":"0","24":"0","25":"1.70","26":"6.79","27":"0.20","28":"0.78","29":"0.14","30":"0.57"},{"1":"Najee Harris","2":"RB","3":"2.50","4":"10","5":"3.75","6":"15","7":"21.00","8":"84","9":"0.00","10":"0","11":"0.00","12":"0","13":"0.00","14":"0","15":"-5.50","16":"-22","17":"22.25","18":"89","19":"0.50","20":"2","21":"-0.05","22":"-0.22","23":"0","24":"0","25":"-4.08","26":"-16.32","27":"0.14","28":"0.55","29":"-0.03","30":"-0.11"},{"1":"Calvin Austin","2":"WR","3":"1.75","4":"7","5":"2.50","6":"10","7":"31.25","8":"125","9":"0.25","10":"1","11":"0.00","12":"0","13":"0.00","14":"0","15":"25.75","16":"103","17":"15.75","18":"63","19":"1.00","20":"4","21":"2.31","22":"9.24","23":"0","24":"0","25":"0.96","26":"3.84","27":"0.10","28":"0.39","29":"0.16","30":"0.63"},{"1":"Van Jefferson","2":"WR","3":"1.67","4":"5","5":"2.67","6":"8","7":"12.00","8":"36","9":"0.00","10":"0","11":"0.00","12":"0","13":"0.00","14":"0","15":"26.67","16":"80","17":"8.67","18":"26","19":"0.33","20":"1","21":"-1.52","22":"-4.57","23":"0","24":"0","25":"0.47","26":"1.40","27":"0.12","28":"0.35","29":"0.16","30":"0.47"},{"1":"Cordarrelle Patterson","2":"RB","3":"1.25","4":"5","5":"1.75","6":"7","7":"8.50","8":"34","9":"0.00","10":"0","11":"0.00","12":"0","13":"0.00","14":"0","15":"6.75","16":"27","17":"6.25","18":"25","19":"0.50","20":"2","21":"-3.04","22":"-6.08","23":"0","24":"0","25":"1.73","26":"3.46","27":"0.11","28":"0.22","29":"0.07","30":"0.15"},{"1":"Jaylen Warren","2":"RB","3":"1.67","4":"5","5":"1.67","6":"5","7":"9.33","8":"28","9":"0.00","10":"0","11":"0.00","12":"0","13":"0.00","14":"0","15":"-2.00","16":"-6","17":"11.33","18":"34","19":"0.33","20":"1","21":"-0.06","22":"-0.19","23":"0","24":"0","25":"-1.83","26":"-5.50","27":"0.08","28":"0.23","29":"-0.01","30":"-0.04"}],"options":{"columns":{"min":{},"max":[10],"total":[30]},"rows":{"min":[10],"max":[10],"total":[7]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

  
Some of these statistics won't have any meaning summed (or possibly by taking an average), so I'll dig into each one to get clearer on that.
  
This looks like a good article on [EPA](https://bestballstats.com/expected-points-added-a-full-explanation/#:~:text=Expected%20Points%20Added%20(EPA)%20is,evaluate%20team%20and%20player%20performance.).


## Play by play data


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjQgPC0gbG9hZF9wYnAoc2Vhc29ucz1tb3N0X3JlY2VudF9zZWFzb24oKSlcbmBgYCJ9 -->

```r
play_by_play_2024 <- load_pbp(seasons=most_recent_season())
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## Average field position


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MzIsIm5jb2wiOjMsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMzIgw5cgMyJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUE2VlQyMDdDUUJBZDJnSlNvekhoMFJkL0FCNzB3YnV5WEZTMG9vR2krRVJXcU5oWXQ2U3RsMGMvMVM4UmQyRm5pNXVvaVRhWm50bXpjMlpucHR0MnZiZGg5MndBTU1HeStEdkxYY2gyM2FQU0ZvQmw4RVVHTENnSWZPWGJ4V2trd0FxM05ibGh0QzZrWjFhN1IraldHeTEwejV2S3JaMDBVWFZjUmJMWnFxUHJrSnJLMmtDeWRYT01wS3RFYnByL21uUlVmdEpXN3R5cGpzcFZKMDVhb1l0cHoycHByVVExbzBJTjV3ckp5eWFLekpPTHJtTFR0aHlTbG4yS2JxZUJyTkZSRXlKdEZKbW5wS2RZMStHd0xPWmJxY0gwcVZRbEVnMHIvOFJEaVFkL3hQMXZjRS9EM1Y5d1I4TnR3R2NKeEQwVGw1Q1BEbVozVDVqMWk0bHJuUHZCOG5PMklLMmdtUzF0VWZzUnNvdytlakhNZmdKVGt2bHhHQ2NlZlpUTFZmbzg2c2NKalJLZmpmcDN2aGNNK3p6Q1QveVF5WkMxaUxLSC9rOXhYNDh0Uk9GTEdZOFdjekhlK0dzeW1ienI5UTBDR21OOVNOcERtdER5WGNUMWZQV2hTZkxoV0p6SVJVWlJUbWhlbklrMFl1V0ppVXFHcGNIOUUzc29yVzlxKythWWplVDBNbk5mTWlPL0p2cm1yQXhqSXVVNUtjOTViT1F6RC9zSjZLMFhZT2FoOXl6ZFpUNlE2VHpLNDhobkNUYksyYmljaEFsRmlUMElBMlNtcmNQSEo5bSthbm4zQkFBQSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["avg_starting_field_position"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["rank_avg_starting_field_position"],"name":[3],"type":["int"],"align":["right"]}],"data":[{"1":"NO","2":"38","3":"1"},{"1":"BUF","2":"36","3":"2"},{"1":"DEN","2":"34","3":"3"},{"1":"MIN","2":"34","3":"3"},{"1":"CHI","2":"32","3":"4"},{"1":"GB","2":"32","3":"4"},{"1":"IND","2":"32","3":"4"},{"1":"LAC","2":"32","3":"4"},{"1":"NE","2":"32","3":"4"},{"1":"NYG","2":"32","3":"4"},{"1":"TB","2":"32","3":"4"},{"1":"TEN","2":"32","3":"4"},{"1":"WAS","2":"31","3":"5"},{"1":"CAR","2":"30","3":"6"},{"1":"CIN","2":"30","3":"6"},{"1":"CLE","2":"30","3":"6"},{"1":"DAL","2":"30","3":"6"},{"1":"DET","2":"30","3":"6"},{"1":"KC","2":"30","3":"6"},{"1":"MIA","2":"30","3":"6"},{"1":"BAL","2":"29","3":"7"},{"1":"LV","2":"29","3":"7"},{"1":"PIT","2":"29","3":"7"},{"1":"HOU","2":"28","3":"8"},{"1":"PHI","2":"28","3":"8"},{"1":"LA","2":"27","3":"9"},{"1":"NYJ","2":"27","3":"9"},{"1":"SEA","2":"27","3":"9"},{"1":"SF","2":"27","3":"9"},{"1":"ARI","2":"26","3":"10"},{"1":"JAX","2":"26","3":"10"},{"1":"ATL","2":"25","3":"11"}],"options":{"columns":{"min":{},"max":[10],"total":[3]},"rows":{"min":[10],"max":[10],"total":[32]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



## Run-Pass split

Here's run-pass split, but it lacks in-game context. If a team is behind, they'll be much more likely to be pass-heavy.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbImdyb3VwZWRfZGYiLCJ0YmxfZGYiLCJ0YmwiLCJkYXRhLmZyYW1lIl0sIm5yb3ciOjY0LCJuY29sIjo0LCJzdW1tYXJ5Ijp7IkEgdGliYmxlIjpbIjY0IMOXIDQiXSwiR3JvdXBzIjpbInBvc3RlYW0gWzMyXSJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUE5VldTMi9UUUJEZUprNnJSclNxeElrL3dLMDVrQU53cytQRWlaUFVDVWxLMHd2RlRadzJOTFd0eENuMHdQc2hEb2lIS2lFVklTNElCT0xZRzZmK0FQZ0IvQUgrQVBlRzJleXNkMnNxOFJaaXBhODdPL1BOWTJmSGFtclpaanJaVEJKQzRrUlI0RzhDUkpKWWJCanpad2hSWW5DWUlBcVpwdnNWTUI4SEFXaGtEcUNpSVo3VnlseXM1elF1NnVVY2lySHllYTdVR2lHMVVGa01xUVdUaTlaeW5vdEZyUmtTVEN1TUpSSm9OZUZWNVBaR0ppd3J4NTNpQ3liM2lsa1ZMcFYwYm00SVpsV1VraEhYcXBxTjBEOG5nb1plUzFxZGkyVk5Gd1Z3cjdocFpYbUF1aEVtV0F4RnJjYlR4dktaYnlUSkxEbEprWTdNSkpjaUZTaktsdTRpTG5qbzJxSVpva1dpYjZLWFVvT2x0a3R2SVI1SWVqYjVMVVV2NVdjL2NpNmt3UkhqSk0yWUdEeDVIT21RSHA1YnhiY0hnLzlZanZlSDdxL1JmOER6NTlpL1VlN1JpYjRyL3MxYi90bEsvNEZJeU14NHpnbDVDWGdIZUFONENuZ1BlQVY0QVhnT2VBaDRCSGdDZUF6WUFieEZQVDNmQTl3RTNNTHpmY1ExUUlBMm11OE9vQWU0QzlnRWJBRnVvMzBBdUFTNERyZ0s2Q0NHZ0M3QVE3NG42ZGJSWndQUXhoaXJnQlhBQmNBeVlBbHdFWFZ0OUR1SCtpYWdEcGlsZlZDck8ybTYxT29OUXBkYTNkNkY5VXl0bm1WNzVRdXpWMDUyNkZJckoxRFBkOEw4ckE5MGZWU3RaYWEza0craGZXRWZkN1NYOTFqYzBtZkdLL0h6YXp6dk1sN3BBWXRiUlA4aTZvc3FudFBNejhRNnpiM0lqbndUODVwbEZzOUV2d0xXWFVCK0FmTVhPcmdqUDl5UHNUMlBmbm1zSzQvOFBOWmxERmc4QS9VRzVqY3dqb0g5eStFNWkzbXo2Si9GdnVtZkdFOUh1NDUxNjJqUFlQL0NIZmtackZQRC9tbjhqSDRxNDBWK3lDUmFQZnBSczM4R1hKbHMyNEdkNnZUdFRTZENuKzU3bDFNdTZLa0wvYTVpZElwR285RitOQzRuMGJnS0txZDhieEE0OWlZUDV2ZnM3WlZnMjNkUU1jRS8zS1R2OUZzcmdSZlk5RHM2aU1TZTh2eWc2N2tRUFVaL2drMUdxcC9vUnhSelE1ZFcwNTV2clEvZGpmbFRweVAydU8rdTBhUmpGVnN6S0t1U3JMQXlsQkc2VDZMN3BPT3VkVjEraDBUUFhuVjZQSExiMlVKeEZqbzM3a25LNzNmZGdGOFV0SU1VdXlocVdsNlBhOFpYSndkZkFWeXl1SEtZQ2dBQSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["play_type"],"name":[2],"type":["chr"],"align":["left"]},{"label":["n"],"name":[3],"type":["int"],"align":["right"]},{"label":["perc_total"],"name":[4],"type":["dbl"],"align":["right"]}],"data":[{"1":"DAL","2":"pass","3":"163","4":"66.3"},{"1":"SEA","2":"pass","3":"171","4":"66.0"},{"1":"CLE","2":"pass","3":"168","4":"65.9"},{"1":"LV","2":"pass","3":"150","4":"64.9"},{"1":"ATL","2":"pass","3":"186","4":"63.9"},{"1":"HOU","2":"pass","3":"165","4":"62.3"},{"1":"CHI","2":"pass","3":"158","4":"62.2"},{"1":"NYG","2":"pass","3":"156","4":"62.2"},{"1":"JAX","2":"pass","3":"142","4":"62.0"},{"1":"CIN","2":"pass","3":"143","4":"61.6"},{"1":"LA","2":"pass","3":"145","4":"60.7"},{"1":"CAR","2":"pass","3":"144","4":"60.3"},{"1":"NYJ","2":"pass","3":"147","4":"60.0"},{"1":"TB","2":"pass","3":"169","4":"59.5"},{"1":"DEN","2":"pass","3":"142","4":"58.7"},{"1":"MIA","2":"pass","3":"144","4":"57.4"},{"1":"NO","2":"run","3":"134","4":"55.8"},{"1":"KC","2":"pass","3":"129","4":"55.4"},{"1":"TEN","2":"pass","3":"130","4":"55.3"},{"1":"PHI","2":"pass","3":"144","4":"55.2"},{"1":"BAL","2":"run","3":"136","4":"55.1"},{"1":"PIT","2":"run","3":"136","4":"53.5"},{"1":"NE","2":"pass","3":"126","4":"53.2"},{"1":"MIN","2":"pass","3":"116","4":"52.5"},{"1":"WAS","2":"run","3":"129","4":"52.4"},{"1":"LAC","2":"run","3":"110","4":"51.9"},{"1":"DET","2":"pass","3":"132","4":"51.4"},{"1":"IND","2":"pass","3":"108","4":"51.4"},{"1":"SF","2":"pass","3":"133","4":"51.2"},{"1":"BUF","2":"pass","3":"109","4":"50.7"},{"1":"ARI","2":"pass","3":"118","4":"50.6"},{"1":"GB","2":"run","3":"131","4":"50.4"},{"1":"GB","2":"pass","3":"129","4":"49.6"},{"1":"ARI","2":"run","3":"115","4":"49.4"},{"1":"BUF","2":"run","3":"106","4":"49.3"},{"1":"SF","2":"run","3":"127","4":"48.8"},{"1":"DET","2":"run","3":"125","4":"48.6"},{"1":"IND","2":"run","3":"102","4":"48.6"},{"1":"LAC","2":"pass","3":"102","4":"48.1"},{"1":"WAS","2":"pass","3":"117","4":"47.6"},{"1":"MIN","2":"run","3":"105","4":"47.5"},{"1":"NE","2":"run","3":"111","4":"46.8"},{"1":"PIT","2":"pass","3":"118","4":"46.5"},{"1":"BAL","2":"pass","3":"111","4":"44.9"},{"1":"PHI","2":"run","3":"117","4":"44.8"},{"1":"TEN","2":"run","3":"105","4":"44.7"},{"1":"KC","2":"run","3":"104","4":"44.6"},{"1":"NO","2":"pass","3":"106","4":"44.2"},{"1":"MIA","2":"run","3":"107","4":"42.6"},{"1":"DEN","2":"run","3":"100","4":"41.3"},{"1":"TB","2":"run","3":"115","4":"40.5"},{"1":"NYJ","2":"run","3":"98","4":"40.0"},{"1":"CAR","2":"run","3":"95","4":"39.7"},{"1":"LA","2":"run","3":"94","4":"39.3"},{"1":"CIN","2":"run","3":"89","4":"38.4"},{"1":"JAX","2":"run","3":"87","4":"38.0"},{"1":"CHI","2":"run","3":"96","4":"37.8"},{"1":"NYG","2":"run","3":"95","4":"37.8"},{"1":"HOU","2":"run","3":"100","4":"37.7"},{"1":"ATL","2":"run","3":"105","4":"36.1"},{"1":"LV","2":"run","3":"81","4":"35.1"},{"1":"CLE","2":"run","3":"87","4":"34.1"},{"1":"SEA","2":"run","3":"88","4":"34.0"},{"1":"DAL","2":"run","3":"83","4":"33.7"}],"options":{"columns":{"min":{},"max":[10],"total":[4]},"rows":{"min":[10],"max":[10],"total":[64]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


```{=html}

<!-- rnb-html-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInNoaW55LnRhZyJdLCJzaXppbmdQb2xpY3kiOltdfX0= -->

<div id="qqgixjbnqs" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#qqgixjbnqs table {
  font-family: Roboto, system-ui, 'Segoe UI', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#qqgixjbnqs thead, #qqgixjbnqs tbody, #qqgixjbnqs tfoot, #qqgixjbnqs tr, #qqgixjbnqs td, #qqgixjbnqs th {
  border-style: none;
}

#qqgixjbnqs p {
  margin: 0;
  padding: 0;
}

#qqgixjbnqs .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: rgba(255, 255, 255, 0);
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: rgba(255, 255, 255, 0);
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#qqgixjbnqs .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#qqgixjbnqs .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#qqgixjbnqs .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#qqgixjbnqs .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qqgixjbnqs .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qqgixjbnqs .gt_col_headings {
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: rgba(255, 255, 255, 0);
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#qqgixjbnqs .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#qqgixjbnqs .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#qqgixjbnqs .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#qqgixjbnqs .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#qqgixjbnqs .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#qqgixjbnqs .gt_spanner_row {
  border-bottom-style: hidden;
}

#qqgixjbnqs .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#qqgixjbnqs .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#qqgixjbnqs .gt_from_md > :first-child {
  margin-top: 0;
}

#qqgixjbnqs .gt_from_md > :last-child {
  margin-bottom: 0;
}

#qqgixjbnqs .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#qqgixjbnqs .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#qqgixjbnqs .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#qqgixjbnqs .gt_row_group_first td {
  border-top-width: 2px;
}

#qqgixjbnqs .gt_row_group_first th {
  border-top-width: 2px;
}

#qqgixjbnqs .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qqgixjbnqs .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#qqgixjbnqs .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#qqgixjbnqs .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qqgixjbnqs .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#qqgixjbnqs .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#qqgixjbnqs .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#qqgixjbnqs .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#qqgixjbnqs .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#qqgixjbnqs .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qqgixjbnqs .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#qqgixjbnqs .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#qqgixjbnqs .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#qqgixjbnqs .gt_left {
  text-align: left;
}

#qqgixjbnqs .gt_center {
  text-align: center;
}

#qqgixjbnqs .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#qqgixjbnqs .gt_font_normal {
  font-weight: normal;
}

#qqgixjbnqs .gt_font_bold {
  font-weight: bold;
}

#qqgixjbnqs .gt_font_italic {
  font-style: italic;
}

#qqgixjbnqs .gt_super {
  font-size: 65%;
}

#qqgixjbnqs .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#qqgixjbnqs .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#qqgixjbnqs .gt_indent_1 {
  text-indent: 5px;
}

#qqgixjbnqs .gt_indent_2 {
  text-indent: 10px;
}

#qqgixjbnqs .gt_indent_3 {
  text-indent: 15px;
}

#qqgixjbnqs .gt_indent_4 {
  text-indent: 20px;
}

#qqgixjbnqs .gt_indent_5 {
  text-indent: 25px;
}

#qqgixjbnqs .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#qqgixjbnqs div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
  <table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_heading">
      <td colspan="3" class="gt_heading gt_title gt_font_normal" style><span class='gt_from_md'><strong>Run-pass split by NFL teams in the 2024 Season</strong></span></td>
    </tr>
    <tr class="gt_heading">
      <td colspan="3" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style>Of plays run within 16 points (ahead or behind)</td>
    </tr>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Play type">Play type</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="# of plays"># of plays</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="% of total">% of total</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="ARI - 1">ARI - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="ARI - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="ARI - 1  n" class="gt_row gt_right">94</td>
<td headers="ARI - 1  perc_total" class="gt_row gt_right" style="background-color: #F97D5D; color: #FFFFFF;">57.7</td></tr>
    <tr><td headers="ARI - 1  play_type" class="gt_row gt_left">run</td>
<td headers="ARI - 1  n" class="gt_row gt_right">69</td>
<td headers="ARI - 1  perc_total" class="gt_row gt_right" style="background-color: #59167E; color: #FFFFFF;">42.3</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="ATL - 1">ATL - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="ATL - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="ATL - 1  n" class="gt_row gt_right">186</td>
<td headers="ATL - 1  perc_total" class="gt_row gt_right" style="background-color: #FED597; color: #000000;">63.9</td></tr>
    <tr><td headers="ATL - 1  play_type" class="gt_row gt_left">run</td>
<td headers="ATL - 1  n" class="gt_row gt_right">105</td>
<td headers="ATL - 1  perc_total" class="gt_row gt_right" style="background-color: #110C2F; color: #FFFFFF;">36.1</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="BAL - 1">BAL - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="BAL - 1  play_type" class="gt_row gt_left">run</td>
<td headers="BAL - 1  n" class="gt_row gt_right">106</td>
<td headers="BAL - 1  perc_total" class="gt_row gt_right" style="background-color: #C23B76; color: #FFFFFF;">51.0</td></tr>
    <tr><td headers="BAL - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="BAL - 1  n" class="gt_row gt_right">102</td>
<td headers="BAL - 1  perc_total" class="gt_row gt_right" style="background-color: #A9327C; color: #FFFFFF;">49.0</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="BUF - 1">BUF - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="BUF - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="BUF - 1  n" class="gt_row gt_right">73</td>
<td headers="BUF - 1  perc_total" class="gt_row gt_right" style="background-color: #CC4071; color: #FFFFFF;">51.8</td></tr>
    <tr><td headers="BUF - 1  play_type" class="gt_row gt_left">run</td>
<td headers="BUF - 1  n" class="gt_row gt_right">68</td>
<td headers="BUF - 1  perc_total" class="gt_row gt_right" style="background-color: #A02F7F; color: #FFFFFF;">48.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="CAR - 1">CAR - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="CAR - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="CAR - 1  n" class="gt_row gt_right">76</td>
<td headers="CAR - 1  perc_total" class="gt_row gt_right" style="background-color: #FD9C6B; color: #000000;">59.8</td></tr>
    <tr><td headers="CAR - 1  play_type" class="gt_row gt_left">run</td>
<td headers="CAR - 1  n" class="gt_row gt_right">51</td>
<td headers="CAR - 1  perc_total" class="gt_row gt_right" style="background-color: #3F0F73; color: #FFFFFF;">40.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="CHI - 1">CHI - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="CHI - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="CHI - 1  n" class="gt_row gt_right">153</td>
<td headers="CHI - 1  perc_total" class="gt_row gt_right" style="background-color: #FEBD83; color: #000000;">62.2</td></tr>
    <tr><td headers="CHI - 1  play_type" class="gt_row gt_left">run</td>
<td headers="CHI - 1  n" class="gt_row gt_right">93</td>
<td headers="CHI - 1  perc_total" class="gt_row gt_right" style="background-color: #21114D; color: #FFFFFF;">37.8</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="CIN - 1">CIN - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="CIN - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="CIN - 1  n" class="gt_row gt_right">143</td>
<td headers="CIN - 1  perc_total" class="gt_row gt_right" style="background-color: #FEB57C; color: #000000;">61.6</td></tr>
    <tr><td headers="CIN - 1  play_type" class="gt_row gt_left">run</td>
<td headers="CIN - 1  n" class="gt_row gt_right">89</td>
<td headers="CIN - 1  perc_total" class="gt_row gt_right" style="background-color: #271259; color: #FFFFFF;">38.4</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="CLE - 1">CLE - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="CLE - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="CLE - 1  n" class="gt_row gt_right">131</td>
<td headers="CLE - 1  perc_total" class="gt_row gt_right" style="background-color: #FED99B; color: #000000;">64.2</td></tr>
    <tr><td headers="CLE - 1  play_type" class="gt_row gt_left">run</td>
<td headers="CLE - 1  n" class="gt_row gt_right">73</td>
<td headers="CLE - 1  perc_total" class="gt_row gt_right" style="background-color: #0E0A2A; color: #FFFFFF;">35.8</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="DAL - 1">DAL - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="DAL - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="DAL - 1  n" class="gt_row gt_right">107</td>
<td headers="DAL - 1  perc_total" class="gt_row gt_right" style="background-color: #FEC387; color: #000000;">62.6</td></tr>
    <tr><td headers="DAL - 1  play_type" class="gt_row gt_left">run</td>
<td headers="DAL - 1  n" class="gt_row gt_right">64</td>
<td headers="DAL - 1  perc_total" class="gt_row gt_right" style="background-color: #1D1046; color: #FFFFFF;">37.4</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="DEN - 1">DEN - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="DEN - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="DEN - 1  n" class="gt_row gt_right">140</td>
<td headers="DEN - 1  perc_total" class="gt_row gt_right" style="background-color: #FE9F6D; color: #000000;">60.1</td></tr>
    <tr><td headers="DEN - 1  play_type" class="gt_row gt_left">run</td>
<td headers="DEN - 1  n" class="gt_row gt_right">93</td>
<td headers="DEN - 1  perc_total" class="gt_row gt_right" style="background-color: #3B0F70; color: #FFFFFF;">39.9</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="DET - 1">DET - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="DET - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="DET - 1  n" class="gt_row gt_right">132</td>
<td headers="DET - 1  perc_total" class="gt_row gt_right" style="background-color: #C73D74; color: #FFFFFF;">51.4</td></tr>
    <tr><td headers="DET - 1  play_type" class="gt_row gt_left">run</td>
<td headers="DET - 1  n" class="gt_row gt_right">125</td>
<td headers="DET - 1  perc_total" class="gt_row gt_right" style="background-color: #A5307E; color: #FFFFFF;">48.6</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="GB - 1">GB - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="GB - 1  play_type" class="gt_row gt_left">run</td>
<td headers="GB - 1  n" class="gt_row gt_right">120</td>
<td headers="GB - 1  perc_total" class="gt_row gt_right" style="background-color: #F9795D; color: #FFFFFF;">57.4</td></tr>
    <tr><td headers="GB - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="GB - 1  n" class="gt_row gt_right">89</td>
<td headers="GB - 1  perc_total" class="gt_row gt_right" style="background-color: #5C177F; color: #FFFFFF;">42.6</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="HOU - 1">HOU - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="HOU - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="HOU - 1  n" class="gt_row gt_right">136</td>
<td headers="HOU - 1  perc_total" class="gt_row gt_right" style="background-color: #FA8360; color: #000000;">58.1</td></tr>
    <tr><td headers="HOU - 1  play_type" class="gt_row gt_left">run</td>
<td headers="HOU - 1  n" class="gt_row gt_right">98</td>
<td headers="HOU - 1  perc_total" class="gt_row gt_right" style="background-color: #54137D; color: #FFFFFF;">41.9</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="IND - 1">IND - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="IND - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="IND - 1  n" class="gt_row gt_right">102</td>
<td headers="IND - 1  perc_total" class="gt_row gt_right" style="background-color: #C23B76; color: #FFFFFF;">51.0</td></tr>
    <tr><td headers="IND - 1  play_type" class="gt_row gt_left">run</td>
<td headers="IND - 1  n" class="gt_row gt_right">98</td>
<td headers="IND - 1  perc_total" class="gt_row gt_right" style="background-color: #A9327C; color: #FFFFFF;">49.0</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="JAX - 1">JAX - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="JAX - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="JAX - 1  n" class="gt_row gt_right">102</td>
<td headers="JAX - 1  perc_total" class="gt_row gt_right" style="background-color: #F97C5D; color: #FFFFFF;">57.6</td></tr>
    <tr><td headers="JAX - 1  play_type" class="gt_row gt_left">run</td>
<td headers="JAX - 1  n" class="gt_row gt_right">75</td>
<td headers="JAX - 1  perc_total" class="gt_row gt_right" style="background-color: #5A167E; color: #FFFFFF;">42.4</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="KC - 1">KC - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="KC - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="KC - 1  n" class="gt_row gt_right">129</td>
<td headers="KC - 1  perc_total" class="gt_row gt_right" style="background-color: #EF5E5E; color: #FFFFFF;">55.4</td></tr>
    <tr><td headers="KC - 1  play_type" class="gt_row gt_left">run</td>
<td headers="KC - 1  n" class="gt_row gt_right">104</td>
<td headers="KC - 1  perc_total" class="gt_row gt_right" style="background-color: #742081; color: #FFFFFF;">44.6</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="LA - 1">LA - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="LA - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="LA - 1  n" class="gt_row gt_right">119</td>
<td headers="LA - 1  perc_total" class="gt_row gt_right" style="background-color: #FEA470; color: #000000;">60.4</td></tr>
    <tr><td headers="LA - 1  play_type" class="gt_row gt_left">run</td>
<td headers="LA - 1  n" class="gt_row gt_right">78</td>
<td headers="LA - 1  perc_total" class="gt_row gt_right" style="background-color: #37106B; color: #FFFFFF;">39.6</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="LAC - 1">LAC - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="LAC - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="LAC - 1  n" class="gt_row gt_right">92</td>
<td headers="LAC - 1  perc_total" class="gt_row gt_right" style="background-color: #BC3978; color: #FFFFFF;">50.5</td></tr>
    <tr><td headers="LAC - 1  play_type" class="gt_row gt_left">run</td>
<td headers="LAC - 1  n" class="gt_row gt_right">90</td>
<td headers="LAC - 1  perc_total" class="gt_row gt_right" style="background-color: #AF357B; color: #FFFFFF;">49.5</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="LV - 1">LV - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="LV - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="LV - 1  n" class="gt_row gt_right">122</td>
<td headers="LV - 1  perc_total" class="gt_row gt_right" style="background-color: #FEA873; color: #000000;">60.7</td></tr>
    <tr><td headers="LV - 1  play_type" class="gt_row gt_left">run</td>
<td headers="LV - 1  n" class="gt_row gt_right">79</td>
<td headers="LV - 1  perc_total" class="gt_row gt_right" style="background-color: #331068; color: #FFFFFF;">39.3</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="MIA - 1">MIA - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="MIA - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="MIA - 1  n" class="gt_row gt_right">109</td>
<td headers="MIA - 1  perc_total" class="gt_row gt_right" style="background-color: #E85462; color: #FFFFFF;">54.5</td></tr>
    <tr><td headers="MIA - 1  play_type" class="gt_row gt_left">run</td>
<td headers="MIA - 1  n" class="gt_row gt_right">91</td>
<td headers="MIA - 1  perc_total" class="gt_row gt_right" style="background-color: #7E2482; color: #FFFFFF;">45.5</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="MIN - 1">MIN - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="MIN - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="MIN - 1  n" class="gt_row gt_right">95</td>
<td headers="MIN - 1  perc_total" class="gt_row gt_right" style="background-color: #F4685C; color: #FFFFFF;">56.2</td></tr>
    <tr><td headers="MIN - 1  play_type" class="gt_row gt_left">run</td>
<td headers="MIN - 1  n" class="gt_row gt_right">74</td>
<td headers="MIN - 1  perc_total" class="gt_row gt_right" style="background-color: #6B1C81; color: #FFFFFF;">43.8</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="NE - 1">NE - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="NE - 1  play_type" class="gt_row gt_left">run</td>
<td headers="NE - 1  n" class="gt_row gt_right">92</td>
<td headers="NE - 1  perc_total" class="gt_row gt_right" style="background-color: #C73D74; color: #FFFFFF;">51.4</td></tr>
    <tr><td headers="NE - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="NE - 1  n" class="gt_row gt_right">87</td>
<td headers="NE - 1  perc_total" class="gt_row gt_right" style="background-color: #A5307E; color: #FFFFFF;">48.6</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="NO - 1">NO - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="NO - 1  play_type" class="gt_row gt_left">run</td>
<td headers="NO - 1  n" class="gt_row gt_right">97</td>
<td headers="NO - 1  perc_total" class="gt_row gt_right" style="background-color: #D9466B; color: #FFFFFF;">53.0</td></tr>
    <tr><td headers="NO - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="NO - 1  n" class="gt_row gt_right">86</td>
<td headers="NO - 1  perc_total" class="gt_row gt_right" style="background-color: #912B80; color: #FFFFFF;">47.0</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="NYG - 1">NYG - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="NYG - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="NYG - 1  n" class="gt_row gt_right">128</td>
<td headers="NYG - 1  perc_total" class="gt_row gt_right" style="background-color: #FD9C6B; color: #000000;">59.8</td></tr>
    <tr><td headers="NYG - 1  play_type" class="gt_row gt_left">run</td>
<td headers="NYG - 1  n" class="gt_row gt_right">86</td>
<td headers="NYG - 1  perc_total" class="gt_row gt_right" style="background-color: #3F0F73; color: #FFFFFF;">40.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="NYJ - 1">NYJ - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="NYJ - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="NYJ - 1  n" class="gt_row gt_right">125</td>
<td headers="NYJ - 1  perc_total" class="gt_row gt_right" style="background-color: #FE9F6D; color: #000000;">60.1</td></tr>
    <tr><td headers="NYJ - 1  play_type" class="gt_row gt_left">run</td>
<td headers="NYJ - 1  n" class="gt_row gt_right">83</td>
<td headers="NYJ - 1  perc_total" class="gt_row gt_right" style="background-color: #3B0F70; color: #FFFFFF;">39.9</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="PHI - 1">PHI - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="PHI - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="PHI - 1  n" class="gt_row gt_right">116</td>
<td headers="PHI - 1  perc_total" class="gt_row gt_right" style="background-color: #D6446D; color: #FFFFFF;">52.7</td></tr>
    <tr><td headers="PHI - 1  play_type" class="gt_row gt_left">run</td>
<td headers="PHI - 1  n" class="gt_row gt_right">104</td>
<td headers="PHI - 1  perc_total" class="gt_row gt_right" style="background-color: #942C80; color: #FFFFFF;">47.3</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="PIT - 1">PIT - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="PIT - 1  play_type" class="gt_row gt_left">run</td>
<td headers="PIT - 1  n" class="gt_row gt_right">127</td>
<td headers="PIT - 1  perc_total" class="gt_row gt_right" style="background-color: #E24D66; color: #FFFFFF;">53.8</td></tr>
    <tr><td headers="PIT - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="PIT - 1  n" class="gt_row gt_right">109</td>
<td headers="PIT - 1  perc_total" class="gt_row gt_right" style="background-color: #872881; color: #FFFFFF;">46.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="SEA - 1">SEA - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="SEA - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="SEA - 1  n" class="gt_row gt_right">171</td>
<td headers="SEA - 1  perc_total" class="gt_row gt_right" style="background-color: #FCFDBF; color: #000000;">66.8</td></tr>
    <tr><td headers="SEA - 1  play_type" class="gt_row gt_left">run</td>
<td headers="SEA - 1  n" class="gt_row gt_right">85</td>
<td headers="SEA - 1  perc_total" class="gt_row gt_right" style="background-color: #000004; color: #FFFFFF;">33.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="SF - 1">SF - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="SF - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="SF - 1  n" class="gt_row gt_right">125</td>
<td headers="SF - 1  perc_total" class="gt_row gt_right" style="background-color: #CD4071; color: #FFFFFF;">51.9</td></tr>
    <tr><td headers="SF - 1  play_type" class="gt_row gt_left">run</td>
<td headers="SF - 1  n" class="gt_row gt_right">116</td>
<td headers="SF - 1  perc_total" class="gt_row gt_right" style="background-color: #9F2F7F; color: #FFFFFF;">48.1</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="TB - 1">TB - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="TB - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="TB - 1  n" class="gt_row gt_right">134</td>
<td headers="TB - 1  perc_total" class="gt_row gt_right" style="background-color: #FA815F; color: #000000;">58.0</td></tr>
    <tr><td headers="TB - 1  play_type" class="gt_row gt_left">run</td>
<td headers="TB - 1  n" class="gt_row gt_right">97</td>
<td headers="TB - 1  perc_total" class="gt_row gt_right" style="background-color: #56147D; color: #FFFFFF;">42.0</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="TEN - 1">TEN - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="TEN - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="TEN - 1  n" class="gt_row gt_right">125</td>
<td headers="TEN - 1  perc_total" class="gt_row gt_right" style="background-color: #EB5761; color: #FFFFFF;">54.8</td></tr>
    <tr><td headers="TEN - 1  play_type" class="gt_row gt_left">run</td>
<td headers="TEN - 1  n" class="gt_row gt_right">103</td>
<td headers="TEN - 1  perc_total" class="gt_row gt_right" style="background-color: #7A2382; color: #FFFFFF;">45.2</td></tr>
    <tr class="gt_group_heading_row">
      <th colspan="3" class="gt_group_heading" scope="colgroup" id="WAS - 1">WAS - 1</th>
    </tr>
    <tr class="gt_row_group_first"><td headers="WAS - 1  play_type" class="gt_row gt_left">run</td>
<td headers="WAS - 1  n" class="gt_row gt_right">115</td>
<td headers="WAS - 1  perc_total" class="gt_row gt_right" style="background-color: #DC4869; color: #FFFFFF;">53.2</td></tr>
    <tr><td headers="WAS - 1  play_type" class="gt_row gt_left">pass</td>
<td headers="WAS - 1  n" class="gt_row gt_right">101</td>
<td headers="WAS - 1  perc_total" class="gt_row gt_right" style="background-color: #8E2A81; color: #FFFFFF;">46.8</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="3">Data from `nflreadr::` package</td>
    </tr>
  </tfoot>
  
</table>
</div>


<!-- rnb-html-end -->

```

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



## Average years per rush / pass play

## Personnel groupings 

## When is George Pickens targeted? 

### Splits

### Downs 

### Quarters 

### Position at snap 

### Redzone 


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6OSwibmNvbCI6Nywic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyI5IMOXIDciXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBN1ZUVFcvVU1CQ2R6WDZrV2VocUpWcXBCODRJSWEwdkt3RTNGclVxdElkcWhRcjBGaG5IbTBUTjJwSHR0SlFUUDQyZnhJMWIyM0ZpTDYyRktpU0VwY21NMzh6WWI4YVREd2RuOC9IWkdBRDZNQmpnZDRnbUREK2VIczVlQXd3aTNQUmdBSW5WWDlIOUJJMFlaWXFTT0VkL2VYVDYzMHlBaWIzcXpVOW8xNy9xZ0hyeWppeExkczZGZHNEakpUbFV2T1JxM1pqQ1lZOCtrV08rV25HbHBiQTVON2ljYTJ1ZnZHMjBLWVVQM1NkTGFrd1g2azQ4SUorcExrcVJtdzIyZFl5WVVueXpQeUh2Y1Y5cXRMZGJlZ0FqbE9pTzlQNGdiV3NXODY2dXhVdW5YM1Q2eHg3Y1c0dXAwenRPUDNYNjJTWms0dTRPVy9iZ2VpQ3U0eGZlKy96dnpsM3NoZnp1amVOUTBEVzNEYlBIeHc2TWE2a05wMnZmZThXemIxTHd0SzdvbGNOMkZHZTh2T0NxQlZIWmM1eHZtOGxHbU5SUWxYUGpSMktxbTNWNlJWV20wNXlXZ21jKzJPSkdOcXpJNUtWL3lkM2Z3WFNGYzVBeWFsZ1JVRStVdkNTZXZuM3Y2RHQrY0twK2hUV3lpbXBmb3dmSEdUV1VySlNsRFhBZHBNU3lOcVhFZVliSS9xdWpJTG1uQW1EYUNNc2ttN0dpRWVleithdkEzNjlGYmkrRmJ1TEFNYloyY3NlT094clJqVXNmdWZRUkZ6bjJ6TmRUMFMrODhpZG4vTUtaRTJ4STJ3OVNxMUlZWHlpaW1oaHBxRThaTTFsNXBDMGRybThCU3h2NFpjRUVBQUE9In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["redzone_play"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["receiver_player_name"],"name":[3],"type":["chr"],"align":["left"]},{"label":["count_targets"],"name":[4],"type":["int"],"align":["right"]},{"label":["sum_yards_gained"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["sum_touchdown"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["sum_yards_after_catch"],"name":[7],"type":["dbl"],"align":["right"]}],"data":[{"1":"PIT","2":"1","3":"G.Pickens","4":"6","5":"19","6":"0","7":"4"},{"1":"PIT","2":"1","3":"P.Freiermuth","4":"2","5":"22","6":"1","7":"5"},{"1":"PIT","2":"1","3":"V.Jefferson","4":"2","5":"13","6":"0","7":"12"},{"1":"PIT","2":"1","3":"NA","4":"2","5":"-6","6":"0","7":"0"},{"1":"PIT","2":"1","3":"C.Austin","4":"1","5":"0","6":"0","7":"0"},{"1":"PIT","2":"1","3":"C.Patterson","4":"1","5":"4","6":"0","7":"0"},{"1":"PIT","2":"1","3":"D.Washington","4":"1","5":"5","6":"1","7":"0"},{"1":"PIT","2":"1","3":"J.Warren","4":"1","5":"7","6":"0","7":"6"},{"1":"PIT","2":"1","3":"N.Harris","4":"1","5":"11","6":"0","7":"11"}],"options":{"columns":{"min":{},"max":[10],"total":[7]},"rows":{"min":[10],"max":[10],"total":[9]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->

