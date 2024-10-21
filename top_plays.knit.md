
<!-- rnb-text-begin -->

---
title: "NFL Analytics: top high-leverage plays"
output: html_notebook
---


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeSh0aWR5dmVyc2UpXG5saWJyYXJ5KG5mbHZlcnNlKVxubGlicmFyeShndClcbmxpYnJhcnkoZ3RFeHRyYXMpXG5saWJyYXJ5KGdndGV4dClcbmxpYnJhcnkoZ2dyZXBlbClcbmxpYnJhcnkocGF0Y2h3b3JrKVxubGlicmFyeShnZ2ltYWdlKVxuYGBgIn0= -->

```r
library(tidyverse)
library(nflverse)
library(gt)
library(gtExtras)
library(ggtext)
library(ggrepel)
library(patchwork)
library(ggimage)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuICB0aGVtZShcbiAgICB0ZXh0ID0gZWxlbWVudF90ZXh0KGZhbWlseSA9IFwiTGV4ZW5kXCIsXG4gICAgICAgICAgICAgICAgICAgICAgICBzaXplID0gYmFzZV9zaXplLFxuICAgICAgICAgICAgICAgICAgICAgICAgY29sb3IgPSBcImJsYWNrXCIpLFxuICAgIGF4aXMudGlja3MgPSBlbGVtZW50X2JsYW5rKCksXG4gICAgYXhpcy50aXRsZSA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpLFxuICAgIGF4aXMudGV4dCA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpLFxuICAgIHBsb3QudGl0bGUucG9zaXRpb24gPSBcInBsb3RcIixcbiAgICBwbG90LnRpdGxlID0gZWxlbWVudF9tYXJrZG93bihzaXplID0gMTYsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgdmp1c3QgPSAuMDIsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaGp1c3QgPSAwLjUpLFxuICAgIHBsb3Quc3VidGl0bGUgPSBlbGVtZW50X21hcmtkb3duKGhqdXN0ID0gMC41KSxcbiAgICBwbG90LmNhcHRpb24gPSBlbGVtZW50X21hcmtkb3duKHNpemUgPSA4KSxcbiAgICBwYW5lbC5ncmlkLm1pbm9yID0gZWxlbWVudF9ibGFuaygpLFxuICAgIHBhbmVsLmdyaWQubWFqb3IgPSAgZWxlbWVudF9saW5lKGNvbG9yID0gXCIjZDBkMGQwXCIpLFxuICAgIHBhbmVsLmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoZmlsbCA9IFwiI2Y3ZjdmN1wiKSxcbiAgICBwbG90LmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoZmlsbCA9IFwiI2Y3ZjdmN1wiKSxcbiAgICBwYW5lbC5ib3JkZXIgPSBlbGVtZW50X2JsYW5rKCksXG4gICAgbGVnZW5kLmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoY29sb3IgPSBcIiNGN0Y3RjdcIiksXG4gICAgbGVnZW5kLmtleSA9IGVsZW1lbnRfcmVjdChjb2xvciA9IFwiI0Y3RjdGN1wiKSxcbiAgICBsZWdlbmQudGl0bGUgPSBlbGVtZW50X3RleHQoZmFjZSA9IFwiYm9sZFwiKSxcbiAgICBsZWdlbmQudGl0bGUuYWxpZ24gPSAwLjUsXG4gICAgc3RyaXAudGV4dCA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpKVxuXG5gYGAifQ== -->

```r
  theme(
    text = element_text(family = "Lexend",
                        size = base_size,
                        color = "black"),
    axis.ticks = element_blank(),
    axis.title = element_text(face = "bold"),
    axis.text = element_text(face = "bold"),
    plot.title.position = "plot",
    plot.title = element_markdown(size = 16,
                                  vjust = .02,
                                  hjust = 0.5),
    plot.subtitle = element_markdown(hjust = 0.5),
    plot.caption = element_markdown(size = 8),
    panel.grid.minor = element_blank(),
    panel.grid.major =  element_line(color = "#d0d0d0"),
    panel.background = element_rect(fill = "#f7f7f7"),
    plot.background = element_rect(fill = "#f7f7f7"),
    panel.border = element_blank(),
    legend.background = element_rect(color = "#F7F7F7"),
    legend.key = element_rect(color = "#F7F7F7"),
    legend.title = element_text(face = "bold"),
    legend.title.align = 0.5,
    strip.text = element_text(face = "bold"))

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiRXJyb3I6IG9iamVjdCAnYmFzZV9zaXplJyBub3QgZm91bmRcbiJ9 -->

```
Error: object 'base_size' not found
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudGVhbXMgPC0gbmZscmVhZHI6OmxvYWRfdGVhbXMoY3VycmVudCA9IFRSVUUpXG5gYGAifQ== -->

```r
teams <- nflreadr::load_teams(current = TRUE)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


# Data 


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjQgPC0gbmZscmVhZHI6OmxvYWRfcGJwKHNlYXNvbnMgPSBtb3N0X3JlY2VudF9zZWFzb24oKSlcbmBgYCJ9 -->

```r
play_by_play_2024 <- nflreadr::load_pbp(seasons = most_recent_season())
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudG9wX3BsYXlzIDwtIHBsYXlfYnlfcGxheV8yMDI0ICU+JSBcbiAgZmlsdGVyKHN0cl9kZXRlY3QoZ2FtZV9pZCwgJ1BJVCcpKSAlPiUgXG4gIGxlZnRfam9pbih4PS4sXG4gICAgICAgICAgICB5PXRlYW1zLFxuICAgICAgICAgICAgYnk9YygncG9zdGVhbScgPSAndGVhbV9hYmJyJykpICU+JSBcbiAgbXV0YXRlKGRvd25fZGlzdCA9IHBhc3RlKGRvd24sIHlkc3RvZ28sIHNlcCA9ICctJyksXG4gICAgICAgICBzY29yZSA9IHBhc3RlKHRvdGFsX2F3YXlfc2NvcmUsIHRvdGFsX2hvbWVfc2NvcmUsIHNlcCA9ICctJyksIFxuICAgICAgICAgcGxheV90eXBlID0gY2FzZV93aGVuKHBsYXlfdHlwZSA9PSAncGFzcycgfiAnUGFzcycsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdydW4nIH4gJ1J1bicsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdmaWVsZF9nb2FsJyB+ICdGRycsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdwdW50JyB+ICdQdW50JyxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBUUlVFIH4gJ090aGVyJyksXG4gICAgICAgICBhYnNfZXBhID0gYWJzKGVwYSksXG4gICAgICAgICB3cF9jaGcgPSBhYnMobGVhZCh3cCkgLSB3cCkpICU+JSBcbiAgZ3JvdXBfYnkoZ2FtZV9pZCkgJT4lIFxuICBhcnJhbmdlKC1hYnNfZXBhKSAlPiVcbiAgc2VsZWN0KGdhbWVfaWQsIHRlYW1fd29yZG1hcmssIHF0ciwgdGltZSwgZG93bl9kaXN0LCB5cmRsbiwgc2NvcmUsIHBsYXlfdHlwZSxcbiAgICAgICAgIGRlc2MsIGVwYSwgd3AsIHdwX2NoZykgJT4lXG4gICMgZmlsdGVyaW5nIG91dCBnYXJiYWdlIHRpbWUgKENvbmdlbGlvIGJvb2sgcmVjb21tZW5kcyB1c2luZyA5NS81IHNwbGl0IGlmIHlvdSdyZSBnb2luZyB0byByZW1vdmUgZ2FyYmFnZSB0aW1lIGF0IGFsbClcbiAgZmlsdGVyKHdwID4gLjA1ICYgd3AgPCAuOTUpICU+JSBcbiAgc2xpY2UoMToxMCkgJT4lIFxuICB1bmdyb3VwKClcbmBgYCJ9 -->

```r
top_plays <- play_by_play_2024 %>% 
  filter(str_detect(game_id, 'PIT')) %>% 
  left_join(x=.,
            y=teams,
            by=c('posteam' = 'team_abbr')) %>% 
  mutate(down_dist = paste(down, ydstogo, sep = '-'),
         score = paste(total_away_score, total_home_score, sep = '-'), 
         play_type = case_when(play_type == 'pass' ~ 'Pass',
                               play_type == 'run' ~ 'Run',
                               play_type == 'field_goal' ~ 'FG',
                               play_type == 'punt' ~ 'Punt',
                               TRUE ~ 'Other'),
         abs_epa = abs(epa),
         wp_chg = abs(lead(wp) - wp)) %>% 
  group_by(game_id) %>% 
  arrange(-abs_epa) %>%
  select(game_id, team_wordmark, qtr, time, down_dist, yrdln, score, play_type,
         desc, epa, wp, wp_chg) %>%
  # filtering out garbage time (Congelio book recommends using 95/5 split if you're going to remove garbage time at all)
  filter(wp > .05 & wp < .95) %>% 
  slice(1:10) %>% 
  ungroup()
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->




<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudG9wX3BsYXlzICU+JSBcbiAgZGlzdGluY3QoZ2FtZV9pZClcbmBgYCJ9 -->

```r
top_plays %>% 
  distinct(game_id)
```

<!-- rnb-source-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NywibmNvbCI6MSwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyI3IMOXIDEiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTJSMzArRE1CREhEd1lqSTlHWitIZEFOalovdkJMUlpJWVFZOURNcDZZQ0loRUxBYVkrK20vN01qdzZHbTBmV3RyUGZiL0gzZlUrMks3c3JRMEFFekFNM0UwOGd2a1EzemlYQUlhT0Z3ME1tQTNmTHd5ZmNnQndnc3NhQTNOdjRhM0pZa251TmpIeDQxREdIc2ZCZFNUakZRbjlxeUVrNHpWWGI2SkF4bWNrOE1OLzZ1TURQdWZxOEZFV1g1RG82WmFMNVFaTVJ0K3pkaXhlUUN0SFNJcFUwYzZhNnRNVitpTmMramR1ZmQvL3FFbVRrclpxVWp1bEhYVmZHdlRqYmE5WXJLcnVpb3FoU1IvR09WWE1XcU9BK1k0TmxhUk84cnBqYjg1U0NVOXFsZy8vSEY4R3hvSTEva0ovWisxUWhkNlA5dWxvbjJZc0wxZ20yaW5wYzFhS3pHbjJJUWFPOCtEamNPdW1ZSjNvRTJucmRsVkhoY1ZPcWxJUTNqbnNmd0duZlU3MFl3SUFBQT09In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]}],"data":[{"1":"2024_01_PIT_ATL"},{"1":"2024_02_PIT_DEN"},{"1":"2024_03_LAC_PIT"},{"1":"2024_04_PIT_IND"},{"1":"2024_05_DAL_PIT"},{"1":"2024_06_PIT_LV"},{"1":"2024_07_NYJ_PIT"}],"options":{"columns":{"min":{},"max":[10],"total":[1]},"rows":{"min":[10],"max":[10],"total":[7]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


```{=html}

<!-- rnb-html-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInNoaW55LnRhZyJdLCJzaXppbmdQb2xpY3kiOltdfX0= -->

<div id="wlwixtzqcq" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>@import url("https://fonts.googleapis.com/css2?family=Roboto+Condensed:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#wlwixtzqcq table {
  font-family: 'Roboto Condensed', system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#wlwixtzqcq thead, #wlwixtzqcq tbody, #wlwixtzqcq tfoot, #wlwixtzqcq tr, #wlwixtzqcq td, #wlwixtzqcq th {
  border-style: none;
}

#wlwixtzqcq p {
  margin: 0;
  padding: 0;
}

#wlwixtzqcq .gt_table {
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

#wlwixtzqcq .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#wlwixtzqcq .gt_title {
  color: #333333;
  font-size: 60px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#wlwixtzqcq .gt_subtitle {
  color: #333333;
  font-size: 16px;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#wlwixtzqcq .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#wlwixtzqcq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#wlwixtzqcq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 5px;
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

#wlwixtzqcq .gt_col_heading {
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

#wlwixtzqcq .gt_column_spanner_outer {
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

#wlwixtzqcq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#wlwixtzqcq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#wlwixtzqcq .gt_column_spanner {
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

#wlwixtzqcq .gt_spanner_row {
  border-bottom-style: hidden;
}

#wlwixtzqcq .gt_group_heading {
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

#wlwixtzqcq .gt_empty_group_heading {
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

#wlwixtzqcq .gt_from_md > :first-child {
  margin-top: 0;
}

#wlwixtzqcq .gt_from_md > :last-child {
  margin-bottom: 0;
}

#wlwixtzqcq .gt_row {
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

#wlwixtzqcq .gt_stub {
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

#wlwixtzqcq .gt_stub_row_group {
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

#wlwixtzqcq .gt_row_group_first td {
  border-top-width: 2px;
}

#wlwixtzqcq .gt_row_group_first th {
  border-top-width: 2px;
}

#wlwixtzqcq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#wlwixtzqcq .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#wlwixtzqcq .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#wlwixtzqcq .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#wlwixtzqcq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#wlwixtzqcq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#wlwixtzqcq .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#wlwixtzqcq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#wlwixtzqcq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#wlwixtzqcq .gt_footnotes {
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

#wlwixtzqcq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#wlwixtzqcq .gt_sourcenotes {
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

#wlwixtzqcq .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#wlwixtzqcq .gt_left {
  text-align: left;
}

#wlwixtzqcq .gt_center {
  text-align: center;
}

#wlwixtzqcq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#wlwixtzqcq .gt_font_normal {
  font-weight: normal;
}

#wlwixtzqcq .gt_font_bold {
  font-weight: bold;
}

#wlwixtzqcq .gt_font_italic {
  font-style: italic;
}

#wlwixtzqcq .gt_super {
  font-size: 65%;
}

#wlwixtzqcq .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#wlwixtzqcq .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#wlwixtzqcq .gt_indent_1 {
  text-indent: 5px;
}

#wlwixtzqcq .gt_indent_2 {
  text-indent: 10px;
}

#wlwixtzqcq .gt_indent_3 {
  text-indent: 15px;
}

#wlwixtzqcq .gt_indent_4 {
  text-indent: 20px;
}

#wlwixtzqcq .gt_indent_5 {
  text-indent: 25px;
}

#wlwixtzqcq .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#wlwixtzqcq div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>
  <table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_heading">
      <td colspan="11" class="gt_heading gt_title gt_font_normal" style="font-size: 24; font-weight: bold;"><span class='gt_from_md'><strong>Biggest Plays of the Game</strong></span></td>
    </tr>
    <tr class="gt_heading">
      <td colspan="11" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style><span class='gt_from_md'>Plays ranked by absolute value of Expected Points Added<br>Excluding garbage time where win probabilty is .05 &lt; x &lt; .95</span></td>
    </tr>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Possessing team">Possessing team</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Qtr">Qtr</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Time">Time</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Down-Dist">Down-Dist</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Field Pos">Field Pos</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="score">score</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Play">Play</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Description">Description</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="epa">epa</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Win Prob">Win Prob</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: bold;" scope="col" id="Win Prob Change">Win Prob Change</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">3</td>
<td headers="time" class="gt_row gt_right">07:39</td>
<td headers="down_dist" class="gt_row gt_right">2-10</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 23</td>
<td headers="score" class="gt_row gt_right">15-16</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(7:39) (Shotgun) 8-A.Rodgers pass deep left intended for 5-G.Wilson INTERCEPTED by 31-B.Bishop at NYJ 42. 31-B.Bishop to NYJ 1 for 41 yards (17-D.Adams). NYJ-65-X.Newman-Johnson was injured during the play.</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #FFB39B; color: #000000;">−6.50</td>
<td headers="wp" class="gt_row gt_right">42.8%</td>
<td headers="wp_chg" class="gt_row gt_right">34.8%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">2</td>
<td headers="time" class="gt_row gt_right">06:58</td>
<td headers="down_dist" class="gt_row gt_right">2-9</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 40</td>
<td headers="score" class="gt_row gt_right">7-6</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(6:58) (Shotgun) 8-A.Rodgers pass short middle to 20-B.Hall pushed ob at PIT 3 for 57 yards (39-M.Fitzpatrick) [99-L.Ogunjobi].</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #629454; color: #FFFFFF;">4.43</td>
<td headers="wp" class="gt_row gt_right">58.8%</td>
<td headers="wp_chg" class="gt_row gt_right">11.9%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">3</td>
<td headers="time" class="gt_row gt_right">02:42</td>
<td headers="down_dist" class="gt_row gt_right">4-10</td>
<td headers="yrdln" class="gt_row gt_left">PIT 17</td>
<td headers="score" class="gt_row gt_right">15-23</td>
<td headers="play_type" class="gt_row gt_left">FG</td>
<td headers="desc" class="gt_row gt_left">(2:42) 9-G.Zuerlein 35 yard field goal is BLOCKED (94-D.Lowry), Center-42-T.Hennessy, Holder-6-T.Morstead.</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #FFDCCF; color: #000000;">−4.39</td>
<td headers="wp" class="gt_row gt_right">18.9%</td>
<td headers="wp_chg" class="gt_row gt_right">66.9%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">3</td>
<td headers="time" class="gt_row gt_right">12:02</td>
<td headers="down_dist" class="gt_row gt_right">3-7</td>
<td headers="yrdln" class="gt_row gt_left">PIT 24</td>
<td headers="score" class="gt_row gt_right">15-13</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(12:02) (No Huddle, Shotgun) 3-R.Wilson pass deep right to 14-G.Pickens to NYJ 39 for 37 yards (23-I.Oliver).</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #6F9D61; color: #FFFFFF;">3.86</td>
<td headers="wp" class="gt_row gt_right">44.8%</td>
<td headers="wp_chg" class="gt_row gt_right">12.9%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">2</td>
<td headers="time" class="gt_row gt_right">11:35</td>
<td headers="down_dist" class="gt_row gt_right">2-17</td>
<td headers="yrdln" class="gt_row gt_left">PIT 24</td>
<td headers="score" class="gt_row gt_right">7-3</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(11:35) 3-R.Wilson pass deep left to 14-G.Pickens to NYJ 32 for 44 yards (26-B.Echols).</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #729E64; color: #FFFFFF;">3.73</td>
<td headers="wp" class="gt_row gt_right">35.4%</td>
<td headers="wp_chg" class="gt_row gt_right">12.5%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">2</td>
<td headers="time" class="gt_row gt_right">00:32</td>
<td headers="down_dist" class="gt_row gt_right">2-10</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 11</td>
<td headers="score" class="gt_row gt_right">15-12</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(:32) (No Huddle, Shotgun) 3-R.Wilson pass short right to 14-G.Pickens for 11 yards, TOUCHDOWN.</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #80A873; color: #FFFFFF;">3.09</td>
<td headers="wp" class="gt_row gt_right">30.3%</td>
<td headers="wp_chg" class="gt_row gt_right">6.5%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">2</td>
<td headers="time" class="gt_row gt_right">01:21</td>
<td headers="down_dist" class="gt_row gt_right">2-4</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 36</td>
<td headers="score" class="gt_row gt_right">15-6</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(1:21) (Shotgun) 8-A.Rodgers pass deep middle intended for 5-G.Wilson INTERCEPTED by 31-B.Bishop at PIT 46. 31-B.Bishop to PIT 46 for no gain (5-G.Wilson).</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #FFFAF8; color: #000000;">−2.78</td>
<td headers="wp" class="gt_row gt_right">84.0%</td>
<td headers="wp_chg" class="gt_row gt_right">58.6%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">3</td>
<td headers="time" class="gt_row gt_right">03:36</td>
<td headers="down_dist" class="gt_row gt_right">4-1</td>
<td headers="yrdln" class="gt_row gt_left">PIT 32</td>
<td headers="score" class="gt_row gt_right">15-23</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(3:36) (Shotgun) 8-A.Rodgers pass short middle to 18-M.Williams to PIT 17 for 15 yards (25-D.Elliott) [99-L.Ogunjobi].</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #87AD7B; color: #FFFFFF;">2.76</td>
<td headers="wp" class="gt_row gt_right">18.6%</td>
<td headers="wp_chg" class="gt_row gt_right">8.3%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">4</td>
<td headers="time" class="gt_row gt_right">12:13</td>
<td headers="down_dist" class="gt_row gt_right">3-4</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 4</td>
<td headers="score" class="gt_row gt_right">15-29</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(12:13) (Shotgun) 3-R.Wilson pass short right to 11-V.Jefferson for 4 yards, TOUCHDOWN.</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #8EB283; color: #000000;">2.44</td>
<td headers="wp" class="gt_row gt_right">93.5%</td>
<td headers="wp_chg" class="gt_row gt_right">3.2%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_left"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_right">3</td>
<td headers="time" class="gt_row gt_right">10:08</td>
<td headers="down_dist" class="gt_row gt_right">3-5</td>
<td headers="yrdln" class="gt_row gt_left">NYJ 34</td>
<td headers="score" class="gt_row gt_right">15-13</td>
<td headers="play_type" class="gt_row gt_left">Pass</td>
<td headers="desc" class="gt_row gt_left">(10:08) (Shotgun) 3-R.Wilson pass deep right to 88-P.Freiermuth to NYJ 13 for 21 yards (35-J.Mills).</td>
<td headers="epa" class="gt_row gt_right" style="background-color: #90B384; color: #000000;">2.38</td>
<td headers="wp" class="gt_row gt_right">55.7%</td>
<td headers="wp_chg" class="gt_row gt_right">7.4%</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="11">Replicating work done by Kevin Cole in the Unexpected Points Substack newsletter</td>
    </tr>
  </tfoot>
  
</table>
</div>


<!-- rnb-html-end -->

```

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjQgJT4lIFxuICBmaWx0ZXIoZXBhID09IG1pbl9lcGEpXG5cbmBgYCJ9 -->

```r
play_by_play_2024 %>% 
  filter(epa == min_epa)

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoi4pSA4pSAIG5mbHZlcnNlIHBsYXkgYnkgcGxheSBkYXRhIOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgFxu4oS5IERhdGEgdXBkYXRlZDogMjAyNC0xMC0yMSAwNToyMTozNCBFRFRcbiJ9 -->

```
── nflverse play by play data ──────────────────────────────────────────────────────────────────────────────────────────
ℹ Data updated: 2024-10-21 05:21:34 EDT
```



<!-- rnb-output-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbIm5mbHZlcnNlX2RhdGEiLCJ0YmxfZGYiLCJ0YmwiLCJkYXRhLnRhYmxlIiwiZGF0YS5mcmFtZSJdLCJucm93IjoxLCJuY29sIjozNzIsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMSDDlyAzNzIiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBKzBkVzJ3Y1YzWGoyRjU3L1ZxL0U2ZVVhUlFFRmZGMmQ3MSt4QkxZYldNM1Vkc2tKR21hRnFISmVPZU9kL0I2Wmpzem00MzdRZk1GZ2c5VXRmQ0hCQ28vcFI5UVVSNFNVQ1dnU2pUS0IxQkF0RkNrQWhJdEVoOFZoWThXS053N00vZk91WGZ1N0NZMEZTcU1wY1I3M3VlZWUrNzdaSFB5OE5tNTNObGNKcFBabmVudXhuLzM0SStabnZ0T3I4OHVaVExkWFJqWWxlbk85SlBmRnpCNUhQLzJNREJNRUt1UGZTVVQvdVFCNDNDNVdLNm94WG4xbmpQcTRiVmpBalZIcUtWaWNhRzRLRkIyeDVtNzdqa2pNcDFjdXd2L0d2SlIyTk9PQXQxYVM5dnBiQ2xFQmUyYW9NMktlejViS3M0V0Z4am54UmNwcHh4K1lsMm1xZWVJVmpkS2xDa1QvWWptZlhqbGRZR2VTYVRUc093U0RSYVhsdWNQaVVqY1pHVSt5ZXJxQ1drUVB2TWhvdWxXcFRRL2UxZmhYdE55YTZpbE5EVFhWZHlhN1hoS0hSbWVZbG9lc25Ta0s0YnRLRXVIWnU4bzNHRzNrT01xUjQrZFhqdDU1OXFKMDJ1SGxZMGRwVHg3b25DcTZYaWFhU21hcHhCL2lnVU9TeFRnWkZGMk5FZDNEeXFuajk5MzU1SER4KzgvVmhEYzZpWXVKQVcwRXl3RytEcmt1WGo2RVJBZEl3RkppdkVqdnVIc0Uwd21rK24vRi82NUJ2aDY1YVdaczlyWG9XR2l2c1RoMDgrNlRDRGtpbmk4Rk9jV2xoWXJTVlpqWHUwWDRBTWRZRkhmVFIzNEJmMWk5Njk4Y2Jyd0NvUS9lL1VqQ29RclQyMWVodkRqZjc3RXlUOWZ1OExSYjMvalFZNysybTAyMUJjMVAyRSttUHJoVjkvNFpnUmZ2dlhjejk1OEtZSXYvZkhtbm85L2Z1dzVwbCtBTDQvOC9qdFgzd0w2UkxqN3VlZWJWNTh0TW40Qlh2bnJtNDNTRXJCL3NMMi9NZit6VDdkZVhnZnlJcnoveEFzZmZQSFJiekYrQVY3NTV3TkRMeHdBN1JYZzFWMzJsN1ZQQVA4RmVPVlB3eCs5Q09OLzljZTltWGF3d0gvcGw4KzhmYURuWTA4eStPZS8vZjZ6Wi9vbkdMOEkvKzdxNWNlNm52d0ZnMSt1ZmVvM2IzMzlMSU5mL2Q1ZnprRjdQLzNjdmxWbzc5S1gvczc1SThKUHZQUzNOMC85NUJYR0w4QmkvRVgvTy9YWHBVZCswQWZoRlFHK2RHWGcwMWUrL1kyb1BRTGNTWDdsdTFkdStjZlhYbjJkOFF0d0ovLysyL0E3V0M1UytGMkk5L1gyeC85US8rVXpzWlYydnJ3a2J2VDYyVTZOcW9odEhEZ1ZoK2JtbGdSS0g5M0NKV3E0d1Z1VmQ1RmYwdUp3ZThJRkxiNmp1ZmJkV1FxbjhQOFRmRzJuaHhzTnY2ZUg4SDgyYTkwNCtYZXpTN2pMbEFjeTlPZWROdkY2cyt6R3JLN0orc1BibHV4clZIYmwxODlzblFPNkxoOSsrY04vQVBCcXNZT3RJSHhEeHhzTnhiT2IxWnB1dHl3bUxMOXRHeTBWYjF1NHJWdzVxSlFXbG92enkrVUZnV0ZQZEcxMXVseGNuaTh0bDRxRmhkTGlnd0xmek5wMmd5enh5cnFKNmpxNWo3blhyQ1BsaUxsWmk5cCtrWEFXVHpVdGEwYzVqYllieThyaTNJK2VWdFlQS2tlYTI2WnVlanZMU3JuOGdZUEsvYWFsTHl2SGxFVmx1MUVUTEIxWTFDdkZxcjZvelpibVN1WFpVZ2taczVxaGwyWVhLZ3ZGNGlHanRMUlJSb0xNcm1LSG9BMnl1NldqeDQ4bDhzcnpOUjZpOGtKaHZsSjhVQ0lYOUlYOGhqRFdjVzJNVkJhWGk2WEN3aUhmU0tCMGoxUnA5OXh5aFRWZXZPdUkzVjBJOEdxbVBad1F6T3pkUisrOCsvajZlb2NZUTFwUHFieGNuaE9SeGFYbFNneDV6eGxscmlRaStjdklSOC95YmtlNVQ2ODR4OERuL1dMSWp0amJDTkR6NEhQeU5kUWRERTY2UnUyem01NXUyLzR1bUhOKzB3bXVINm5nVWZBNUt6QVBuRUthcFp6UWRqeGJUSkhoMnkyTU5HM2xoSW1jcWpnRVNJaUt4Y3oxak5yck9UOE1SdmU1UjZIL0k1bUVtZTlpWEFjOEpsRDVCeklKdWRuR3IwN25ObWhUZHU1cHUxT1FIRzg2dDczVEdRdTIvTnBzWHB2RU5VVkd2QkVVMTB3QXc1N3J4QnRFL1ZkZmVPMGM0Rjg5L3ZoVFRSL2tYb2Q2TEcwYmhVM1o1ZEZwcEZIWGRsUlRwK0FtNW9uQUFidXVxenlxdjRZSHJ1b2hiWnNpeU9zTlJBeTRTSE50Uy9WMkdvaU85aFpDVzh5aTdRTHV3UkNFN0ZrZEdZQmx5RFYxcE5xR2FwQUJST1hJZTBQZHRKQmF3aU11ZE1WM1ZkYzhxbWp2UTAzTjhaQ2p1cWhxVzdxck9tZ2I3elZOYXpOa21LcHBkU09aNnV0TG9nYldpQUxhY0dvTldkVExIdDB4ejFOdnV0d0czWDA5NURrME5QNDZGT2JWcHEzVlZjOVdOMjFLOWN4dEt0NnpneHRNV2JNN3V1dlpqSzhYZ3hieW1FN2tWcW1YZmdlRDRQcUJjM0d2NHRpeGJuZHJ0cmZacE1yN0xWdXROWFc5amxqTE5sVGRzUnNiV3BWMll4OUdiVmtJMVFIc05zd3RLT0pXSFcxN0k5SkNYb0RVT3JJMnZScnQyZ0JsVnpYUHRKbDV6WFJVMzB1NmdRcGMxZ3dTWE14YXBlS0RUdE1TcGJNRXQ2blJVSS82U2FQNmtYV1EyNnpUSUExdG1kVXRWVGRkVDdPcTFNVXhkTUZ6TkxWaG01YkhzMDk2TFR2RTQzUTR6eE9uZzBHQit3b3ZQL0ZNbVE2R1NCSTVHMUpvbzBJUWpxbXNwME53R0lPa1gzRTR5S0JtZ2d6TGh1c01HMTVKMW1mQ3daYk1rZmRzRDBmUGI2TmJ0UjNFNC8zR1Fmd1F0Y2tocVJtSUhQTUIzQW1HZ1J4a2VhWkcwMm1NMDZFU2lGSTRSWkF5SGRjR3lVTTRxME1aeDk1Z00xeWpvUnFiRURWQ1VLNW1JRzhueGtraUhLR3l2T0JBWENqTEMrUmhlZ0g4WGo2NThJcUQ4eGt5ZENFMmRhQ0d4cklnNnBjWTF1K1ZDRHNPZUoybVc0dVRmQUU1eVpmeVI2cGNTaUJseWZnRjRJNVdCZUJnMWQ1dXFEeExnT1A1cG9GdGljZzBzSjlNanFTbHlpTnBuandGbzZXMUJOMVRNR0JKVkNZcjFjeGtlV3BYaTNaekw4NXlsVUZaWDFzRSt1SU0zTjFpQ3ZyUG8wM05WU1BFY0lBSTVWbThReGdPajhGUUtjVDFVWFYwQ0hIYWtsS3JsWnhhTVZLVVduSXBnZVNuVm90UHJaWWt0VVFjenlkTnJSaVpUNjAyMGxMbGZHcTEycVpXak1xbFZyS3NWRE9YV2lBT2pTYWVYVGJ3WXJuRmx2MFJ3M1JjVHlVN0VMOTdKR2kvYUNPY2VDRWFXVnJkMndrcEUxN05kUFNBRXN4ZkhyTXhDbWlHaGc4K2xEQnAyRTNIcThtbHhpQ1JFeHN4TFJMVk92SVFkSzdmUDlPRC9ja2dxWERCSjdRRzJCcU0rVEhBcHdpeW4vUmFlSW1nTFJnSktXVHI5ckJ0SVU2QXJNVjQ5N2xoTnkyMkpSbndLY1M5eURNZlpaQXVnM3VVU2JMUHNBMURhbmNzSWdxbW1aak0rakFsY2c0d1pURWZob3dtMlllcGhvMGp3bm9tUkZxMnh4TW1Rb0swM2E1ZHQxVVB4NWx0NjNxRFpZOE9TVDQxOGdHclRpemduUnJycjRIUVJqMmFiQ1pJWDlNbU9IalRqVE9DcXBtVzBmQnFURjNBbTgyYXlXWXlmNnJSUEE5dE54ak9uMGg0WExjYnBVdC9kQ2NVaHRnWGlHRjkxU0kyN3lDdjZWZ3gvRGhjN25uYm85R0t6eFBHd0g2VnA0elE5b3N0YThhVTlBYlJwYjB2R3pCRCtDUGUrL0pkT1ZySFp5ZkgzeW56STJlUUVhSnBZamhpSnEybnNRQXFZQS9taVcyOE14VTNxR004SG14bi9iTUIzb1Z5UjRFeDRoaytVc1VWVFlnVW9Hb2tvSW5LOHFRMU1wOTRQUFNKVUVRMU16QnFVdDl1U3VJQXFxZDVIdEhJSHRnREVoTXpjam93TUFrNVJQVlRsRWpHUkV6NUhoa1ZxSjZDazIxY1drWUYwamRUN1cyMUtPMjRZQno5OFJEa3BDUk9lNlZrSVA5K2FxZTlubHZhc2dGOU4wWFRWaUxQVEJJUE03ZWZtdXZJZWFBVEo3Q2JKODVMQnlXSEJ4TCtHaVBYeFZPWXJwdWxVM2VzZDl0eEFTdWo0UTRtcG1CY0lBQ1pmY0VjeDVZZ3RSU1RmbDhpU3pzOTVjNTZ5cklZQnF1VnhJMEprU0tSaWh1ZEVDblE1MkJsVjhQbE5tUW93Y3NFSllFbGxvTHQrVG9hTFhjMkdtK2IzS2cwcW1CbndqZVFvM0JlVFBNeW92RnBYakEybFVpbGdVdDdwZktRZ1Z1RUpSN3NTMkFBT2laRUZ0QStRWCs4Q2ZzU0dKTDFsOXZvbit1a2Y2NnovcmsyK2l1ZDlGYzY2Njl3bVJFaVd5WSthd1I4ZE5hS1V5VGRvN1RqZ3YwczVRT095TXpGZTB0bVRwcFdVajVnYm8rL3VkV1JnU3hYbG5ZemNqb3d3V3VJdXpvanB3TU53OEdRMXZsQWpFZFlVZVZrakFTME1ibTRLNU14a3N3TExqNVQ0WFRERmlMT3grazRGVzZsOXNYSnNXVWlrUVZ1cWtTbWNsc255dTJka0t4VmlTd3dQdEw5WUQ1aEh6Z1pQS2NRb21RMmxSRGxzbkZmcHlWRUlEdEFEMkRnWFNsRXdhQU1obWRUeURkS2NiRU5oVURnVGlZaENTb2ZkNUQvMUlKWC9pcjJsanh6c08yZGhNUS9JRVNlUlE4MSs0TFJnNDhMYXRKaGNZK01oZHlsMEM2TzZNbEgwUms1RTFBelJpKzI0NXMrbnNLQzF4dThBWVpRVjVYZUZYWlhHM1owYjRBY0U3RXJqUUJTM1dhMWlxSlRhb2psZ2pWc083ci9wdmRRRTBWUE56blgweHhQQlE5bUErUXp1Y0hRTlhZN2dabDBzOG1lVlZwSTgvQnBpYXF3REh6b2JwaFJPM0ordjFYSjFwTDFGTUhvaUp5bmRaWVA5STFOeFJwWTBCcW9TcDRnU0xLNWZvU29DandkaTY5eXc4alNBenV3QlVNRVM1Sk1KUytkdEZtR2VRRlBXUEJsY1F5Z2hHY3JpaU9ITnpGQStZQVl0TkhHVzM2V1ZqNmVocStCTjdLNFM2TGJnTkdBSHQwSHNrNE1DTUZOVjVrK3kwNEZXUC9mbXdWckVud0RHZytvN0tXV09NbmJpVCtyaHEwS25nWDlvV00rekhvak5CZTIxdEd3TStBbVk0STVFNmVGa3Y2N2J0QVgwSnVKR0RYbVVHQlQ3TER4eUtSSW1nUTlZT3FCUEd2SU9FLzA0MGZ6TXZib2xvczl6L1VKRDZPOVhHTDArTGZGTktYY0JzNFF6ck5jY0pzTU1IMjZlZDV2UFIzTGptM1RwKytzMjNRTWpZM0ZiaksvME04dGs0VXBGMTZhYSt4bU1oZmVrd05NT0VTalFUZ1lQTU56STNkUTI3QkpxT0M0eXZKelIyOXdzMFI3TDd4bitpUnlYTFNqV25qdFk3VGU0TTZFY29ZM0tETE9QbnFCUXpPR1hlakl1THZCZlZzM3VEbkxSU09IdVI1TUZrd3dhbFYvNkhoVWdSSDZGMVZwTUNjWXFodXVWakxYdXFKMXp0QXNUM09saDIyQkZKV0poQVRXbnBDUE1Reko3bzRuL042MzhYZ2x0MC9oWVo5MkFUN0RSdTlnZlJmNGQ3RlJIOTVHV3JDZWEyeGxIUThKdWhrakRmb2tQaVd5UHM1ZzFSa1hRQWRsL1IwclhwMzRxcGwreDI0VmFPVU1LYzNwdW9qL0NrcVhPTVl4UFBXVGw5dGczc1RaaWtjQVh6WTBUY3NMeXlXRmxJR1dsdWNxeXRyaDA0S2lvVWdSV1IrRVdsTFNGZVFmNXZxL2RjM1RCT2s4bGpZMDF6dXBocy9JZ29KY3BiQlFLQlVPRlV1TGd1Um93YjladzVOcHdVVjF3MEVHU2ZEd3o5dmhuM3hhTzVUV0RxVzFRMm50VU1DUjFnNmx0VU5wN1ZCYU81VFdEclZMcmJSMktLMGRTbXVIMHRxaHRIWW9yUjFLYTRmUzJxRzBkaWl0SFVwcmg5TGFvYlIyS0swZFNtdUgwdHFodEhZb2s5WU9wYlZEOUFDYTFnNmx0VU5wN1JEWHdyUjJLSzBkQ3B1WTFnNjlaMnFIZXFyMTRFdW44Z0NaSTBVN0JjUFIvTysvZWxzUXlkciszUlFXNmhvblRST0VkemtDSXQrMFNORDEyV3F0YVczTkxvcGZMYmU3WVcwU281bm9PNG5nVjJlRm44bC9HRUhjNktMZng5UkxRNHUzRzlFbzdxbHJHNnhvWTdlTzZCby83T0JzSkNWU2hZWmpzcFVnaDdGdUFVNFZ1YXBkcDVpd3BPamZLNkQyVk41aUFBQT0ifQ== -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["play_id"],"name":[1],"type":["dbl"],"align":["right"]},{"label":["game_id"],"name":[2],"type":["chr"],"align":["left"]},{"label":["old_game_id"],"name":[3],"type":["chr"],"align":["left"]},{"label":["home_team"],"name":[4],"type":["chr"],"align":["left"]},{"label":["away_team"],"name":[5],"type":["chr"],"align":["left"]},{"label":["season_type"],"name":[6],"type":["chr"],"align":["left"]},{"label":["week"],"name":[7],"type":["int"],"align":["right"]},{"label":["posteam"],"name":[8],"type":["chr"],"align":["left"]},{"label":["posteam_type"],"name":[9],"type":["chr"],"align":["left"]},{"label":["defteam"],"name":[10],"type":["chr"],"align":["left"]},{"label":["side_of_field"],"name":[11],"type":["chr"],"align":["left"]},{"label":["yardline_100"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["game_date"],"name":[13],"type":["chr"],"align":["left"]},{"label":["quarter_seconds_remaining"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["half_seconds_remaining"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["game_seconds_remaining"],"name":[16],"type":["dbl"],"align":["right"]},{"label":["game_half"],"name":[17],"type":["chr"],"align":["left"]},{"label":["quarter_end"],"name":[18],"type":["dbl"],"align":["right"]},{"label":["drive"],"name":[19],"type":["dbl"],"align":["right"]},{"label":["sp"],"name":[20],"type":["dbl"],"align":["right"]},{"label":["qtr"],"name":[21],"type":["dbl"],"align":["right"]},{"label":["down"],"name":[22],"type":["dbl"],"align":["right"]},{"label":["goal_to_go"],"name":[23],"type":["int"],"align":["right"]},{"label":["time"],"name":[24],"type":["chr"],"align":["left"]},{"label":["yrdln"],"name":[25],"type":["chr"],"align":["left"]},{"label":["ydstogo"],"name":[26],"type":["dbl"],"align":["right"]},{"label":["ydsnet"],"name":[27],"type":["dbl"],"align":["right"]},{"label":["desc"],"name":[28],"type":["chr"],"align":["left"]},{"label":["play_type"],"name":[29],"type":["chr"],"align":["left"]},{"label":["yards_gained"],"name":[30],"type":["dbl"],"align":["right"]},{"label":["shotgun"],"name":[31],"type":["dbl"],"align":["right"]},{"label":["no_huddle"],"name":[32],"type":["dbl"],"align":["right"]},{"label":["qb_dropback"],"name":[33],"type":["dbl"],"align":["right"]},{"label":["qb_kneel"],"name":[34],"type":["dbl"],"align":["right"]},{"label":["qb_spike"],"name":[35],"type":["dbl"],"align":["right"]},{"label":["qb_scramble"],"name":[36],"type":["dbl"],"align":["right"]},{"label":["pass_length"],"name":[37],"type":["chr"],"align":["left"]},{"label":["pass_location"],"name":[38],"type":["chr"],"align":["left"]},{"label":["air_yards"],"name":[39],"type":["dbl"],"align":["right"]},{"label":["yards_after_catch"],"name":[40],"type":["dbl"],"align":["right"]},{"label":["run_location"],"name":[41],"type":["chr"],"align":["left"]},{"label":["run_gap"],"name":[42],"type":["chr"],"align":["left"]},{"label":["field_goal_result"],"name":[43],"type":["chr"],"align":["left"]},{"label":["kick_distance"],"name":[44],"type":["dbl"],"align":["right"]},{"label":["extra_point_result"],"name":[45],"type":["chr"],"align":["left"]},{"label":["two_point_conv_result"],"name":[46],"type":["chr"],"align":["left"]},{"label":["home_timeouts_remaining"],"name":[47],"type":["dbl"],"align":["right"]},{"label":["away_timeouts_remaining"],"name":[48],"type":["dbl"],"align":["right"]},{"label":["timeout"],"name":[49],"type":["dbl"],"align":["right"]},{"label":["timeout_team"],"name":[50],"type":["chr"],"align":["left"]},{"label":["td_team"],"name":[51],"type":["chr"],"align":["left"]},{"label":["td_player_name"],"name":[52],"type":["chr"],"align":["left"]},{"label":["td_player_id"],"name":[53],"type":["chr"],"align":["left"]},{"label":["posteam_timeouts_remaining"],"name":[54],"type":["dbl"],"align":["right"]},{"label":["defteam_timeouts_remaining"],"name":[55],"type":["dbl"],"align":["right"]},{"label":["total_home_score"],"name":[56],"type":["dbl"],"align":["right"]},{"label":["total_away_score"],"name":[57],"type":["dbl"],"align":["right"]},{"label":["posteam_score"],"name":[58],"type":["dbl"],"align":["right"]},{"label":["defteam_score"],"name":[59],"type":["dbl"],"align":["right"]},{"label":["score_differential"],"name":[60],"type":["dbl"],"align":["right"]},{"label":["posteam_score_post"],"name":[61],"type":["dbl"],"align":["right"]},{"label":["defteam_score_post"],"name":[62],"type":["dbl"],"align":["right"]},{"label":["score_differential_post"],"name":[63],"type":["dbl"],"align":["right"]},{"label":["no_score_prob"],"name":[64],"type":["dbl"],"align":["right"]},{"label":["opp_fg_prob"],"name":[65],"type":["dbl"],"align":["right"]},{"label":["opp_safety_prob"],"name":[66],"type":["dbl"],"align":["right"]},{"label":["opp_td_prob"],"name":[67],"type":["dbl"],"align":["right"]},{"label":["fg_prob"],"name":[68],"type":["dbl"],"align":["right"]},{"label":["safety_prob"],"name":[69],"type":["dbl"],"align":["right"]},{"label":["td_prob"],"name":[70],"type":["dbl"],"align":["right"]},{"label":["extra_point_prob"],"name":[71],"type":["dbl"],"align":["right"]},{"label":["two_point_conversion_prob"],"name":[72],"type":["dbl"],"align":["right"]},{"label":["ep"],"name":[73],"type":["dbl"],"align":["right"]},{"label":["epa"],"name":[74],"type":["dbl"],"align":["right"]},{"label":["total_home_epa"],"name":[75],"type":["dbl"],"align":["right"]},{"label":["total_away_epa"],"name":[76],"type":["dbl"],"align":["right"]},{"label":["total_home_rush_epa"],"name":[77],"type":["dbl"],"align":["right"]},{"label":["total_away_rush_epa"],"name":[78],"type":["dbl"],"align":["right"]},{"label":["total_home_pass_epa"],"name":[79],"type":["dbl"],"align":["right"]},{"label":["total_away_pass_epa"],"name":[80],"type":["dbl"],"align":["right"]},{"label":["air_epa"],"name":[81],"type":["dbl"],"align":["right"]},{"label":["yac_epa"],"name":[82],"type":["dbl"],"align":["right"]},{"label":["comp_air_epa"],"name":[83],"type":["dbl"],"align":["right"]},{"label":["comp_yac_epa"],"name":[84],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_air_epa"],"name":[85],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_air_epa"],"name":[86],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_yac_epa"],"name":[87],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_yac_epa"],"name":[88],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_air_epa"],"name":[89],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_air_epa"],"name":[90],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_yac_epa"],"name":[91],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_yac_epa"],"name":[92],"type":["dbl"],"align":["right"]},{"label":["wp"],"name":[93],"type":["dbl"],"align":["right"]},{"label":["def_wp"],"name":[94],"type":["dbl"],"align":["right"]},{"label":["home_wp"],"name":[95],"type":["dbl"],"align":["right"]},{"label":["away_wp"],"name":[96],"type":["dbl"],"align":["right"]},{"label":["wpa"],"name":[97],"type":["dbl"],"align":["right"]},{"label":["vegas_wpa"],"name":[98],"type":["dbl"],"align":["right"]},{"label":["vegas_home_wpa"],"name":[99],"type":["dbl"],"align":["right"]},{"label":["home_wp_post"],"name":[100],"type":["dbl"],"align":["right"]},{"label":["away_wp_post"],"name":[101],"type":["dbl"],"align":["right"]},{"label":["vegas_wp"],"name":[102],"type":["dbl"],"align":["right"]},{"label":["vegas_home_wp"],"name":[103],"type":["dbl"],"align":["right"]},{"label":["total_home_rush_wpa"],"name":[104],"type":["dbl"],"align":["right"]},{"label":["total_away_rush_wpa"],"name":[105],"type":["dbl"],"align":["right"]},{"label":["total_home_pass_wpa"],"name":[106],"type":["dbl"],"align":["right"]},{"label":["total_away_pass_wpa"],"name":[107],"type":["dbl"],"align":["right"]},{"label":["air_wpa"],"name":[108],"type":["dbl"],"align":["right"]},{"label":["yac_wpa"],"name":[109],"type":["dbl"],"align":["right"]},{"label":["comp_air_wpa"],"name":[110],"type":["dbl"],"align":["right"]},{"label":["comp_yac_wpa"],"name":[111],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_air_wpa"],"name":[112],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_air_wpa"],"name":[113],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_yac_wpa"],"name":[114],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_yac_wpa"],"name":[115],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_air_wpa"],"name":[116],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_air_wpa"],"name":[117],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_yac_wpa"],"name":[118],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_yac_wpa"],"name":[119],"type":["dbl"],"align":["right"]},{"label":["punt_blocked"],"name":[120],"type":["dbl"],"align":["right"]},{"label":["first_down_rush"],"name":[121],"type":["dbl"],"align":["right"]},{"label":["first_down_pass"],"name":[122],"type":["dbl"],"align":["right"]},{"label":["first_down_penalty"],"name":[123],"type":["dbl"],"align":["right"]},{"label":["third_down_converted"],"name":[124],"type":["dbl"],"align":["right"]},{"label":["third_down_failed"],"name":[125],"type":["dbl"],"align":["right"]},{"label":["fourth_down_converted"],"name":[126],"type":["dbl"],"align":["right"]},{"label":["fourth_down_failed"],"name":[127],"type":["dbl"],"align":["right"]},{"label":["incomplete_pass"],"name":[128],"type":["dbl"],"align":["right"]},{"label":["touchback"],"name":[129],"type":["dbl"],"align":["right"]},{"label":["interception"],"name":[130],"type":["dbl"],"align":["right"]},{"label":["punt_inside_twenty"],"name":[131],"type":["dbl"],"align":["right"]},{"label":["punt_in_endzone"],"name":[132],"type":["dbl"],"align":["right"]},{"label":["punt_out_of_bounds"],"name":[133],"type":["dbl"],"align":["right"]},{"label":["punt_downed"],"name":[134],"type":["dbl"],"align":["right"]},{"label":["punt_fair_catch"],"name":[135],"type":["dbl"],"align":["right"]},{"label":["kickoff_inside_twenty"],"name":[136],"type":["dbl"],"align":["right"]},{"label":["kickoff_in_endzone"],"name":[137],"type":["dbl"],"align":["right"]},{"label":["kickoff_out_of_bounds"],"name":[138],"type":["dbl"],"align":["right"]},{"label":["kickoff_downed"],"name":[139],"type":["dbl"],"align":["right"]},{"label":["kickoff_fair_catch"],"name":[140],"type":["dbl"],"align":["right"]},{"label":["fumble_forced"],"name":[141],"type":["dbl"],"align":["right"]},{"label":["fumble_not_forced"],"name":[142],"type":["dbl"],"align":["right"]},{"label":["fumble_out_of_bounds"],"name":[143],"type":["dbl"],"align":["right"]},{"label":["solo_tackle"],"name":[144],"type":["dbl"],"align":["right"]},{"label":["safety"],"name":[145],"type":["dbl"],"align":["right"]},{"label":["penalty"],"name":[146],"type":["dbl"],"align":["right"]},{"label":["tackled_for_loss"],"name":[147],"type":["dbl"],"align":["right"]},{"label":["fumble_lost"],"name":[148],"type":["dbl"],"align":["right"]},{"label":["own_kickoff_recovery"],"name":[149],"type":["dbl"],"align":["right"]},{"label":["own_kickoff_recovery_td"],"name":[150],"type":["dbl"],"align":["right"]},{"label":["qb_hit"],"name":[151],"type":["dbl"],"align":["right"]},{"label":["rush_attempt"],"name":[152],"type":["dbl"],"align":["right"]},{"label":["pass_attempt"],"name":[153],"type":["dbl"],"align":["right"]},{"label":["sack"],"name":[154],"type":["dbl"],"align":["right"]},{"label":["touchdown"],"name":[155],"type":["dbl"],"align":["right"]},{"label":["pass_touchdown"],"name":[156],"type":["dbl"],"align":["right"]},{"label":["rush_touchdown"],"name":[157],"type":["dbl"],"align":["right"]},{"label":["return_touchdown"],"name":[158],"type":["dbl"],"align":["right"]},{"label":["extra_point_attempt"],"name":[159],"type":["dbl"],"align":["right"]},{"label":["two_point_attempt"],"name":[160],"type":["dbl"],"align":["right"]},{"label":["field_goal_attempt"],"name":[161],"type":["dbl"],"align":["right"]},{"label":["kickoff_attempt"],"name":[162],"type":["dbl"],"align":["right"]},{"label":["punt_attempt"],"name":[163],"type":["dbl"],"align":["right"]},{"label":["fumble"],"name":[164],"type":["dbl"],"align":["right"]},{"label":["complete_pass"],"name":[165],"type":["dbl"],"align":["right"]},{"label":["assist_tackle"],"name":[166],"type":["dbl"],"align":["right"]},{"label":["lateral_reception"],"name":[167],"type":["dbl"],"align":["right"]},{"label":["lateral_rush"],"name":[168],"type":["dbl"],"align":["right"]},{"label":["lateral_return"],"name":[169],"type":["dbl"],"align":["right"]},{"label":["lateral_recovery"],"name":[170],"type":["dbl"],"align":["right"]},{"label":["passer_player_id"],"name":[171],"type":["chr"],"align":["left"]},{"label":["passer_player_name"],"name":[172],"type":["chr"],"align":["left"]},{"label":["passing_yards"],"name":[173],"type":["dbl"],"align":["right"]},{"label":["receiver_player_id"],"name":[174],"type":["chr"],"align":["left"]},{"label":["receiver_player_name"],"name":[175],"type":["chr"],"align":["left"]},{"label":["receiving_yards"],"name":[176],"type":["dbl"],"align":["right"]},{"label":["rusher_player_id"],"name":[177],"type":["chr"],"align":["left"]},{"label":["rusher_player_name"],"name":[178],"type":["chr"],"align":["left"]},{"label":["rushing_yards"],"name":[179],"type":["dbl"],"align":["right"]},{"label":["lateral_receiver_player_id"],"name":[180],"type":["chr"],"align":["left"]},{"label":["lateral_receiver_player_name"],"name":[181],"type":["chr"],"align":["left"]},{"label":["lateral_receiving_yards"],"name":[182],"type":["dbl"],"align":["right"]},{"label":["lateral_rusher_player_id"],"name":[183],"type":["chr"],"align":["left"]},{"label":["lateral_rusher_player_name"],"name":[184],"type":["chr"],"align":["left"]},{"label":["lateral_rushing_yards"],"name":[185],"type":["dbl"],"align":["right"]},{"label":["lateral_sack_player_id"],"name":[186],"type":["chr"],"align":["left"]},{"label":["lateral_sack_player_name"],"name":[187],"type":["chr"],"align":["left"]},{"label":["interception_player_id"],"name":[188],"type":["chr"],"align":["left"]},{"label":["interception_player_name"],"name":[189],"type":["chr"],"align":["left"]},{"label":["lateral_interception_player_id"],"name":[190],"type":["chr"],"align":["left"]},{"label":["lateral_interception_player_name"],"name":[191],"type":["chr"],"align":["left"]},{"label":["punt_returner_player_id"],"name":[192],"type":["chr"],"align":["left"]},{"label":["punt_returner_player_name"],"name":[193],"type":["chr"],"align":["left"]},{"label":["lateral_punt_returner_player_id"],"name":[194],"type":["chr"],"align":["left"]},{"label":["lateral_punt_returner_player_name"],"name":[195],"type":["chr"],"align":["left"]},{"label":["kickoff_returner_player_name"],"name":[196],"type":["chr"],"align":["left"]},{"label":["kickoff_returner_player_id"],"name":[197],"type":["chr"],"align":["left"]},{"label":["lateral_kickoff_returner_player_id"],"name":[198],"type":["chr"],"align":["left"]},{"label":["lateral_kickoff_returner_player_name"],"name":[199],"type":["chr"],"align":["left"]},{"label":["punter_player_id"],"name":[200],"type":["chr"],"align":["left"]},{"label":["punter_player_name"],"name":[201],"type":["chr"],"align":["left"]},{"label":["kicker_player_name"],"name":[202],"type":["chr"],"align":["left"]},{"label":["kicker_player_id"],"name":[203],"type":["chr"],"align":["left"]},{"label":["own_kickoff_recovery_player_id"],"name":[204],"type":["chr"],"align":["left"]},{"label":["own_kickoff_recovery_player_name"],"name":[205],"type":["chr"],"align":["left"]},{"label":["blocked_player_id"],"name":[206],"type":["chr"],"align":["left"]},{"label":["blocked_player_name"],"name":[207],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_1_player_id"],"name":[208],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_1_player_name"],"name":[209],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_2_player_id"],"name":[210],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_2_player_name"],"name":[211],"type":["chr"],"align":["left"]},{"label":["qb_hit_1_player_id"],"name":[212],"type":["chr"],"align":["left"]},{"label":["qb_hit_1_player_name"],"name":[213],"type":["chr"],"align":["left"]},{"label":["qb_hit_2_player_id"],"name":[214],"type":["chr"],"align":["left"]},{"label":["qb_hit_2_player_name"],"name":[215],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_team"],"name":[216],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_player_id"],"name":[217],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_player_name"],"name":[218],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_team"],"name":[219],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_player_id"],"name":[220],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_player_name"],"name":[221],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_team"],"name":[222],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_team"],"name":[223],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_player_id"],"name":[224],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_player_id"],"name":[225],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_player_name"],"name":[226],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_player_name"],"name":[227],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_player_id"],"name":[228],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_player_name"],"name":[229],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_team"],"name":[230],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_player_id"],"name":[231],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_player_name"],"name":[232],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_team"],"name":[233],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_player_id"],"name":[234],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_player_name"],"name":[235],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_team"],"name":[236],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_player_id"],"name":[237],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_player_name"],"name":[238],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_team"],"name":[239],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist"],"name":[240],"type":["dbl"],"align":["right"]},{"label":["tackle_with_assist_1_player_id"],"name":[241],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_1_player_name"],"name":[242],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_1_team"],"name":[243],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_player_id"],"name":[244],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_player_name"],"name":[245],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_team"],"name":[246],"type":["chr"],"align":["left"]},{"label":["pass_defense_1_player_id"],"name":[247],"type":["chr"],"align":["left"]},{"label":["pass_defense_1_player_name"],"name":[248],"type":["chr"],"align":["left"]},{"label":["pass_defense_2_player_id"],"name":[249],"type":["chr"],"align":["left"]},{"label":["pass_defense_2_player_name"],"name":[250],"type":["chr"],"align":["left"]},{"label":["fumbled_1_team"],"name":[251],"type":["chr"],"align":["left"]},{"label":["fumbled_1_player_id"],"name":[252],"type":["chr"],"align":["left"]},{"label":["fumbled_1_player_name"],"name":[253],"type":["chr"],"align":["left"]},{"label":["fumbled_2_player_id"],"name":[254],"type":["chr"],"align":["left"]},{"label":["fumbled_2_player_name"],"name":[255],"type":["chr"],"align":["left"]},{"label":["fumbled_2_team"],"name":[256],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_team"],"name":[257],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_yards"],"name":[258],"type":["dbl"],"align":["right"]},{"label":["fumble_recovery_1_player_id"],"name":[259],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_player_name"],"name":[260],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_team"],"name":[261],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_yards"],"name":[262],"type":["dbl"],"align":["right"]},{"label":["fumble_recovery_2_player_id"],"name":[263],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_player_name"],"name":[264],"type":["chr"],"align":["left"]},{"label":["sack_player_id"],"name":[265],"type":["chr"],"align":["left"]},{"label":["sack_player_name"],"name":[266],"type":["chr"],"align":["left"]},{"label":["half_sack_1_player_id"],"name":[267],"type":["chr"],"align":["left"]},{"label":["half_sack_1_player_name"],"name":[268],"type":["chr"],"align":["left"]},{"label":["half_sack_2_player_id"],"name":[269],"type":["chr"],"align":["left"]},{"label":["half_sack_2_player_name"],"name":[270],"type":["chr"],"align":["left"]},{"label":["return_team"],"name":[271],"type":["chr"],"align":["left"]},{"label":["return_yards"],"name":[272],"type":["dbl"],"align":["right"]},{"label":["penalty_team"],"name":[273],"type":["chr"],"align":["left"]},{"label":["penalty_player_id"],"name":[274],"type":["chr"],"align":["left"]},{"label":["penalty_player_name"],"name":[275],"type":["chr"],"align":["left"]},{"label":["penalty_yards"],"name":[276],"type":["dbl"],"align":["right"]},{"label":["replay_or_challenge"],"name":[277],"type":["dbl"],"align":["right"]},{"label":["replay_or_challenge_result"],"name":[278],"type":["chr"],"align":["left"]},{"label":["penalty_type"],"name":[279],"type":["chr"],"align":["left"]},{"label":["defensive_two_point_attempt"],"name":[280],"type":["dbl"],"align":["right"]},{"label":["defensive_two_point_conv"],"name":[281],"type":["dbl"],"align":["right"]},{"label":["defensive_extra_point_attempt"],"name":[282],"type":["dbl"],"align":["right"]},{"label":["defensive_extra_point_conv"],"name":[283],"type":["dbl"],"align":["right"]},{"label":["safety_player_name"],"name":[284],"type":["chr"],"align":["left"]},{"label":["safety_player_id"],"name":[285],"type":["chr"],"align":["left"]},{"label":["season"],"name":[286],"type":["int"],"align":["right"]},{"label":["cp"],"name":[287],"type":["dbl"],"align":["right"]},{"label":["cpoe"],"name":[288],"type":["dbl"],"align":["right"]},{"label":["series"],"name":[289],"type":["dbl"],"align":["right"]},{"label":["series_success"],"name":[290],"type":["dbl"],"align":["right"]},{"label":["series_result"],"name":[291],"type":["chr"],"align":["left"]},{"label":["order_sequence"],"name":[292],"type":["dbl"],"align":["right"]},{"label":["start_time"],"name":[293],"type":["chr"],"align":["left"]},{"label":["time_of_day"],"name":[294],"type":["chr"],"align":["left"]},{"label":["stadium"],"name":[295],"type":["chr"],"align":["left"]},{"label":["weather"],"name":[296],"type":["chr"],"align":["left"]},{"label":["nfl_api_id"],"name":[297],"type":["chr"],"align":["left"]},{"label":["play_clock"],"name":[298],"type":["chr"],"align":["left"]},{"label":["play_deleted"],"name":[299],"type":["dbl"],"align":["right"]},{"label":["play_type_nfl"],"name":[300],"type":["chr"],"align":["left"]},{"label":["special_teams_play"],"name":[301],"type":["dbl"],"align":["right"]},{"label":["st_play_type"],"name":[302],"type":["chr"],"align":["left"]},{"label":["end_clock_time"],"name":[303],"type":["chr"],"align":["left"]},{"label":["end_yard_line"],"name":[304],"type":["chr"],"align":["left"]},{"label":["fixed_drive"],"name":[305],"type":["dbl"],"align":["right"]},{"label":["fixed_drive_result"],"name":[306],"type":["chr"],"align":["left"]},{"label":["drive_real_start_time"],"name":[307],"type":["chr"],"align":["left"]},{"label":["drive_play_count"],"name":[308],"type":["dbl"],"align":["right"]},{"label":["drive_time_of_possession"],"name":[309],"type":["chr"],"align":["left"]},{"label":["drive_first_downs"],"name":[310],"type":["dbl"],"align":["right"]},{"label":["drive_inside20"],"name":[311],"type":["dbl"],"align":["right"]},{"label":["drive_ended_with_score"],"name":[312],"type":["dbl"],"align":["right"]},{"label":["drive_quarter_start"],"name":[313],"type":["dbl"],"align":["right"]},{"label":["drive_quarter_end"],"name":[314],"type":["dbl"],"align":["right"]},{"label":["drive_yards_penalized"],"name":[315],"type":["dbl"],"align":["right"]},{"label":["drive_start_transition"],"name":[316],"type":["chr"],"align":["left"]},{"label":["drive_end_transition"],"name":[317],"type":["chr"],"align":["left"]},{"label":["drive_game_clock_start"],"name":[318],"type":["chr"],"align":["left"]},{"label":["drive_game_clock_end"],"name":[319],"type":["chr"],"align":["left"]},{"label":["drive_start_yard_line"],"name":[320],"type":["chr"],"align":["left"]},{"label":["drive_end_yard_line"],"name":[321],"type":["chr"],"align":["left"]},{"label":["drive_play_id_started"],"name":[322],"type":["dbl"],"align":["right"]},{"label":["drive_play_id_ended"],"name":[323],"type":["dbl"],"align":["right"]},{"label":["away_score"],"name":[324],"type":["int"],"align":["right"]},{"label":["home_score"],"name":[325],"type":["int"],"align":["right"]},{"label":["location"],"name":[326],"type":["chr"],"align":["left"]},{"label":["result"],"name":[327],"type":["int"],"align":["right"]},{"label":["total"],"name":[328],"type":["int"],"align":["right"]},{"label":["spread_line"],"name":[329],"type":["dbl"],"align":["right"]},{"label":["total_line"],"name":[330],"type":["dbl"],"align":["right"]},{"label":["div_game"],"name":[331],"type":["int"],"align":["right"]},{"label":["roof"],"name":[332],"type":["chr"],"align":["left"]},{"label":["surface"],"name":[333],"type":["chr"],"align":["left"]},{"label":["temp"],"name":[334],"type":["int"],"align":["right"]},{"label":["wind"],"name":[335],"type":["int"],"align":["right"]},{"label":["home_coach"],"name":[336],"type":["chr"],"align":["left"]},{"label":["away_coach"],"name":[337],"type":["chr"],"align":["left"]},{"label":["stadium_id"],"name":[338],"type":["chr"],"align":["left"]},{"label":["game_stadium"],"name":[339],"type":["chr"],"align":["left"]},{"label":["aborted_play"],"name":[340],"type":["dbl"],"align":["right"]},{"label":["success"],"name":[341],"type":["dbl"],"align":["right"]},{"label":["passer"],"name":[342],"type":["chr"],"align":["left"]},{"label":["passer_jersey_number"],"name":[343],"type":["int"],"align":["right"]},{"label":["rusher"],"name":[344],"type":["chr"],"align":["left"]},{"label":["rusher_jersey_number"],"name":[345],"type":["int"],"align":["right"]},{"label":["receiver"],"name":[346],"type":["chr"],"align":["left"]},{"label":["receiver_jersey_number"],"name":[347],"type":["int"],"align":["right"]},{"label":["pass"],"name":[348],"type":["dbl"],"align":["right"]},{"label":["rush"],"name":[349],"type":["dbl"],"align":["right"]},{"label":["first_down"],"name":[350],"type":["dbl"],"align":["right"]},{"label":["special"],"name":[351],"type":["dbl"],"align":["right"]},{"label":["play"],"name":[352],"type":["dbl"],"align":["right"]},{"label":["passer_id"],"name":[353],"type":["chr"],"align":["left"]},{"label":["rusher_id"],"name":[354],"type":["chr"],"align":["left"]},{"label":["receiver_id"],"name":[355],"type":["chr"],"align":["left"]},{"label":["name"],"name":[356],"type":["chr"],"align":["left"]},{"label":["jersey_number"],"name":[357],"type":["int"],"align":["right"]},{"label":["id"],"name":[358],"type":["chr"],"align":["left"]},{"label":["fantasy_player_name"],"name":[359],"type":["chr"],"align":["left"]},{"label":["fantasy_player_id"],"name":[360],"type":["chr"],"align":["left"]},{"label":["fantasy"],"name":[361],"type":["chr"],"align":["left"]},{"label":["fantasy_id"],"name":[362],"type":["chr"],"align":["left"]},{"label":["out_of_bounds"],"name":[363],"type":["dbl"],"align":["right"]},{"label":["home_opening_kickoff"],"name":[364],"type":["dbl"],"align":["right"]},{"label":["qb_epa"],"name":[365],"type":["dbl"],"align":["right"]},{"label":["xyac_epa"],"name":[366],"type":["dbl"],"align":["right"]},{"label":["xyac_mean_yardage"],"name":[367],"type":["dbl"],"align":["right"]},{"label":["xyac_median_yardage"],"name":[368],"type":["int"],"align":["right"]},{"label":["xyac_success"],"name":[369],"type":["dbl"],"align":["right"]},{"label":["xyac_fd"],"name":[370],"type":["dbl"],"align":["right"]},{"label":["xpass"],"name":[371],"type":["dbl"],"align":["right"]},{"label":["pass_oe"],"name":[372],"type":["dbl"],"align":["right"]}],"data":[{"1":"1192","2":"2024_05_LV_DEN","3":"2024100607","4":"DEN","5":"LV","6":"REG","7":"5","8":"LV","9":"away","10":"DEN","11":"DEN","12":"5","13":"2024-10-06","14":"539","15":"539","16":"2339","17":"Half1","18":"0","19":"5","20":"1","21":"2","22":"1","23":"1","24":"08:59","25":"DEN 5","26":"5","27":"64","28":"(8:59) 15-G.Minshew pass short left intended for 89-B.Bowers INTERCEPTED by 2-P.Surtain at DEN 0. 2-P.Surtain for 100 yards, TOUCHDOWN.","29":"pass","30":"0","31":"0","32":"0","33":"1","34":"0","35":"0","36":"0","37":"short","38":"left","39":"5","40":"NA","41":"NA","42":"NA","43":"NA","44":"NA","45":"NA","46":"NA","47":"2","48":"3","49":"0","50":"NA","51":"DEN","52":"P.Surtain","53":"00-0036874","54":"3","55":"2","56":"9","57":"10","58":"10","59":"3","60":"7","61":"10","62":"9","63":"1","64":"0.02059625","65":"0.01259468","66":"0.0003153327","67":"0.0194578","68":"0.1906979","69":"0.0005478086","70":"0.7557903","71":"0","72":"0","73":"5.689102","74":"-12.6891","75":"-0.6911647","76":"0.6911647","77":"-3.9857","78":"3.9857","79":"2.596085","80":"-2.596085","81":"1.310898","82":"-14","83":"0","84":"0","85":"2.961166","86":"-2.961166","87":"-9.157853","88":"9.157853","89":"1.834242","90":"-1.834242","91":"2.179503","92":"-2.179503","93":"0.7829888","94":"0.2170112","95":"0.2170112","96":"0.7829888","97":"-0.3391109","98":"-0.3104085","99":"0.3104085","100":"0.5561221","101":"0.4438779","102":"0.7415707","103":"0.2584293","104":"-0.1234891","105":"0.1234891","106":"0.03681916","107":"-0.03681916","108":"0","109":"-0.3391109","110":"0","111":"0","112":"-0.00774768","113":"0.00774768","114":"-0.1956643","115":"0.1956643","116":"-0.00774768","117":"0.00774768","118":"0.09291279","119":"-0.09291279","120":"0","121":"0","122":"0","123":"0","124":"0","125":"0","126":"0","127":"0","128":"0","129":"0","130":"1","131":"0","132":"0","133":"0","134":"0","135":"0","136":"0","137":"0","138":"0","139":"0","140":"0","141":"0","142":"0","143":"0","144":"0","145":"0","146":"0","147":"0","148":"0","149":"0","150":"0","151":"0","152":"0","153":"1","154":"0","155":"1","156":"0","157":"0","158":"1","159":"0","160":"0","161":"0","162":"0","163":"0","164":"0","165":"0","166":"0","167":"0","168":"0","169":"0","170":"0","171":"00-0035289","172":"G.Minshew","173":"NA","174":"00-0039338","175":"B.Bowers","176":"NA","177":"NA","178":"NA","179":"NA","180":"NA","181":"NA","182":"NA","183":"NA","184":"NA","185":"NA","186":"NA","187":"NA","188":"00-0036874","189":"P.Surtain","190":"NA","191":"NA","192":"NA","193":"NA","194":"NA","195":"NA","196":"NA","197":"NA","198":"NA","199":"NA","200":"NA","201":"NA","202":"NA","203":"NA","204":"NA","205":"NA","206":"NA","207":"NA","208":"NA","209":"NA","210":"NA","211":"NA","212":"NA","213":"NA","214":"NA","215":"NA","216":"NA","217":"NA","218":"NA","219":"NA","220":"NA","221":"NA","222":"NA","223":"NA","224":"NA","225":"NA","226":"NA","227":"NA","228":"NA","229":"NA","230":"NA","231":"NA","232":"NA","233":"NA","234":"NA","235":"NA","236":"NA","237":"NA","238":"NA","239":"NA","240":"0","241":"NA","242":"NA","243":"NA","244":"NA","245":"NA","246":"NA","247":"00-0036874","248":"P.Surtain","249":"NA","250":"NA","251":"NA","252":"NA","253":"NA","254":"NA","255":"NA","256":"NA","257":"NA","258":"NA","259":"NA","260":"NA","261":"NA","262":"NA","263":"NA","264":"NA","265":"NA","266":"NA","267":"NA","268":"NA","269":"NA","270":"NA","271":"DEN","272":"100","273":"NA","274":"NA","275":"NA","276":"NA","277":"0","278":"NA","279":"NA","280":"0","281":"0","282":"0","283":"0","284":"NA","285":"NA","286":"2024","287":"0.4172009","288":"-41.72009","289":"16","290":"0","291":"Opp touchdown","292":"1192","293":"10/6/24, 16:05:26","294":"2024-10-06T20:51:10.617Z","295":"Empower Field at Mile High","296":"Sunny Temp: 73° F, Humidity: 22%, Wind: N 7 mph","297":"7d40cd7a-1312-11ef-afd1-646009f18b2e","298":"0","299":"0","300":"INTERCEPTION","301":"0","302":"NA","303":"2024-10-06T20:51:26.540Z","304":"NA","305":"5","306":"Opp touchdown","307":"2024-10-06T20:47:01.690Z","308":"6","309":"3:40","310":"3","311":"1","312":"1","313":"2","314":"2","315":"0","316":"KICKOFF","317":"INTERCEPTION","318":"12:23","319":"08:43","320":"LV 31","321":"DEN 5","322":"1046","323":"1192","324":"18","325":"34","326":"Home","327":"16","328":"52","329":"3","330":"36","331":"1","332":"outdoors","333":"grass","334":"73","335":"7","336":"Sean Payton","337":"Antonio Pierce","338":"DEN00","339":"Empower Field at Mile High","340":"0","341":"0","342":"G.Minshew II","343":"15","344":"NA","345":"NA","346":"B.Bowers","347":"89","348":"1","349":"0","350":"0","351":"0","352":"1","353":"00-0035289","354":"NA","355":"00-0039338","356":"G.Minshew II","357":"15","358":"00-0035289","359":"B.Bowers","360":"00-0039338","361":"B.Bowers","362":"00-0039338","363":"0","364":"0","365":"-12.6891","366":"NA","367":"NA","368":"NA","369":"NA","370":"NA","371":"0.3684636","372":"63.15364"}],"options":{"columns":{"min":{},"max":[10],"total":[372]},"rows":{"min":[10],"max":[10],"total":[1]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->




<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MiwibmNvbCI6NSwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyIyIMOXIDUiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTFRUFUvRE1CQjEwNlJWUTF1SzRFZXdOQU1zTEtnVnF2Z2FFRUpGS2hKU1pWSzNWS1NPRlRzRndjSS82SThBTWJJeUlqSER3c0xNajJCdE9DYytxYzFKdHUvZXUyZS84MW1udCszMlhFSklrZGcyN0E2a3hEbnY3amQzQ0xFdEtBckVKaFY5M2dHOXJsbFlEVmlXSVlvbkY4ZVluaDUxNGFocnRuMDRUS1BkSVJnWjNuN0o4TDNxSjhRWDR0alUrcDVkYnY1OXpCQi9mM04zeGRPUDIzcSsvejE0M1hqSTJYSTRuVEJwTERrR0xJdFFLa1lucGx5VHNlOHpLZnNSVmF3dnFKU0dhQ3dSVWN3TlhxWFRVWjhKdXRpN2dwaHVXL1pRaWNKYkQzM1V0T2xIMkpJa21lZk4rb0crTURPTG9EdWdpbnJEQ1BSUTVTWGxVS2h4eUVGazZjOHY1Y1NGS0Flc3hsdzdHVFQ5NjVqZk5MZHlkRkh3a1g0emhiS29tZHhheUozTWhaVVllY25JUzR5UHhwemhPQUc5WWdIZVBHQlRrOWJoUDlMdjhFUTA1Z3JuQkZSNktsUVVKYTRmQm9pa2s1UDVQN0xEVkoyUkFnQUEifQ== -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["success_rate_pass"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["success_rate_run"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["avg_epa_pass"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["avg_epa_run"],"name":[5],"type":["dbl"],"align":["right"]}],"data":[{"1":"NYJ","2":"48.8","3":"33.3","4":"0.00","5":"-0.09"},{"1":"PIT","2":"40.0","3":"36.1","4":"0.29","5":"0.04"}],"options":{"columns":{"min":{},"max":[10],"total":[5]},"rows":{"min":[10],"max":[10],"total":[2]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjQgJT4lIFxuICBmaWx0ZXIocG9zdGVhbSA9PSAnUElUJyxcbiAgICAgICAgICFpcy5uYShyZWNlaXZlcl9wbGF5ZXJfbmFtZSkpICU+JSBcbiAgZ3JvdXBfYnkoZ2FtZV9pZCwgcG9zdGVhbSwgcmVjZWl2ZXJfcGxheWVyX25hbWUpICU+JVxuICAjIGdyb3VwX2J5KHBvc3RlYW0sIHJlY2VpdmVyX3BsYXllcl9uYW1lKSAlPiUgXG4gIHN1bW1hcmlzZShlcGEgPSBzdW0oZXBhLCBuYS5ybSA9IFRSVUUpLFxuICAgICAgICAgICAgY291bnRfdGFyZ2V0cyA9IG4oKSxcbiAgICAgICAgICAgIGNhdGNoZXMgPSBzdW0oY29tcGxldGVfcGFzcywgbmEucm0gPSBUUlVFKSwgXG4gICAgICAgICAgICB0b3VjaGRvd25zID0gc3VtKHRvdWNoZG93biwgbmEucm0gPSBUUlVFKSxcbiAgICAgICAgICAgIHlhcmRzX3JlY2VpdmluZyA9IHN1bShyZWNlaXZpbmdfeWFyZHMsIG5hLnJtID0gVFJVRSksIFxuICAgICAgICAgICAgbG9uZyA9IGlmZWxzZShpcy5pbmZpbml0ZShtYXgocmVjZWl2aW5nX3lhcmRzLCBuYS5ybSA9IFRSVUUpKSxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIDAsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICBtYXgocmVjZWl2aW5nX3lhcmRzLCBuYS5ybSA9IFRSVUUpKSxcbiAgICAgICAgICAgIGZpcnN0X2Rvd25fY2F0Y2ggPSBzdW0oZmlyc3RfZG93bl9wYXNzLCBuYS5ybSA9IFRSVUUpLCBcbiAgICAgICAgICAgIC5ncm91cHMgPSAnZHJvcCcpICU+JSBcbiAgbXV0YXRlKGVwYV9wZXJfdGFyZ2V0ID0gZXBhIC8gY291bnRfdGFyZ2V0cyxcbiAgICAgICAgIHlhcmRzX3Blcl9jYXRjaCA9IGlmX2Vsc2UoeWFyZHNfcmVjZWl2aW5nID09IDAsIDAsIHJvdW5kKHlhcmRzX3JlY2VpdmluZyAvIGNhdGNoZXMsIDEpKSkgJT4lIFxuICAjIGZpbHRlcihnYW1lX2lkID09ICcyMDI0XzA3X05ZSl9QSVQnKSAlPiUgXG4gIGFycmFuZ2UoLWVwYSlcblxuYGBgIn0= -->

```r
play_by_play_2024 %>% 
  filter(posteam == 'PIT',
         !is.na(receiver_player_name)) %>% 
  group_by(game_id, posteam, receiver_player_name) %>%
  # group_by(posteam, receiver_player_name) %>% 
  summarise(epa = sum(epa, na.rm = TRUE),
            count_targets = n(),
            catches = sum(complete_pass, na.rm = TRUE), 
            touchdowns = sum(touchdown, na.rm = TRUE),
            yards_receiving = sum(receiving_yards, na.rm = TRUE), 
            long = ifelse(is.infinite(max(receiving_yards, na.rm = TRUE)),
                              0,
                              max(receiving_yards, na.rm = TRUE)),
            first_down_catch = sum(first_down_pass, na.rm = TRUE), 
            .groups = 'drop') %>% 
  mutate(epa_per_target = epa / count_targets,
         yards_per_catch = if_else(yards_receiving == 0, 0, round(yards_receiving / catches, 1))) %>% 
  # filter(game_id == '2024_07_NYJ_PIT') %>% 
  arrange(-epa)

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiV2FybmluZzogVGhlcmUgd2FzIDEgd2FybmluZyBpbiBgc3VtbWFyaXNlKClgLlxu4oS5IEluIGFyZ3VtZW50OiBgbG9uZyA9IGlmZWxzZSguLi4pYC5cbuKEuSBJbiBncm91cCA1MDogYGdhbWVfaWQgPSBcIjIwMjRfMDdfTllKX1BJVFwiYCwgYHBvc3RlYW0gPSBcIlBJVFwiYCwgYHJlY2VpdmVyX3BsYXllcl9uYW1lID0gXCJOLkhhcnJpc1wiYC5cbkNhdXNlZCBieSB3YXJuaW5nIGluIGBtYXgoKWA6XG4hIG5vIG5vbi1taXNzaW5nIGFyZ3VtZW50cyB0byBtYXg7IHJldHVybmluZyAtSW5mXG4ifQ== -->

```
Warning: There was 1 warning in `summarise()`.
ℹ In argument: `long = ifelse(...)`.
ℹ In group 50: `game_id = "2024_07_NYJ_PIT"`, `posteam = "PIT"`, `receiver_player_name = "N.Harris"`.
Caused by warning in `max()`:
! no non-missing arguments to max; returning -Inf
```



<!-- rnb-output-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NTIsIm5jb2wiOjEyLCJzdW1tYXJ5Ijp7IkEgdGliYmxlIjpbIjUyIMOXIDEyIl19fSwicmRmIjoiSDRzSUFBQUFBQUFBQSsxWmUxQlVWUmcvQ3l3dkliR29JWFVRQWJVY3VQSlMwTkI3ZVlTOFpGQkJNVzNXMjNJWGRseDJ0N3NYaUpvS2N6UnJIS2FoOFlHT1NqaE5mMmhqeVl5UGYxck1vVkh6a2FObzRqUmxHbWFoa0N5V2xOSzVlNyt6c1FmdXNxZ3ovZU9adWZzNzMrOThyM1BPdldlL3U3c2t1eXc1dUN3WUllU0wvUHp3cHhaM2tiYTBKQ2MrRFNFL0h5eG9rQjhLa3ZFTlBQd003b1RnS3d4ZktUQXdQaWtoS1VXWGtLd3J6TWpTRmVlVnVOT3B1cUlWK2NQcFJKblNaWlFVZXVWa2JMNW42N0l6Q3IxMmt1VE1KUHZsSXErY3BEaTE4NHF5UGROUEtmUWNKMTI0ekhORWo4b3FBVld5VnRGV1dhZ3hKVUw3OEtpc3NucGoyekNWZTRUVzlwaUlpZzhWV21YNXZFemtZZkpUMmNmSDhqQ043ZGFoUXo1TTJtTkw1TEZNY3RTSDNmMnc4djFQODBuM1NkZkxydnM5RkpqRlpGVGJKS01aNUtDRlRMRlJ2MFl3MjlTSXdLWE1JcVBKSklnZ2h4UXpPYUpnRk1TcWFxblNBeGRZeE9UeW9taFVkUnlTelN6bmJaVkdjNFZrTVh0eVJLVThrbDFnUHVaRVVWQ2RGdTJFem01VUI5NW1Pend5NVhra1IrT1dNZm1Dd1NDSU5rOVVVQ2FUYjZrMDJ6ekdEODZ5TUxsQ1hTMHZscXROZFJGVExGWWJKV21zKzBENzhXSmZ2TmxQTHpLbWxuQmNGbFBNUzlMUXRSbk5aSGlRRVJhWXptd2tsVkVXWWFSdG8rOEl0L1R4bDVYOGVISlJ1N2RtZGQxSFhLUWpwT2NBUWx4RXYrSElwZGVMdUFtSDFzY3lXQTQxN3VnN2p6SHdUUDNHSlJnRE5HVzNMMkQwTjM5UnVYRFZKVTdiT2xVVGhXWHQ3TDlQRjJQMEczelhoQjk4enJkbWQyUzNqTEdyQnhybkxPWjh2am5jMDRabHREbnNyVTB5VGxobitBa2g5cCt1cjdzYk1BNmMzNncxeWJncGFBRWVaKyt0bmRXZWpySGY4ZG1OMmdPNXJPUElEN2Z3b2NMZTZaeU84MFpzVDBoemJqM0dXN2RmWEhtMnBaRHRXc3RHSm1ENVdvOTJxMlpiT252dDBDL0ZPQjU3dFNSMHZJd2RqdVBSc3QyRlNZNUtuQzk3c25yOUZGays4ZHkrREl6Mm96VjN6K0s4N1dkSzV5MlY1WE92N3B2UmpQSEtsaGhmN05kK1BhNnBETWV6MzB5S084aGgvSzNWTXMyS3NXZkt3WHpzMy82SFkwdWZiSGRuWjBqZGFveDlLYTBGNGZjZDlyNFRiNmJlMDNYYUhYa05XMjVrcE5zZHIweVlnbDhUN0k0eis1Sms3SjliMFBBclFtMW9neFNBNVRadHV5bHhBOFp3eTY0ZDUrU1pvbERuTVlyZk1PUTl4VmNBdm54QTlvVyt6R2xBMWdBbjkvMUF6eCs0Y2NESlYrQVFmZTJRUGhuM2dVc3pKS2JQRU45a1RFT05hU2dkWC9CUGZBYUFyTngvWWM0NUlpNGNNQUlRQVlaUk1uTFhaM3RCRHFSazVNNFBzNmY1eVZTOHNKSDE2SGpEZUpWOHliaExMM3hrbnM2ZjVra2J6YithSDVlZFNuelh2QUpkb1p6N3BKYUh0KzFSN1IrMXFjVWRMWi8vSzkrSGFNcnp0THpOS1hBckFVczVCVmxGaWVQcUZjd0R6QUFzQkNUUFlScGdJbkszbnc0NEh6QVRzQUF3R1hBVjV6NmVCZjd6QVJuZ293SG5vWkg1bHdCVEFST29jWkl2eVovd0VkUjRBc1VqOThiTnBQSUh1N1l3a0FuR0FaTHpZamJsSCticmVwNm9lU0d5VHdXUWJ3Nk1ad09tdU90ekN5aWVyQWVaRjhrM2tkS0xvdklpUEFmNEFtQVdZQkkxUDNxL295bVo1bU9wZVBRNHlYYyt4ZFA3RkVYeHlMMjU3RWllYXZ0RTVqZVprb2wvZXAvSVBrYTRRaW43Uk9KUy9vZWRwelNxZkI5NWU1N1QrcXJmWXlwKzZiaDBuTkhPWTlwT3JUM3U4NVBXVjVPSDhNcjMwOEMyTy80TCtPM3M3K3VhRHU5S3U4NTJiNGpMbkhpeWhkTW9kU3g3NC8zOWR6TU5CcmIzZzcxYXViNzhVNmxqMmN0N25tNWIzUEE1cVdQWjdvVURGYytXbHBJNmx1MVQ2bGoyNXZxTGU2cDJIbVYvVnVwWXRuUGpSRjBPOXRkaDJwL2NVVnJLZGtNZGUreTk3ZDE3VzI2eW5WREhYb1k2dGgzcTJDc3RiNmRiaDlTeHh5OTJOUnV3bi9PT1NZMGZtcEpkZGV3eHFHT1BRUjE3RHVyWWRxcU8zVFYvcHFreGJ4cDdCT3JZTDZHTy9RcnEyRU16UGtyQitkbS9WYWxqTzZHTy9SSHEyS3RVSFhzTjZ0aE8vcS84VHpwaTdOZWhqcjBTZmZTZGZ1ejN1MCtYTlh5Y25HenZVT3BZZTY5U3g5cS92OXFjMWhUYmFPOWRVYkMvMDJBZys4U2xucExiYVc1T3NyTnhjUVpuNDJZcG04bEZnVHkzWHBFVEFhZURIWDFPa0hPUDJJYzJ5VzA3Rnc5eUVvVXhnQW5QSzNya1BJa0J1OFJXSmE5STRNbjRWTWlMNWlmQlBHWlFlZEhuSHNuL1ljKzlpVlQrYXVmZVpBcW5BUWJCL09oemo4d3JuRVJ5K3dORGErYXJCQnRTZnNzSkFUS2dBcE02STNtaERiQmFiSkxBVjRFWUxncDZ3VmdqaURxcmlhL0RJTHNnUHd3SlZoNjZvWHBMdFZuU1NieFlJVWprRFRWQXowdjZTb0dJd1pLbFdsOVpicWwxdmNLT3I4TXYwamFkRWdLLzhRUHRaN0s0K21FR28yaVRkTEtWenVrTytLZHdiSjBWNTZPRWRIY284NHF5Ky95RFJFc3RROVpBZmhIenFjY2ZnNE9EcCtpRjBwdDRHMWtvUWdhWDh4TFBHRVI1QVJCNlFKa0VXS3lTMFlLbmhuemt2NGo4S1dPTlNCRmgxV1k1ay9KNGZXVzFlVTE4U2lvMTdtdkZhNENESXVVVkRFSEdjajlsU0Q5RVNjTm5FTXo5d2R4Zk1GY1l6V1NudENiK05jRkVQSmNMTldRVjhZSTQxNE94aWtZeldjVmd6Tm9ZeVNMeHhDUlliekVSeGpsMTlPQmZyUTQvU1RnYkFBQT0ifQ== -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["posteam"],"name":[2],"type":["chr"],"align":["left"]},{"label":["receiver_player_name"],"name":[3],"type":["chr"],"align":["left"]},{"label":["epa"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["count_targets"],"name":[5],"type":["int"],"align":["right"]},{"label":["catches"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["touchdowns"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["yards_receiving"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["long"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["first_down_catch"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["epa_per_target"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["yards_per_catch"],"name":[12],"type":["dbl"],"align":["right"]}],"data":[{"1":"2024_03_LAC_PIT","2":"PIT","3":"C.Austin","4":"8.3117009","5":"5","6":"4","7":"1","8":"95","9":"55","10":"2","11":"1.66234019","12":"23.8"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"G.Pickens","4":"7.7383306","5":"9","6":"5","7":"1","8":"111","9":"44","10":"4","11":"0.85981451","12":"22.2"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"G.Pickens","4":"6.2396497","5":"7","6":"6","7":"0","8":"85","9":"40","10":"4","11":"0.89137853","12":"14.2"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"S.Miller","4":"4.4292188","5":"2","6":"2","7":"0","8":"31","9":"20","10":"1","11":"2.21460942","12":"15.5"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"P.Freiermuth","4":"3.6765670","5":"5","6":"4","7":"0","8":"33","9":"15","10":"2","11":"0.73531340","12":"8.2"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"P.Freiermuth","4":"3.1008311","5":"3","6":"2","7":"0","8":"51","9":"30","10":"2","11":"1.03361036","12":"25.5"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"N.Harris","4":"2.8756579","5":"2","6":"2","7":"0","8":"35","9":"20","10":"2","11":"1.43782895","12":"17.5"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"G.Pickens","4":"2.8040474","5":"7","6":"5","7":"0","8":"57","9":"27","10":"3","11":"0.40057820","12":"11.4"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"D.Washington","4":"2.7124653","5":"1","6":"1","7":"1","8":"5","9":"5","10":"1","11":"2.71246529","12":"5.0"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"P.Freiermuth","4":"2.6513592","5":"3","6":"3","7":"1","8":"24","9":"19","10":"2","11":"0.88378639","12":"8.0"},{"1":"2024_04_PIT_IND","2":"PIT","3":"C.Austin","4":"2.6247548","5":"1","6":"1","7":"0","8":"17","9":"17","10":"1","11":"2.62475476","12":"17.0"},{"1":"2024_04_PIT_IND","2":"PIT","3":"D.Washington","4":"2.4329207","5":"2","6":"2","7":"0","8":"31","9":"20","10":"1","11":"1.21646034","12":"15.5"},{"1":"2024_06_PIT_LV","2":"PIT","3":"J.Warren","4":"2.3927631","5":"3","6":"3","7":"0","8":"11","9":"8","10":"0","11":"0.79758770","12":"3.7"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"G.Pickens","4":"2.3470324","5":"4","6":"2","7":"0","8":"29","9":"16","10":"2","11":"0.58675811","12":"14.5"},{"1":"2024_06_PIT_LV","2":"PIT","3":"C.Austin","4":"2.0727853","5":"5","6":"2","7":"0","8":"36","9":"20","10":"2","11":"0.41455707","12":"18.0"},{"1":"2024_04_PIT_IND","2":"PIT","3":"N.Harris","4":"2.0085514","5":"6","6":"3","7":"0","8":"54","9":"32","10":"2","11":"0.33475857","12":"18.0"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"J.Warren","4":"1.8063382","5":"2","6":"2","7":"0","8":"19","9":"12","10":"1","11":"0.90316912","12":"9.5"},{"1":"2024_04_PIT_IND","2":"PIT","3":"G.Pickens","4":"1.6766558","5":"11","6":"7","7":"0","8":"113","9":"38","10":"3","11":"0.15242325","12":"16.1"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"D.Washington","4":"1.6591885","5":"4","6":"4","7":"0","8":"36","9":"18","10":"2","11":"0.41479713","12":"9.0"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"P.Freiermuth","4":"1.5940397","5":"4","6":"4","7":"0","8":"39","9":"14","10":"2","11":"0.39850992","12":"9.8"},{"1":"2024_06_PIT_LV","2":"PIT","3":"G.Pickens","4":"1.3722304","5":"8","6":"3","7":"0","8":"53","9":"31","10":"2","11":"0.17152880","12":"17.7"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"J.Warren","4":"1.2953777","5":"3","6":"2","7":"0","8":"15","9":"11","10":"1","11":"0.43179255","12":"7.5"},{"1":"2024_06_PIT_LV","2":"PIT","3":"D.Washington","4":"1.1782589","5":"1","6":"1","7":"0","8":"9","9":"9","10":"1","11":"1.17825890","12":"9.0"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"V.Jefferson","4":"0.9702913","5":"5","6":"3","7":"0","8":"26","9":"11","10":"1","11":"0.19405825","12":"8.7"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"V.Jefferson","4":"0.9353225","5":"3","6":"2","7":"1","8":"15","9":"11","10":"2","11":"0.31177415","12":"7.5"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"B.Johnson","4":"0.7032772","5":"1","6":"1","7":"0","8":"9","9":"9","10":"0","11":"0.70327717","12":"9.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"P.Freiermuth","4":"0.6229275","5":"4","6":"4","7":"0","8":"27","9":"10","10":"2","11":"0.15573187","12":"6.8"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"Co.Heyward","4":"0.6161982","5":"4","6":"2","7":"1","8":"23","9":"16","10":"1","11":"0.15404955","12":"11.5"},{"1":"2024_06_PIT_LV","2":"PIT","3":"N.Harris","4":"0.5415101","5":"2","6":"2","7":"0","8":"16","9":"11","10":"1","11":"0.27075507","12":"8.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"M.Pruitt","4":"0.3430653","5":"2","6":"1","7":"0","8":"9","9":"9","10":"0","11":"0.17153265","12":"9.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"D.Washington","4":"0.3142062","5":"1","6":"1","7":"0","8":"5","9":"5","10":"0","11":"0.31420622","12":"5.0"},{"1":"2024_04_PIT_IND","2":"PIT","3":"P.Freiermuth","4":"0.2067114","5":"7","6":"5","7":"1","8":"57","9":"29","10":"2","11":"0.02953020","12":"11.4"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"N.Harris","4":"0.1960044","5":"2","6":"1","7":"0","8":"9","9":"9","10":"0","11":"0.09800221","12":"9.0"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"C.Austin","4":"-0.1364430","5":"2","6":"1","7":"0","8":"6","9":"6","10":"0","11":"-0.06822150","12":"6.0"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"D.Washington","4":"-0.2369759","5":"2","6":"1","7":"0","8":"5","9":"5","10":"0","11":"-0.11848797","12":"5.0"},{"1":"2024_06_PIT_LV","2":"PIT","3":"P.Freiermuth","4":"-0.2713423","5":"3","6":"2","7":"0","8":"16","9":"8","10":"0","11":"-0.09044744","12":"8.0"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"C.Austin","4":"-0.4310386","5":"2","6":"1","7":"0","8":"6","9":"6","10":"1","11":"-0.21551931","12":"6.0"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"Co.Heyward","4":"-0.6304442","5":"1","6":"1","7":"0","8":"2","9":"2","10":"0","11":"-0.63044421","12":"2.0"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"N.Harris","4":"-0.7873748","5":"1","6":"0","7":"0","8":"0","9":"0","10":"0","11":"-0.78737484","12":"0.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"J.Warren","4":"-0.8344036","5":"2","6":"2","7":"0","8":"13","9":"9","10":"0","11":"-0.41720179","12":"6.5"},{"1":"2024_04_PIT_IND","2":"PIT","3":"C.Patterson","4":"-0.9726211","5":"2","6":"2","7":"0","8":"19","9":"14","10":"1","11":"-0.48631055","12":"9.5"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"N.Harris","4":"-1.1222143","5":"2","6":"1","7":"0","8":"5","9":"5","10":"0","11":"-0.56110713","12":"5.0"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"J.Warren","4":"-1.1633420","5":"1","6":"1","7":"0","8":"-4","9":"-4","10":"0","11":"-1.16334197","12":"-4.0"},{"1":"2024_06_PIT_LV","2":"PIT","3":"Co.Heyward","4":"-1.2003663","5":"2","6":"1","7":"0","8":"4","9":"4","10":"0","11":"-0.60018315","12":"4.0"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"V.Jefferson","4":"-1.2366888","5":"3","6":"2","7":"0","8":"14","9":"12","10":"0","11":"-0.41222961","12":"7.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"C.Austin","4":"-1.2679582","5":"2","6":"1","7":"0","8":"7","9":"7","10":"0","11":"-0.63397912","12":"7.0"},{"1":"2024_04_PIT_IND","2":"PIT","3":"V.Jefferson","4":"-1.2719890","5":"3","6":"2","7":"0","8":"21","9":"12","10":"1","11":"-0.42399633","12":"10.5"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"N.Harris","4":"-1.3004572","5":"5","6":"5","7":"0","8":"16","9":"8","10":"0","11":"-0.26009144","12":"3.2"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"C.Austin","4":"-1.3264881","5":"4","6":"1","7":"0","8":"36","9":"36","10":"1","11":"-0.33162202","12":"36.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"V.Jefferson","4":"-2.0656510","5":"2","6":"1","7":"0","8":"1","9":"1","10":"0","11":"-1.03282550","12":"1.0"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"G.Pickens","4":"-2.7213978","5":"7","6":"3","7":"0","8":"26","9":"21","10":"1","11":"-0.38877111","12":"8.7"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"C.Patterson","4":"-5.1090035","5":"5","6":"3","7":"0","8":"15","9":"6","10":"1","11":"-1.02180070","12":"5.0"}],"options":{"columns":{"min":{},"max":[10],"total":[12]},"rows":{"min":[10],"max":[10],"total":[52]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6OCwibmNvbCI6MTQsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiOCDDlyAxNCJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUE2MVZYV2pUVUJTK2E3ZXVhMW1kdnlpS0tJemlYN091NjlhSlN1OVlyYXpXb2FXNjZVdkkycmhsUzVQYVpMcUJEMFZVRUdYNDRnOElLc0xRS1c2Q2lqaVU1VUZmUmNHZnlXU0NEME5RcE9EUFZOenFUWEx2YkRMRmwxMjQrZTczM1hOT3pqbVhtOFJDclRXT1ZnY0F3QXFLaTlHekJDMUJ5ZTU0MkZNUFFMRUZrU0pRRE1wVTdFSGJDOUhDaFdZRm1uYThNYy9uOWZscGJ6VzlzeWxPTjhTalJ0bW55YUd0elVhNWhvNDJOS3BiUnRtdldUYzFoNHh5TFIxcWlNNjJOc3N1WGE3VGdrVDNHSTBEZFBQZWlHWnNUTi82eDMrT2xzYjQ5Z2dWNWxnK0tjMFJMOTFPTmZBOEsvekxQRWExY0x3a0N2aWs3Q05mcjN4OFh6ODBBWXR1ZHA2N3ZuTVJYTVg1UzMyeFljVTYzK05HQjZ3NHd5Mjc3Z0VRL1BiaHdlVmJBSXlNM1hxNXNpOXBoNnVQUGFIT0RGaEpITVdhOXdlT0FBRGRVbFhOWm9RVnd1ZTFuMVIrKzJUVnhTeUEza3N2THZ6SWdtQnU4T0dYSE5KWGU3T2Rnd3FBdGR0YUJpNUJRT0xBeFlmWERGdWUyNVRsMDBlZEU2Kyt3ZVhYcGlZWDlNdktJdW5tRXZRMnhUTmNPYjlTQWNIUnp6K0hrSU5TZEdLcTVsSHVsT0orZC9yMTVaZFQvNnNMT3UvMlRYNVg2M3A4OWNiay8rdUN2a2Z1U1BqS0VlaE9qSTJ0UDk0UDY4YWpJOTU5b3pCQUQ0MjNQajBMdmZFTXZPTnRERDQ3Lzd6M1J2OGJXQlViTEgwNnVBeFdiNHpzdVAvMjEweWNBTkFHOUdNTVlvUlpIVGZwUEpqRGVqM0dMWUFNUFU0MTF0ZGgzSWl4RGlObGlyTUJvOWNZaHhCaVowWUkvajRLZEQyZnBWaGZnWkZ3TjhZMUp2OUtZLzVnanVzaStjM0NDb3d6bFJzNWlXdjZySlVJVElxVmdINW5YZVNPdFNPUjVwS0Vwa1ZKWnBrVXByWTBJMGxzaGx4NU5zMFFPNGJMMEFXMGwwa1VVTnVCdGdKbTd6SHUyaGxaWmxOcG1keGpaMEpNcFhsVzVrU0JTQTVaN0U1MEpNVkRNOG84VHNCbUxLMG1oZVh5djRrbEVwUG9ra3pWbDJYRVF4VHBRRG1hbGl4NjVQUDU3K1kySlhnMWxONG1JanFTak14USt6UElIN0ZwazB1cG1OYXpCeGIxdDJFek9SZGxURUpGdDZCbWt2UWtPcnFGTGsvQWI5cTNwb1YyOWFXYXBJOXl2TFlYckYxNkdwWThkcmVSOXJOQ095ZXdwQjZlYVdONUVqbkpIaVMvRU5RUXJSOVVPc01KTWlrVXFSSWxpekpEWEJ3SmtTZUtWanFZL2cwNXF5c2lUQWNBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["posteam"],"name":[2],"type":["chr"],"align":["left"]},{"label":["passer"],"name":[3],"type":["chr"],"align":["left"]},{"label":["epa"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["air_epa"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["yac_epa"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["qb_epa"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["xyac_epa"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["attempts"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["completions"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["touchdowns"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["incomplete_pass"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["complete_pass"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["sacks"],"name":[14],"type":["dbl"],"align":["right"]}],"data":[{"1":"2024_01_PIT_ATL","2":"PIT","3":"J.Fields","4":"-1.3522767","5":"-2.499611","6":"5.3712491","7":"-1.3522767","8":"18.766209","9":"23","10":"17","11":"0","12":"6","13":"17","14":"2"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"J.Fields","4":"2.2096760","5":"11.224969","6":"-6.9985506","7":"2.2096760","8":"11.195037","9":"20","10":"13","11":"1","12":"7","13":"13","14":"2"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"J.Fields","4":"8.2054751","5":"4.108349","6":"6.9150313","7":"8.2054751","8":"22.868359","9":"31","10":"25","11":"1","12":"6","13":"25","14":"2"},{"1":"2024_04_PIT_IND","2":"PIT","3":"J.Fields","4":"-2.3833869","5":"11.350671","6":"-5.1129650","7":"3.4636516","8":"23.373777","9":"33","10":"22","11":"1","12":"11","13":"22","14":"4"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"J.Fields","4":"-3.4093462","5":"16.624353","6":"-14.8635564","7":"-3.4715112","8":"16.329868","9":"27","10":"15","11":"2","12":"12","13":"15","14":"3"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"K.Allen","4":"1.4325529","5":"1.042662","6":"0.3898913","7":"1.4325529","8":"0.274953","9":"1","10":"1","11":"0","12":"0","13":"1","14":"0"},{"1":"2024_06_PIT_LV","2":"PIT","3":"J.Fields","4":"-0.4326682","5":"8.594730","6":"-2.1923775","7":"-0.4326682","8":"15.661484","9":"24","10":"14","11":"0","12":"10","13":"14","14":"3"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"R.Wilson","4":"8.7613387","5":"21.278681","6":"-11.4425114","7":"8.7613387","8":"17.223790","9":"29","10":"16","11":"2","12":"13","13":"16","14":"1"}],"options":{"columns":{"min":{},"max":[10],"total":[14]},"rows":{"min":[10],"max":[10],"total":[8]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->

