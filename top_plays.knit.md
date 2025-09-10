
<!-- rnb-text-begin -->

---
title: "NFL Analytics: top high-leverage plays"
output: html_notebook
---


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudGVhbXMgPC0gbmZscmVhZHI6OmxvYWRfdGVhbXMoY3VycmVudCA9IFRSVUUpXG5cbmBgYCJ9 -->

```r
teams <- nflreadr::load_teams(current = TRUE)

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiTm90ZTogbmZscmVhZHIgY2FjaGVzIChpLmUuLCBzdG9yZXMgYSBzYXZlZCB2ZXJzaW9uKSBkYXRhIGJ5IGRlZmF1bHQuXG5JZiB5b3UgZXhwZWN0IGRpZmZlcmVudCBvdXRwdXQgdHJ5IG9uZSBvZiB0aGUgZm9sbG93aW5nOlxu4oS5IFJlc3RhcnQgeW91ciBSIFNlc3Npb24gb3JcbuKEuSBSdW4gYG5mbHJlYWRyOjouY2xlYXJfY2FjaGUoKWAuXG5UbyBkaXNhYmxlIHRoaXMgd2FybmluZywgcnVuIGBvcHRpb25zKG5mbHJlYWRyLnZlcmJvc2UgPSBGQUxTRSlgIG9yIGFkZCBpdCB0byB5b3VyIC5ScHJvZmlsZVxuVGhpcyBtZXNzYWdlIGlzIGRpc3BsYXllZCBvbmNlIGV2ZXJ5IDggaG91cnMuXG4ifQ== -->

```
Note: nflreadr caches (i.e., stores a saved version) data by default.
If you expect different output try one of the following:
ℹ Restart your R Session or
ℹ Run `nflreadr::.clear_cache()`.
To disable this warning, run `options(nflreadr.verbose = FALSE)` or add it to your .Rprofile
This message is displayed once every 8 hours.
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


# Data


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->




<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudG9wX3BsYXlzIDwtIHBsYXlfYnlfcGxheV8yMDI1ICU+JSBcbiAgZmlsdGVyKHN0cl9kZXRlY3QoZ2FtZV9pZCwgJ1BJVCcpKSAlPiUgXG4gIGxlZnRfam9pbih4PS4sXG4gICAgICAgICAgICB5PXRlYW1zICU+JSBzZWxlY3QodGVhbV9hYmJyLCB0ZWFtX3dvcmRtYXJrKSxcbiAgICAgICAgICAgIGJ5PWMoJ3Bvc3RlYW0nID0gJ3RlYW1fYWJicicpKSAlPiUgXG4gIGxlZnRfam9pbih4PS4sXG4gICAgICAgICAgICB5PXRlYW1zICU+JSBzZWxlY3QodGVhbV9hYmJyLCBob21lX25pY2sgPSB0ZWFtX25pY2spLFxuICAgICAgICAgICAgYnk9YygnaG9tZV90ZWFtJyA9ICd0ZWFtX2FiYnInKSkgJT4lIFxuICBsZWZ0X2pvaW4oeD0uLFxuICAgICAgICAgICAgeT10ZWFtcyAlPiUgc2VsZWN0KHRlYW1fYWJiciwgYXdheV9uaWNrID0gdGVhbV9uaWNrKSxcbiAgICAgICAgICAgIGJ5PWMoJ2F3YXlfdGVhbScgPSAndGVhbV9hYmJyJykpICU+JSBcbiAgbXV0YXRlKGRvd25fZGlzdCA9IHBhc3RlKGRvd24sIHlkc3RvZ28sIHNlcCA9ICctJyksXG4gICAgICAgICBzY29yZSA9IHBhc3RlKHRvdGFsX2F3YXlfc2NvcmUsIHRvdGFsX2hvbWVfc2NvcmUsIHNlcCA9ICctJyksIFxuICAgICAgICAgcGxheV90eXBlID0gY2FzZV93aGVuKHBsYXlfdHlwZSA9PSAncGFzcycgfiAnUGFzcycsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdydW4nIH4gJ1J1bicsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdmaWVsZF9nb2FsJyB+ICdGRycsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGxheV90eXBlID09ICdwdW50JyB+ICdQdW50JyxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBUUlVFIH4gJ090aGVyJyksXG4gICAgICAgICBhYnNfZXBhID0gYWJzKGVwYSkpICU+JSBcbiAgZ3JvdXBfYnkoZ2FtZV9pZCkgJT4lIFxuICBhcnJhbmdlKC1hYnNfZXBhKSAlPiVcbiAgc2VsZWN0KGdhbWVfaWQsIHdlZWssIGhvbWVfbmljaywgYXdheV9uaWNrLCB0ZWFtX3dvcmRtYXJrLCBxdHIsIHRpbWUsIGRvd25fZGlzdCwgeXJkbG4sIHNjb3JlLCBwbGF5X3R5cGUsXG4gICAgICAgICBkZXNjLCBlcGEsIHdwYSkgJT4lXG4gICMgZmlsdGVyaW5nIG91dCBnYXJiYWdlIHRpbWUgKENvbmdlbGlvIGJvb2sgcmVjb21tZW5kcyB1c2luZyA5NS81IHNwbGl0IGlmIHlvdSdyZSBnb2luZyB0byByZW1vdmUgZ2FyYmFnZSB0aW1lIGF0IGFsbClcbiAgZmlsdGVyKHdwID4gLjA1ICYgd3AgPCAuOTUpICU+JSBcbiAgc2xpY2UoMToxMCkgJT4lIFxuICB1bmdyb3VwKClcblxuYGBgIn0= -->

```r
top_plays <- play_by_play_2025 %>% 
  filter(str_detect(game_id, 'PIT')) %>% 
  left_join(x=.,
            y=teams %>% select(team_abbr, team_wordmark),
            by=c('posteam' = 'team_abbr')) %>% 
  left_join(x=.,
            y=teams %>% select(team_abbr, home_nick = team_nick),
            by=c('home_team' = 'team_abbr')) %>% 
  left_join(x=.,
            y=teams %>% select(team_abbr, away_nick = team_nick),
            by=c('away_team' = 'team_abbr')) %>% 
  mutate(down_dist = paste(down, ydstogo, sep = '-'),
         score = paste(total_away_score, total_home_score, sep = '-'), 
         play_type = case_when(play_type == 'pass' ~ 'Pass',
                               play_type == 'run' ~ 'Run',
                               play_type == 'field_goal' ~ 'FG',
                               play_type == 'punt' ~ 'Punt',
                               TRUE ~ 'Other'),
         abs_epa = abs(epa)) %>% 
  group_by(game_id) %>% 
  arrange(-abs_epa) %>%
  select(game_id, week, home_nick, away_nick, team_wordmark, qtr, time, down_dist, yrdln, score, play_type,
         desc, epa, wpa) %>%
  # filtering out garbage time (Congelio book recommends using 95/5 split if you're going to remove garbage time at all)
  filter(wp > .05 & wp < .95) %>% 
  slice(1:10) %>% 
  ungroup()

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiXHUwMDFiRzE7RXJyb3IgaW4gYGZpbHRlcigpYDpcbuKEuSBJbiBhcmd1bWVudDogYHdwID4gMC4wNSAmIHdwIDwgMC45NWAuXG7ihLkgSW4gZ3JvdXAgMTogYGdhbWVfaWQgPSBcIjIwMjVfMDFfUElUX05ZSlwiYC5cbkNhdXNlZCBieSBlcnJvcjpcbiEgb2JqZWN0ICd3cCcgbm90IGZvdW5kXG5CYWNrdHJhY2U6XG4gIDEuIC4uLiAlPiUgdW5ncm91cCgpXG4gIDUuIGRwbHlyOjo6ZmlsdGVyLmRhdGEuZnJhbWUoLiwgd3AgPiAwLjA1ICYgd3AgPCAwLjk1KVxuICA2LiBkcGx5cjo6OmZpbHRlcl9yb3dzKC5kYXRhLCBkb3RzLCBieSlcbiAgNy4gZHBseXI6OjpmaWx0ZXJfZXZhbCguLi4pXG4gIDkuIG1hc2skZXZhbF9hbGxfZmlsdGVyKGRvdHMsIGVudl9maWx0ZXIpXG4gMTAuIGRwbHlyIChsb2NhbCkgZXZhbCgpXG5cdTAwMWJnXG4ifQ== -->

```
G1;Error in `filter()`:
ℹ In argument: `wp > 0.05 & wp < 0.95`.
ℹ In group 1: `game_id = "2025_01_PIT_NYJ"`.
Caused by error:
! object 'wp' not found
Backtrace:
  1. ... %>% ungroup()
  5. dplyr:::filter.data.frame(., wp > 0.05 & wp < 0.95)
  6. dplyr:::filter_rows(.data, dots, by)
  7. dplyr:::filter_eval(...)
  9. mask$eval_all_filter(dots, env_filter)
 10. dplyr (local) eval()
g
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MSwibmNvbCI6MSwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyIxIMOXIDEiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTJRVVd1RE1CREhUNnVXQ3VzRy9SeEs1eGpzQTVSQzkxQktzZEErU2FhWms3bEVOTjM2MkUrdXUwZ0Njb0VrbDd2N1hlNS94ODM1SlR5SEFEQUR6OFBUUnhQOFU3cU4zZ0E4Rng4T2VMRFE5dzNEcTlFQjhEUUpQQ2JyNURWYlAyZUhYWnJ0TCsrRTh3WDc0UjFoNWlVNnM2b2d1WXRXL3NVMi93RzNlOGRqd0VXTDVqWHJhTkd3WUlyRm55M3krT29KTXBlTnFxUkF5TlVxQWdJN0xaVjFGYnFUSXNxL3J1STdTa2g0MW9oUy8ya0dBcVpoeCt5SnJidHdCNE1IQmcrNEtDdkJyWnlhZmZEYVZpNzRyekdYT0k5eEhISFRWa0pabmVqdFlpVVZzMGlZeTlwNlJ1WFEvd1BxNWNEWjJnRUFBQT09In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]}],"data":[{"1":"2025_01_PIT_NYJ"}],"options":{"columns":{"min":{},"max":[10],"total":[1]},"rows":{"min":[10],"max":[10],"total":[1]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


```{=html}

<!-- rnb-html-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInNoaW55LnRhZyJdLCJzaXppbmdQb2xpY3kiOltdfX0= -->

<div id="dahrvobida" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>@import url("https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Spline+Sans+Mono:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#dahrvobida table {
  font-family: 'Spline Sans Mono', system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#dahrvobida thead, #dahrvobida tbody, #dahrvobida tfoot, #dahrvobida tr, #dahrvobida td, #dahrvobida th {
  border-style: none;
}

#dahrvobida p {
  margin: 0;
  padding: 0;
}

#dahrvobida .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 14px;
  font-weight: 500;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#dahrvobida .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#dahrvobida .gt_title {
  color: #333333;
  font-size: 26px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#dahrvobida .gt_subtitle {
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

#dahrvobida .gt_heading {
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

#dahrvobida .gt_bottom_border {
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#dahrvobida .gt_col_headings {
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#dahrvobida .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: 500;
  text-transform: inherit;
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

#dahrvobida .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: 500;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#dahrvobida .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#dahrvobida .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#dahrvobida .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#dahrvobida .gt_spanner_row {
  border-bottom-style: hidden;
}

#dahrvobida .gt_group_heading {
  padding-top: 1.5px;
  padding-bottom: 1.5px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#dahrvobida .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #000000;
  vertical-align: middle;
}

#dahrvobida .gt_from_md > :first-child {
  margin-top: 0;
}

#dahrvobida .gt_from_md > :last-child {
  margin-bottom: 0;
}

#dahrvobida .gt_row {
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

#dahrvobida .gt_stub {
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
}

#dahrvobida .gt_stub_row_group {
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

#dahrvobida .gt_row_group_first td {
  border-top-width: 2px;
}

#dahrvobida .gt_row_group_first th {
  border-top-width: 2px;
}

#dahrvobida .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#dahrvobida .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#dahrvobida .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#dahrvobida .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#dahrvobida .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#dahrvobida .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#dahrvobida .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#dahrvobida .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#dahrvobida .gt_table_body {
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#dahrvobida .gt_footnotes {
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

#dahrvobida .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#dahrvobida .gt_sourcenotes {
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

#dahrvobida .gt_sourcenote {
  font-size: 10px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#dahrvobida .gt_left {
  text-align: left;
}

#dahrvobida .gt_center {
  text-align: center;
}

#dahrvobida .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#dahrvobida .gt_font_normal {
  font-weight: normal;
}

#dahrvobida .gt_font_bold {
  font-weight: bold;
}

#dahrvobida .gt_font_italic {
  font-style: italic;
}

#dahrvobida .gt_super {
  font-size: 65%;
}

#dahrvobida .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#dahrvobida .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#dahrvobida .gt_indent_1 {
  text-indent: 5px;
}

#dahrvobida .gt_indent_2 {
  text-indent: 10px;
}

#dahrvobida .gt_indent_3 {
  text-indent: 15px;
}

#dahrvobida .gt_indent_4 {
  text-indent: 20px;
}

#dahrvobida .gt_indent_5 {
  text-indent: 25px;
}

#dahrvobida .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#dahrvobida div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}

#dahrvobida tbody tr:last-child {
  border-bottom: 2px solid #ffffff00;
}

#dahrvobida .gt_subtitle {
  padding-top: 0px !important;
  padding-bottom: 4px !important;
}

#dahrvobida .gt_sourcenote {
  border-bottom-color: #FFFDF5 !important;
}

#dahrvobida .gt_heading {
  padding-bottom: 0px;
  padding-top: 6px;
}
</style>
  <table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    <tr class="gt_heading">
      <td colspan="10" class="gt_heading gt_title gt_font_normal" style="font-size: 22px; font-weight: 650; font-family: 'Work Sans';"><span class='gt_from_md'>Top plays from the Jets vs Steelers<br>Week 1 Matchup</span></td>
    </tr>
    <tr class="gt_heading">
      <td colspan="10" class="gt_heading gt_subtitle gt_font_normal gt_bottom_border" style="font-family: 'Work Sans'; font-size: 14px; font-weight: 500;"><span class='gt_from_md'>Plays ranked by absolute value of Expected Points Added<br>Excluding garbage time where win probabilty is .05 &lt; x &lt; .95</span></td>
    </tr>
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="team_wordmark">Possessing team</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="qtr">Qtr</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="time">Time</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="down_dist">Down-Dist</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="yrdln">Field Pos</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="score">score</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="play_type">Play</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="desc">Description</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="epa">epa</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" style="border-bottom-width: 3px; border-bottom-style: solid; border-bottom-color: #000000; font-weight: 650; font-family: 'Work Sans'; font-size: 12px; text-transform: uppercase;" scope="col" id="wpa">Win Prob Change</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">14:57</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NA-0</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">PIT 35</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">24-26</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Other</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">9-C.Boswell kicks 64 yards from PIT 35 to NYJ 1. 3-X.Gipson to NYJ 20 for 19 yards (14-K.Gainwell). FUMBLES (14-K.Gainwell), RECOVERED by PIT-15-B.Skowronek at NYJ 22. 15-B.Skowronek to NYJ 22 for no gain (3-X.Gipson).</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #FF2410; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">−5.7</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">−27.7%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">1</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">00:31</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">1-10</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">PIT 33</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">7-9</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(:31) (Shotgun) 7-J.Fields pass deep right to 5-G.Wilson for 33 yards, TOUCHDOWN.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #7BA56E; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">3.1</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">11.8%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">1</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">06:22</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">3-10</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">PIT 40</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">0-3</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(6:22) (Shotgun) 8-A.Rodgers pass short right to 4-D.Metcalf pushed ob at NYJ 37 for 23 yards (8-A.Cisco).</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #81A975; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">3.0</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">13.3%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">1</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">03:44</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2-7</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 22</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">6-3</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(3:44) 8-A.Rodgers pass short right to 15-B.Skowronek for 22 yards, TOUCHDOWN.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #83AA76; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.9</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">7.0%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">01:08</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4-11</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 42</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">34-32</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">FG</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(1:08) 9-C.Boswell 60 yard field goal is GOOD, Center-46-C.Kuntz, Holder-3-C.Waitman.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #85AC79; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.9</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">22.9%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">05:59</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">3-9</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 38</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">10-16</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(5:59) (Shotgun) 7-J.Fields pass deep middle to 16-T.Johnson to PIT 38 for 24 yards (56-A.Highsmith).</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #86AD7A; color: #FFFFFF; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.9</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">6.6%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">14:12</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2-6</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 18</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">30-26</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(14:12) 8-A.Rodgers pass deep right to 19-C.Austin for 18 yards, TOUCHDOWN.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #8EB283; color: #000000; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.6</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">11.6%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">01:07</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2-10</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 24</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">10-19</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Pass</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(1:07) (Shotgun) 8-A.Rodgers pass deep right to 19-C.Austin to NYJ 3 for 21 yards (21-B.Stephens).</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #92B486; color: #000000; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.6</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4.2%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/NYJ.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">07:06</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4-1</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">PIT 1</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">31-32</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">Run</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(7:06) 7-J.Fields right end for 1 yard, TOUCHDOWN. NYJ-76-J.Simpson was injured during the play.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #93B587; color: #000000; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.5</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">19.6%</td></tr>
    <tr><td headers="team_wordmark" class="gt_row gt_center" style="border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;"><img src="https://github.com/nflverse/nflverse-pbp/raw/master/wordmarks/PIT.png" style="height:30px;"></td>
<td headers="qtr" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2</td>
<td headers="time" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">13:30</td>
<td headers="down_dist" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">4-6</td>
<td headers="yrdln" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">NYJ 37</td>
<td headers="score" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">10-9</td>
<td headers="play_type" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">FG</td>
<td headers="desc" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">(13:30) 9-C.Boswell 56 yard field goal is GOOD, Center-46-C.Kuntz, Holder-3-C.Waitman.</td>
<td headers="epa" class="gt_row gt_center" style="background-color: #99B98E; color: #000000; border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">2.4</td>
<td headers="wpa" class="gt_row gt_center" style="border-left-width: 0.5px; border-left-style: solid; border-left-color: black; border-top-width: 1.5px; border-top-style: dotted; border-top-color: black;">0.7%</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="10">Replicating work done by Kevin Cole in the Unexpected Points Substack newsletter</td>
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


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjUgJT4lIFxuICBmaWx0ZXIoZ2FtZV9pZCA9PSAnMjAyNV8wMV9QSVRfTllKJyxcbiAgICAgICAgIHBsYXlfdHlwZSAlaW4lIGMoJ3J1bicsICdwYXNzJykpICU+JSBcbiAgc2VsZWN0KHBvc3RlYW0sIHBlbmFsdHksIHN1Y2Nlc3MsIHBsYXlfdHlwZSwgZXZlcnl0aGluZygpKSAlPiUgXG4gIGZpbHRlcihpcy5uYShkb3duKSlcblxuYGBgIn0= -->

```r
play_by_play_2025 %>% 
  filter(game_id == '2025_01_PIT_NYJ',
         play_type %in% c('run', 'pass')) %>% 
  select(posteam, penalty, success, play_type, everything()) %>% 
  filter(is.na(down))

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiXHUwMDFiRzM74pSA4pSAIG5mbHZlcnNlIHBsYXkgYnkgcGxheSBkYXRhIOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgOKUgFxuXHUwMDFiZ1x1MDAxYkczO+KEuSBEYXRhIHVwZGF0ZWQ6IDIwMjUtMDktMDggMDU6MjQ6MDAgRURUXG5cdTAwMWJnXG4ifQ== -->

```
G3;── nflverse play by play data ───────────────────────────────────────────────────────────────────────────────────────────────
gG3;ℹ Data updated: 2025-09-08 05:24:00 EDT
g
```



<!-- rnb-output-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbIm5mbHZlcnNlX2RhdGEiLCJ0YmxfZGYiLCJ0YmwiLCJkYXRhLnRhYmxlIiwiZGF0YS5mcmFtZSJdLCJucm93IjoyLCJuY29sIjozNzIsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMiDDlyAzNzIiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBKzFkZTJ3angzbm42U1JSYjFHUE84azZKOTBZanR1bUptOUpTa2VMTFVLZXovZnk0KzV5bG51MjBXSzc0czZLNnlOMzZkMmxlWEwvaUl3VWFCTUUrU3VJKzBjUUp3MktwRTBMSDRJZ1NJRUFVdG8wU0JEWE1BbzBTT0E2Y0pPMnNkczZhRkRBYVpIRzZjenV6T3pNN0N4cHlYZXRYYXdBSG5kKzMyTysrZWFieDg1ODBsMis1K0h5eE1NVG1Vem1jR1o0R1A0N0FoOHpJdzl0bk1uZmxja01EOEhDb2N4d1poeDlYNFBrQmZqdHcwSU9mb1l3NGZDRlIrNWxIek9abVlBYS8wbkNPVzF1MThhUHd4M2Q4NGhZL1EvVWdMZitwOC9MeEdaTGFtbE5VNHZhcGZNYldtUlFET2FsSmhCWlhWY3I2Z2tKTXFpWkhCVld3RDRLMU11bno3S1BtY3cwZHNVaC9HRzVoNXRPRzNEUCs2b3JSZzM4Vi92MzBHbDF1ZHVEZHVmVjlieGFrU0NrRDlheGppY3ZjVjFhLytncmN2eVA3eFZ4dHM2UmMzckxMTEtGVW1aQThOVEhzQVZGSGsvaXA2M084ZmdIQXp6N1IrUTdFL1dJMUZKVnJaYldhS0ZTVllzaUIzUzFVbVFMZzl0eTMwNW8yNlU5V1ozM2IxeTVtTDkwOGZ5RkRlWFV4UXUvZWZyeWcrY3ZYbEJPYm15Y2Z1RFNSa0ZSODNjWFRyWmF3RmJjcnRjRW50THRLSDRUS0czTE1GcWdRQmlWTXlmUDMvOWdBZXQ4dXIvT1N2N2V3aGtMdEF4UFFVTlA4UjFsTFgrMmNNVnFlWTZ0V0o1aTJRMm4zV2tCUDFhQjhyNzNLZWZ0eDdydXR2SlF4OUI5VUZXZ0UvTHJsZndwdlhBT2JQZDAxMUNhdXFlNHdPKzZOakNRY21Udmx0NEdoVUd1T2loT3V2OEc2czloZlB3WDhJZjVUc0tUd2kwSjM2LysvZGJiWDA4WUpsbFR0MXBkRjRoRllSQ0szcVdEODhaNzhVQ3QzNitkOWRzd1hoZndXekZlZTR2OG1RUjdicENlVFB6bkhZWFh2di9BMy83a1QzNzJJL0pOOFI5ai9NYzh2b3ZMdXlLKzlkZ2IzNTM1UW1iM0I4ZC84ZFZyNzdwQzlXQzhKdUM3TDc3WU5MLzU4UHZyUzYrKzUxOSs5RVdOOG1OOFQ4QjNmM3IxSysvUFpUSzdQMXZkK056WFZyNUErVEZlRS9COWpQNEQrYTIrOE1vbm52MEpqSk5mL2NEZjZhL1ZLYjZIOFQwUlYvN3R0N0t2NzJUMlNwYzNQcU1mZW83cXdYaGR4STkrNitJLy9RUFUvOHUvOGVGbjNMMUlEOGIzUkZ4NTluZisvanRRZjJIcHRmelgvK3JwU0grSTF3Vzg5c05EcjM5a2VQbmp0UjlPdHI0MWV2dExGUC9lZjgvLzYwK2YvMjd0ZTYvZTBmNlBMNTg1S1AvdU0xK2ZybjlvZm1mM3V2V0g1NHAzdkVMeHA2OW4vdm5WYXkvdi9sbm5wZEhmLzdYTUlMejJnOFBmVWVCRDdlVTMxdmZZdUgzeFB4OUU1ZHIzRDM5MGg4VmYrdEMzTDloUGY2ejI4cGUxVHRPOVBnamYvZXdIUC9YcGt4K3UxLzc2TmU5M1AvSE1seWcveG5jRmZQZXBqN3d3OGV2UDcreCsvRysrY2ZyblA5K2ovQml2Q2ZqTmpzUGFzOGQvR3hWMi83ejEzUEd0NTE2bWRtSzhKdUo3L3ppLzk5bXZ2bEw3dmRjVjcwNm5UdlZnZkZmRTk2di9ML3ovZXVyczlndTF6enoveVU5Kys5Z0xWQS9HZHdWOHYrMU44UlIvSitMTXZrSEsvM2JmVnhENzN1NTIza1E4bDJIM3ZmaUZYVlh6cWxvK3NiNjZsc0F4Umw3dmlPYUI3d2VjNWtwbFZVM1NUTjRTQjJybU5LNVgxbGN6Q2U4ZytQVTI4MVpmYVc3VXE5SE4wNVBpS1o3aUtmNy9GWDl6aTlqL3ZaMHB6dlRYMis1bzhwMkwzK3o0Mys5TC9JMnkvK1pzWmdmYmcyOXFzcStHbjRNZGJ0VHZDQ3V2bitYdGs3eGNoSGFFMjlMeERhZmJhQnBPejQ0RFJIUC9tOHJjK3ZISzhkTGFuVXF4WEZWTDFkVnlJczdMTFViM2NSdkZTclcwWGkwV0g4VzBaWmEyRG1XcjZscGg3WVQ2cUtCajlnSGczMitaUUhuUTF3MnIyMDZDcWU5M0VQbjhxWmJUTmJhVm51VTNsYmJqQXNYVkxWdnBPSjVuYmJhQXNnSGFuYXB5b3ZLWDE1VXpkeXJudW0zTHNQenRxbEpaZisrZHloWExOcXJLRmFXc3REdk5tNkNRYTkvdDV0cDZVUy9mVmNxWGkwV1FMeFpOTmI5NW9xTG1kVkFzcmFtbWJ1aEdjVis4dlA1RGF2UXdLSjd4L2UybGt4c2w3dm10am9QRUhsOHZWTXJsUi92b0NhT1RYSDZvQjRodmxuTlppTWRTdGF3V1NzVnlRa3lXS29oKzRrVGxVV3JKTXJia1YrU2VLMWVMWkd3TVY2ckJmVHpmZ21VcTEvZjRJdW00SU9sdU9Ba25oZnFpMU43c2ZlZFAzWGZ4ekJteEtQcjM0a09uenQxejhjcUZPTUJ6anFqbGF2a3VVaWl1Vm9ON2VKNWowSzMwNklWSDdsVlcxOWhTV1p4WFJ0RmxkWmw0R3Q5akUxYy9kVDFzOHVkbk9GZElwamh5Zlg0Yi9wQ3lnajlzbGNQbm1BU0hjMkdDUThBUDQvUU45R0hrNzhhZjhHWUJkejM1cHZiY3ZSZmFnNzh6L2Eveng1eXViemlPNjhYS1BGK0dmbU45Ty9DZkhYbVpsWnM4cWJ1T3JaeHRBZHVXUVFMM0E5WlZPT2M1N1pabHl5Q2gweTg4Y2tvdDhvV0RUdkw3T1YxaXo0NW8yK0ZQVnFoZGNtNUR1MktuajNybUFJbFZQeUthbVRTS21aOGJkYWdvczFOMnlEYjRTRXVxZ3p0T0U1eVg0SE5zbU9oenR1cEJab3BWTUg1L1V5cmZoTlVIVkhtZ005K2tPK0I5YkFmRmtYeWc3ZVNieDdta3VoRmJid004N1J6eWlUL2hSc2dIZXBzV2dhMjMvRzFTOUxxTkJ2REkzRFhlYWVuYm1yL2RvZGthQVdBWnBJZ1NiS0xpcE5NeU5CNGFSeWxtR2xQaHVONURLaU5nMGdNNjdFKzJsdUVlQUZmeDh4UzJsN1BDQUNhallkcXpES0E1cG1haWVDWnkyN3Byd0JrT2FFV1ZiS3pHQTl0UUFoRUdibm04cTdzK2NEVVBOQnpiOERRWHRPRm0wYkszTU1QUnB0NHlrNm1CdmlScVdCdFNRRnBLYWdNMnNYTEVjSzBuaURWRFhvZmsxajN1dThRWHpIWnBZc3ZSVzVydmFGc09vZm9XWGV4R3RtR0RDV3QyMi9COGgvS053cUlOZktvVGVBM1dUeDdzTmVncTJxMWUwL0czYUtya3VPMW96UzdLL0tJTjJkUU0xK2xzNmczU1RXTVF1bW9EMEdMS1hnY3VOSXlJMTNEMTltYWtCYVdCYVhCb2IvbE4wcE1oNURSMDMzSm85YnJsYW9HVkdKZ0xUZFpONUV2STJpRGlVMjdYRnFXekNOdlNpV2ZuZ2hqUkFrZTZ3T3UyaUUrbXIxcU5xNXBoZWI1dU40aUo4K0NhNytwYXg3RnNuMmMvNHZjY2pNUGVmNEluTG9WQkQ3c0dydjN4d0ZnS2gwQVNPWXNwcEZHNHlJNlpyRyt3eFJsWVJBTVR1Z01OZVNwSVVUb2NWK2hvU3FwOUJZK3RaSTZjNy9qUWUwRWJ2WVpETTdrd0hqU094YWRKblJ4SXFtSEIrYUFBTzhFMGdRdHMzOUpKT00xek9qUlVJaFJPRVV0WmltdGp5ZE13cXJHTTYyelNHYXpUMGN3dEZwcEZrS2Vid04rT2NTSVBSMUNXRjV5TUMyVjVnUndiWGd4K0N4OWN3UFZnUExNTVE0RE9GS0NqMHlpSStpV0dCcjBTb1FzTUwwcnhqSk1DQVRrcGtBcEdxbHhLSUdYUitHV0syM3FES1U2aHBFK05ad2t4bm0rSnFWc2lzc1RVbjB5T3BLWEtJMm1lZkpUMWx0NFRkQjlsSFpaRXBiSlN6VlNXcHc3MVNEZVB3aWpYYUNrYmFJdUtnVGd0SHU1UkJlTlBnQzNkMHlKZ0pnU3dQUFUzTHJQRFl3b3JaYkV4b280TUlVNWJVbWoxa2tNclJvcENTeTRsa0lMUTZ2R2gxWk9FbG9qeGZOTFFpcEg1ME9vakxWWE9oMWF2YjJqRnFGeG9KY3RLTlhPaHhmaWgwNFd6eXlaY0xLL1NaWC9XdEZ6UDE5Q0dJK2dlQ1J6ODBnU2VlRm1ZMjBRdStrM0xOVUpLT0gvNXRJNDVob1l5ZnluaGlPbDBYYjhwbDVwbmlaelliSlExemhvMzdxT0RKV1ovTWdVblUrQTJRSWZaR3N3SFByRHNZUHZvOStBU1FWb3dpeWxvcC9ha1l3Tk9BSzNGY0xPNTZYUnR1aVdaRENqSXZNaXlBREpSbDdGN2xDTm9uK0dZcHJUZStZZ29WRTNGWkxYUEVDSm5BRlVXczJIYTdLSjltR1k2MENPMFp6Qm9PejVQV01RRWFiczlwK1ZvUHZRejNkYU5oc3NlM1JRRU5BT3BoRnN6MmtHVFdHa3JtbDBXVWVjU20xMjRxWVloUU5Rc3lXaHcrU1Yxd3QxbDA2SlRWekMzNkw0UDJoMktCVE1IancxN1VYeUVBY1BzdFdjQ2dSZ2FxQmJSWFBoN0J6RjhnVjNmK2Jybm9pV2VKOHd6RzFTZU1rdmFMN2FzRzFNeUducVhkTGRzaEV6RFI3alo1ZnR1cmdYZmpkeGdhOHdQbFNsS2lPYUZtWWdadFo3NGdsSEI5bUFPMVEyM291S09kSjdIbWYxcjhESUF0NTNjM244ZVdRWmZtZUtLRmtVS28ybzJwSW5LY3NGdnQwaHM0bkhXSmtRUjFheXdYcFBhZG1zU0I2TjZpZWNSSzFsbWUwQlN4WXFjemxSd2hPVVExUjhsUkRRbVlzcVhaVlJHOVZGMmRvMUx5NmlNOUx1SjlyNWFsSDVjckIrRDhZQi9FeWp1cDF1a1pFYitsMGc5L2ZXOHB5OGJvKy9XYU5wSzVGbEo0cUhWM1VhcUc4aDUreUJPcHQ0Y01sNDZLRG1ja1FnV0Zia3Vua0oxdlZzNmRjZDZ0eDhYVThzYzNyTEVGQ3dJQkVibVdEakgwU1ZJSzhhazM1WEkwazlQYWJDZWtzeUg0V29sTVdOUnBFaWs0cFV1aWhUVzVuQXAxL0J5aXhtSzdPbUJrc0FTQzhIK2ZBTXJMUTJ1Tk40MmVhVlNyekpiRWI2QkhJV3pZb21YRVN0ZjRnVmpVNGxVbWpIcEZxazh5OEF0d2hJTGppVXdNRG9XUlJhbWZZTCtlQk9PSlRBazZ5LzEwVjhlcEw4OFdIKzVqLzdWUWZwWEIrdGY1U0lEZ3loWFFBdjV5S3dWcDBpNlIrbkh4ZmF6bEk4eFJGWmR2TGRrMVVuRFNzckhWTGNjYkc0TllBTGJrNFhkaXB6T1ZNRnJpSnU2SXFjekdtYkNJVzN3amxpSVVGSGxrUmlKMFVibDRxWWNpWkZrVm5EK09ZcW5HN29RY1RZdXhhbnNWdXBZbkJ4YkpoSloyRTJWeUZUcWEwU3B2eEdTdFNxUmhmV1BkRCtZUzlnSEhnbXZTeEJSTXB0S2lITFp1SzFMRWlJak8wbGV3Q0wvVEdHSWRjb1VQcWRnK2VZSUZ0dFFDQVR1elFTVFdPVUxMZ2d1eCtESzM0RFdvbnNOdXIyVGtQZ2JnOGl5NkpicldEaDY0T3VDbHZTeXVDeGpRWWNucElzamV2S3I2SXFjaVZFelQwNnk0NXMrbmtLZE54cGU2dUhTVUlNY0RnNDNPazUwVUFCY0M5QXpqTENrOFJlUTB4amxuRFhqdUVad1ovZDRGMFIzTlJPZXI3dSt4bHlJVGFKbmRHUmg2Tkg5SnBlMmtPMEIzWWR2UzBTRmJjS1g3bzRWdFdNaTZMY0cybHJTbmtLSUFkRDd0RUhqZ1Z5VGFsQURkVm9ITk5DZEF3bzJML0FRVVFHblkvRmlkUWJZUmxnUDI0SnBoS0lnMDlCTkptbVdhVjJERXhaN2N6alBRTUk5RmNIUXk1dm9vRnhJRE52b3dDMC9EYXNBSis1RHFYT3dTNkxUZ0xtUUhoMEEwazRNQ2VIUlZvbGN1eDROVWRnV2FHT3dKckdYUGdzaGxkN0VJaVA1ZXVMWHByaFY0VDFnTUhTc0oybHY0T3B3YTEwZEdzT2NaQ3hTWStJMExCbmMyNFo5d1ZxekdLUEdEQXJyRkR0c0lhcFNKQjFoZXNBeVFubmFrQVdlR1BpUHhHWHNsbTBpZGg4M0p0eUVqbktCTVJJY0Q1T1E4am93UWpqTEpzTGpZd1laTTZ3bmd0YVRzZXc2RHJuYXpucGQxOVRwV0J4Rzh3dDU3bG5VVFJQNGxGeW5SNUVUK0dDY1FmQVFqUWJoVkhqTnpvM2NLWDNUUWE1aXg5Vm9lSlJFdWdzZkxEMEdYQTlzYXpaYzdDaHRORHdrSVp6NHlFVEdPVVpPYkVpSTBCTWNHZmN3YzhBMnpCeVZUVVJEaFRvc25CMm9ZTlNNY1d4NGxFT0I3WXZ5TEtnUkZCcG1seWVaYVVQUndtYnF0cTk3MHJkcmdSUWxlbUFDYlEvbW93elRzdFBoeGFDN0hUaEEwWEVUZnJzblhRQmZXcU9icnJGci9NM1hYRkJ1QXoxY3dIVzZsQzVnZ21IRlNGTUJpVjgvc2dGbTBuU0xhMHdIWllNdEtseU8rS3laY2RmcEZVam1ERTNmQ1JNSE9jWjVPTmVqdTlsd29vVGhDVU0rVEVvaUhFczBTL1V1UlYycmxsYXJxcXFjdm1kRFVEUWRLVUlMQXE5akRuV0Zzcm10Qk4rRzd1dUNkQTVLbTdyblg5YndSYkdnWUdLdFVDeW9oWFZWTFFtU2M0WGdLQTNPbmdVUHRFd1htQ2pBOGVjTi9NbHh1VVAvMjlrL1FyWlNtZ3gwYzVPQll2bGVhWFlRcmpyTkRnbzUwdXlnTkRzb3pRNUtzNFBTN0tCK29aVm1CNlhaUVdsMjBPRHNJT0czRDlKa29UUlpLTVRUWktFMFdTaE5Ga3FUaGRKa29UUlpLRTBXd2d4cHNsQ2FMSlJVWFpvc2xDWUxwY2xDTWRrMFdTaE5Ga3FUaGRKa29UUlpLRTBXNHBPRmhMOTBrdVlPNFVra3pSMTZDN2xESTQxVytML0s1Umh3QWlYdEZFeFhELzRVbVpoRmxIV0NzeWtvTkxTQW1pWUlIM0lGWUxackk2Y2IrVWF6YTEvTnJ3dmt3eDE3QzlXWkNmL25OL1F6alorSG9tZjAzK3doSzRiSVg1RWFKWjZGdTQxb0VJKzA5RTJhczNIWUFHU0puM0ZoTUtJTXFVTEh0ZWhDTUFGUnI4RE9GQk1OcDBVUW5GSDBQOTRyRVBBVWNBQUEifQ== -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["penalty"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["success"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["play_type"],"name":[4],"type":["chr"],"align":["left"]},{"label":["play_id"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["game_id"],"name":[6],"type":["chr"],"align":["left"]},{"label":["old_game_id"],"name":[7],"type":["chr"],"align":["left"]},{"label":["home_team"],"name":[8],"type":["chr"],"align":["left"]},{"label":["away_team"],"name":[9],"type":["chr"],"align":["left"]},{"label":["season_type"],"name":[10],"type":["chr"],"align":["left"]},{"label":["week"],"name":[11],"type":["int"],"align":["right"]},{"label":["posteam_type"],"name":[12],"type":["chr"],"align":["left"]},{"label":["defteam"],"name":[13],"type":["chr"],"align":["left"]},{"label":["side_of_field"],"name":[14],"type":["chr"],"align":["left"]},{"label":["yardline_100"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["game_date"],"name":[16],"type":["chr"],"align":["left"]},{"label":["quarter_seconds_remaining"],"name":[17],"type":["dbl"],"align":["right"]},{"label":["half_seconds_remaining"],"name":[18],"type":["dbl"],"align":["right"]},{"label":["game_seconds_remaining"],"name":[19],"type":["dbl"],"align":["right"]},{"label":["game_half"],"name":[20],"type":["chr"],"align":["left"]},{"label":["quarter_end"],"name":[21],"type":["dbl"],"align":["right"]},{"label":["drive"],"name":[22],"type":["dbl"],"align":["right"]},{"label":["sp"],"name":[23],"type":["dbl"],"align":["right"]},{"label":["qtr"],"name":[24],"type":["dbl"],"align":["right"]},{"label":["down"],"name":[25],"type":["dbl"],"align":["right"]},{"label":["goal_to_go"],"name":[26],"type":["int"],"align":["right"]},{"label":["time"],"name":[27],"type":["chr"],"align":["left"]},{"label":["yrdln"],"name":[28],"type":["chr"],"align":["left"]},{"label":["ydstogo"],"name":[29],"type":["dbl"],"align":["right"]},{"label":["ydsnet"],"name":[30],"type":["dbl"],"align":["right"]},{"label":["desc"],"name":[31],"type":["chr"],"align":["left"]},{"label":["yards_gained"],"name":[32],"type":["dbl"],"align":["right"]},{"label":["shotgun"],"name":[33],"type":["dbl"],"align":["right"]},{"label":["no_huddle"],"name":[34],"type":["dbl"],"align":["right"]},{"label":["qb_dropback"],"name":[35],"type":["dbl"],"align":["right"]},{"label":["qb_kneel"],"name":[36],"type":["dbl"],"align":["right"]},{"label":["qb_spike"],"name":[37],"type":["dbl"],"align":["right"]},{"label":["qb_scramble"],"name":[38],"type":["dbl"],"align":["right"]},{"label":["pass_length"],"name":[39],"type":["chr"],"align":["left"]},{"label":["pass_location"],"name":[40],"type":["chr"],"align":["left"]},{"label":["air_yards"],"name":[41],"type":["dbl"],"align":["right"]},{"label":["yards_after_catch"],"name":[42],"type":["dbl"],"align":["right"]},{"label":["run_location"],"name":[43],"type":["chr"],"align":["left"]},{"label":["run_gap"],"name":[44],"type":["chr"],"align":["left"]},{"label":["field_goal_result"],"name":[45],"type":["chr"],"align":["left"]},{"label":["kick_distance"],"name":[46],"type":["dbl"],"align":["right"]},{"label":["extra_point_result"],"name":[47],"type":["chr"],"align":["left"]},{"label":["two_point_conv_result"],"name":[48],"type":["chr"],"align":["left"]},{"label":["home_timeouts_remaining"],"name":[49],"type":["dbl"],"align":["right"]},{"label":["away_timeouts_remaining"],"name":[50],"type":["dbl"],"align":["right"]},{"label":["timeout"],"name":[51],"type":["dbl"],"align":["right"]},{"label":["timeout_team"],"name":[52],"type":["chr"],"align":["left"]},{"label":["td_team"],"name":[53],"type":["chr"],"align":["left"]},{"label":["td_player_name"],"name":[54],"type":["chr"],"align":["left"]},{"label":["td_player_id"],"name":[55],"type":["chr"],"align":["left"]},{"label":["posteam_timeouts_remaining"],"name":[56],"type":["dbl"],"align":["right"]},{"label":["defteam_timeouts_remaining"],"name":[57],"type":["dbl"],"align":["right"]},{"label":["total_home_score"],"name":[58],"type":["dbl"],"align":["right"]},{"label":["total_away_score"],"name":[59],"type":["dbl"],"align":["right"]},{"label":["posteam_score"],"name":[60],"type":["dbl"],"align":["right"]},{"label":["defteam_score"],"name":[61],"type":["dbl"],"align":["right"]},{"label":["score_differential"],"name":[62],"type":["dbl"],"align":["right"]},{"label":["posteam_score_post"],"name":[63],"type":["dbl"],"align":["right"]},{"label":["defteam_score_post"],"name":[64],"type":["dbl"],"align":["right"]},{"label":["score_differential_post"],"name":[65],"type":["dbl"],"align":["right"]},{"label":["no_score_prob"],"name":[66],"type":["dbl"],"align":["right"]},{"label":["opp_fg_prob"],"name":[67],"type":["dbl"],"align":["right"]},{"label":["opp_safety_prob"],"name":[68],"type":["dbl"],"align":["right"]},{"label":["opp_td_prob"],"name":[69],"type":["dbl"],"align":["right"]},{"label":["fg_prob"],"name":[70],"type":["dbl"],"align":["right"]},{"label":["safety_prob"],"name":[71],"type":["dbl"],"align":["right"]},{"label":["td_prob"],"name":[72],"type":["dbl"],"align":["right"]},{"label":["extra_point_prob"],"name":[73],"type":["dbl"],"align":["right"]},{"label":["two_point_conversion_prob"],"name":[74],"type":["dbl"],"align":["right"]},{"label":["ep"],"name":[75],"type":["dbl"],"align":["right"]},{"label":["epa"],"name":[76],"type":["dbl"],"align":["right"]},{"label":["total_home_epa"],"name":[77],"type":["dbl"],"align":["right"]},{"label":["total_away_epa"],"name":[78],"type":["dbl"],"align":["right"]},{"label":["total_home_rush_epa"],"name":[79],"type":["dbl"],"align":["right"]},{"label":["total_away_rush_epa"],"name":[80],"type":["dbl"],"align":["right"]},{"label":["total_home_pass_epa"],"name":[81],"type":["dbl"],"align":["right"]},{"label":["total_away_pass_epa"],"name":[82],"type":["dbl"],"align":["right"]},{"label":["air_epa"],"name":[83],"type":["dbl"],"align":["right"]},{"label":["yac_epa"],"name":[84],"type":["dbl"],"align":["right"]},{"label":["comp_air_epa"],"name":[85],"type":["dbl"],"align":["right"]},{"label":["comp_yac_epa"],"name":[86],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_air_epa"],"name":[87],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_air_epa"],"name":[88],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_yac_epa"],"name":[89],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_yac_epa"],"name":[90],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_air_epa"],"name":[91],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_air_epa"],"name":[92],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_yac_epa"],"name":[93],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_yac_epa"],"name":[94],"type":["dbl"],"align":["right"]},{"label":["wp"],"name":[95],"type":["dbl"],"align":["right"]},{"label":["def_wp"],"name":[96],"type":["dbl"],"align":["right"]},{"label":["home_wp"],"name":[97],"type":["dbl"],"align":["right"]},{"label":["away_wp"],"name":[98],"type":["dbl"],"align":["right"]},{"label":["wpa"],"name":[99],"type":["dbl"],"align":["right"]},{"label":["vegas_wpa"],"name":[100],"type":["dbl"],"align":["right"]},{"label":["vegas_home_wpa"],"name":[101],"type":["dbl"],"align":["right"]},{"label":["home_wp_post"],"name":[102],"type":["dbl"],"align":["right"]},{"label":["away_wp_post"],"name":[103],"type":["dbl"],"align":["right"]},{"label":["vegas_wp"],"name":[104],"type":["dbl"],"align":["right"]},{"label":["vegas_home_wp"],"name":[105],"type":["dbl"],"align":["right"]},{"label":["total_home_rush_wpa"],"name":[106],"type":["dbl"],"align":["right"]},{"label":["total_away_rush_wpa"],"name":[107],"type":["dbl"],"align":["right"]},{"label":["total_home_pass_wpa"],"name":[108],"type":["dbl"],"align":["right"]},{"label":["total_away_pass_wpa"],"name":[109],"type":["dbl"],"align":["right"]},{"label":["air_wpa"],"name":[110],"type":["dbl"],"align":["right"]},{"label":["yac_wpa"],"name":[111],"type":["dbl"],"align":["right"]},{"label":["comp_air_wpa"],"name":[112],"type":["dbl"],"align":["right"]},{"label":["comp_yac_wpa"],"name":[113],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_air_wpa"],"name":[114],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_air_wpa"],"name":[115],"type":["dbl"],"align":["right"]},{"label":["total_home_comp_yac_wpa"],"name":[116],"type":["dbl"],"align":["right"]},{"label":["total_away_comp_yac_wpa"],"name":[117],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_air_wpa"],"name":[118],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_air_wpa"],"name":[119],"type":["dbl"],"align":["right"]},{"label":["total_home_raw_yac_wpa"],"name":[120],"type":["dbl"],"align":["right"]},{"label":["total_away_raw_yac_wpa"],"name":[121],"type":["dbl"],"align":["right"]},{"label":["punt_blocked"],"name":[122],"type":["dbl"],"align":["right"]},{"label":["first_down_rush"],"name":[123],"type":["dbl"],"align":["right"]},{"label":["first_down_pass"],"name":[124],"type":["dbl"],"align":["right"]},{"label":["first_down_penalty"],"name":[125],"type":["dbl"],"align":["right"]},{"label":["third_down_converted"],"name":[126],"type":["dbl"],"align":["right"]},{"label":["third_down_failed"],"name":[127],"type":["dbl"],"align":["right"]},{"label":["fourth_down_converted"],"name":[128],"type":["dbl"],"align":["right"]},{"label":["fourth_down_failed"],"name":[129],"type":["dbl"],"align":["right"]},{"label":["incomplete_pass"],"name":[130],"type":["dbl"],"align":["right"]},{"label":["touchback"],"name":[131],"type":["dbl"],"align":["right"]},{"label":["interception"],"name":[132],"type":["dbl"],"align":["right"]},{"label":["punt_inside_twenty"],"name":[133],"type":["dbl"],"align":["right"]},{"label":["punt_in_endzone"],"name":[134],"type":["dbl"],"align":["right"]},{"label":["punt_out_of_bounds"],"name":[135],"type":["dbl"],"align":["right"]},{"label":["punt_downed"],"name":[136],"type":["dbl"],"align":["right"]},{"label":["punt_fair_catch"],"name":[137],"type":["dbl"],"align":["right"]},{"label":["kickoff_inside_twenty"],"name":[138],"type":["dbl"],"align":["right"]},{"label":["kickoff_in_endzone"],"name":[139],"type":["dbl"],"align":["right"]},{"label":["kickoff_out_of_bounds"],"name":[140],"type":["dbl"],"align":["right"]},{"label":["kickoff_downed"],"name":[141],"type":["dbl"],"align":["right"]},{"label":["kickoff_fair_catch"],"name":[142],"type":["dbl"],"align":["right"]},{"label":["fumble_forced"],"name":[143],"type":["dbl"],"align":["right"]},{"label":["fumble_not_forced"],"name":[144],"type":["dbl"],"align":["right"]},{"label":["fumble_out_of_bounds"],"name":[145],"type":["dbl"],"align":["right"]},{"label":["solo_tackle"],"name":[146],"type":["dbl"],"align":["right"]},{"label":["safety"],"name":[147],"type":["dbl"],"align":["right"]},{"label":["tackled_for_loss"],"name":[148],"type":["dbl"],"align":["right"]},{"label":["fumble_lost"],"name":[149],"type":["dbl"],"align":["right"]},{"label":["own_kickoff_recovery"],"name":[150],"type":["dbl"],"align":["right"]},{"label":["own_kickoff_recovery_td"],"name":[151],"type":["dbl"],"align":["right"]},{"label":["qb_hit"],"name":[152],"type":["dbl"],"align":["right"]},{"label":["rush_attempt"],"name":[153],"type":["dbl"],"align":["right"]},{"label":["pass_attempt"],"name":[154],"type":["dbl"],"align":["right"]},{"label":["sack"],"name":[155],"type":["dbl"],"align":["right"]},{"label":["touchdown"],"name":[156],"type":["dbl"],"align":["right"]},{"label":["pass_touchdown"],"name":[157],"type":["dbl"],"align":["right"]},{"label":["rush_touchdown"],"name":[158],"type":["dbl"],"align":["right"]},{"label":["return_touchdown"],"name":[159],"type":["dbl"],"align":["right"]},{"label":["extra_point_attempt"],"name":[160],"type":["dbl"],"align":["right"]},{"label":["two_point_attempt"],"name":[161],"type":["dbl"],"align":["right"]},{"label":["field_goal_attempt"],"name":[162],"type":["dbl"],"align":["right"]},{"label":["kickoff_attempt"],"name":[163],"type":["dbl"],"align":["right"]},{"label":["punt_attempt"],"name":[164],"type":["dbl"],"align":["right"]},{"label":["fumble"],"name":[165],"type":["dbl"],"align":["right"]},{"label":["complete_pass"],"name":[166],"type":["dbl"],"align":["right"]},{"label":["assist_tackle"],"name":[167],"type":["dbl"],"align":["right"]},{"label":["lateral_reception"],"name":[168],"type":["dbl"],"align":["right"]},{"label":["lateral_rush"],"name":[169],"type":["dbl"],"align":["right"]},{"label":["lateral_return"],"name":[170],"type":["dbl"],"align":["right"]},{"label":["lateral_recovery"],"name":[171],"type":["dbl"],"align":["right"]},{"label":["passer_player_id"],"name":[172],"type":["chr"],"align":["left"]},{"label":["passer_player_name"],"name":[173],"type":["chr"],"align":["left"]},{"label":["passing_yards"],"name":[174],"type":["dbl"],"align":["right"]},{"label":["receiver_player_id"],"name":[175],"type":["chr"],"align":["left"]},{"label":["receiver_player_name"],"name":[176],"type":["chr"],"align":["left"]},{"label":["receiving_yards"],"name":[177],"type":["dbl"],"align":["right"]},{"label":["rusher_player_id"],"name":[178],"type":["chr"],"align":["left"]},{"label":["rusher_player_name"],"name":[179],"type":["chr"],"align":["left"]},{"label":["rushing_yards"],"name":[180],"type":["dbl"],"align":["right"]},{"label":["lateral_receiver_player_id"],"name":[181],"type":["chr"],"align":["left"]},{"label":["lateral_receiver_player_name"],"name":[182],"type":["chr"],"align":["left"]},{"label":["lateral_receiving_yards"],"name":[183],"type":["dbl"],"align":["right"]},{"label":["lateral_rusher_player_id"],"name":[184],"type":["chr"],"align":["left"]},{"label":["lateral_rusher_player_name"],"name":[185],"type":["chr"],"align":["left"]},{"label":["lateral_rushing_yards"],"name":[186],"type":["dbl"],"align":["right"]},{"label":["lateral_sack_player_id"],"name":[187],"type":["chr"],"align":["left"]},{"label":["lateral_sack_player_name"],"name":[188],"type":["chr"],"align":["left"]},{"label":["interception_player_id"],"name":[189],"type":["chr"],"align":["left"]},{"label":["interception_player_name"],"name":[190],"type":["chr"],"align":["left"]},{"label":["lateral_interception_player_id"],"name":[191],"type":["chr"],"align":["left"]},{"label":["lateral_interception_player_name"],"name":[192],"type":["chr"],"align":["left"]},{"label":["punt_returner_player_id"],"name":[193],"type":["chr"],"align":["left"]},{"label":["punt_returner_player_name"],"name":[194],"type":["chr"],"align":["left"]},{"label":["lateral_punt_returner_player_id"],"name":[195],"type":["chr"],"align":["left"]},{"label":["lateral_punt_returner_player_name"],"name":[196],"type":["chr"],"align":["left"]},{"label":["kickoff_returner_player_name"],"name":[197],"type":["chr"],"align":["left"]},{"label":["kickoff_returner_player_id"],"name":[198],"type":["chr"],"align":["left"]},{"label":["lateral_kickoff_returner_player_id"],"name":[199],"type":["chr"],"align":["left"]},{"label":["lateral_kickoff_returner_player_name"],"name":[200],"type":["chr"],"align":["left"]},{"label":["punter_player_id"],"name":[201],"type":["chr"],"align":["left"]},{"label":["punter_player_name"],"name":[202],"type":["chr"],"align":["left"]},{"label":["kicker_player_name"],"name":[203],"type":["chr"],"align":["left"]},{"label":["kicker_player_id"],"name":[204],"type":["chr"],"align":["left"]},{"label":["own_kickoff_recovery_player_id"],"name":[205],"type":["chr"],"align":["left"]},{"label":["own_kickoff_recovery_player_name"],"name":[206],"type":["chr"],"align":["left"]},{"label":["blocked_player_id"],"name":[207],"type":["chr"],"align":["left"]},{"label":["blocked_player_name"],"name":[208],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_1_player_id"],"name":[209],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_1_player_name"],"name":[210],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_2_player_id"],"name":[211],"type":["chr"],"align":["left"]},{"label":["tackle_for_loss_2_player_name"],"name":[212],"type":["chr"],"align":["left"]},{"label":["qb_hit_1_player_id"],"name":[213],"type":["chr"],"align":["left"]},{"label":["qb_hit_1_player_name"],"name":[214],"type":["chr"],"align":["left"]},{"label":["qb_hit_2_player_id"],"name":[215],"type":["chr"],"align":["left"]},{"label":["qb_hit_2_player_name"],"name":[216],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_team"],"name":[217],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_player_id"],"name":[218],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_1_player_name"],"name":[219],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_team"],"name":[220],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_player_id"],"name":[221],"type":["chr"],"align":["left"]},{"label":["forced_fumble_player_2_player_name"],"name":[222],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_team"],"name":[223],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_team"],"name":[224],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_player_id"],"name":[225],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_player_id"],"name":[226],"type":["chr"],"align":["left"]},{"label":["solo_tackle_1_player_name"],"name":[227],"type":["chr"],"align":["left"]},{"label":["solo_tackle_2_player_name"],"name":[228],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_player_id"],"name":[229],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_player_name"],"name":[230],"type":["chr"],"align":["left"]},{"label":["assist_tackle_1_team"],"name":[231],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_player_id"],"name":[232],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_player_name"],"name":[233],"type":["chr"],"align":["left"]},{"label":["assist_tackle_2_team"],"name":[234],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_player_id"],"name":[235],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_player_name"],"name":[236],"type":["chr"],"align":["left"]},{"label":["assist_tackle_3_team"],"name":[237],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_player_id"],"name":[238],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_player_name"],"name":[239],"type":["chr"],"align":["left"]},{"label":["assist_tackle_4_team"],"name":[240],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist"],"name":[241],"type":["dbl"],"align":["right"]},{"label":["tackle_with_assist_1_player_id"],"name":[242],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_1_player_name"],"name":[243],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_1_team"],"name":[244],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_player_id"],"name":[245],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_player_name"],"name":[246],"type":["chr"],"align":["left"]},{"label":["tackle_with_assist_2_team"],"name":[247],"type":["chr"],"align":["left"]},{"label":["pass_defense_1_player_id"],"name":[248],"type":["chr"],"align":["left"]},{"label":["pass_defense_1_player_name"],"name":[249],"type":["chr"],"align":["left"]},{"label":["pass_defense_2_player_id"],"name":[250],"type":["chr"],"align":["left"]},{"label":["pass_defense_2_player_name"],"name":[251],"type":["chr"],"align":["left"]},{"label":["fumbled_1_team"],"name":[252],"type":["chr"],"align":["left"]},{"label":["fumbled_1_player_id"],"name":[253],"type":["chr"],"align":["left"]},{"label":["fumbled_1_player_name"],"name":[254],"type":["chr"],"align":["left"]},{"label":["fumbled_2_player_id"],"name":[255],"type":["chr"],"align":["left"]},{"label":["fumbled_2_player_name"],"name":[256],"type":["chr"],"align":["left"]},{"label":["fumbled_2_team"],"name":[257],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_team"],"name":[258],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_yards"],"name":[259],"type":["dbl"],"align":["right"]},{"label":["fumble_recovery_1_player_id"],"name":[260],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_1_player_name"],"name":[261],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_team"],"name":[262],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_yards"],"name":[263],"type":["dbl"],"align":["right"]},{"label":["fumble_recovery_2_player_id"],"name":[264],"type":["chr"],"align":["left"]},{"label":["fumble_recovery_2_player_name"],"name":[265],"type":["chr"],"align":["left"]},{"label":["sack_player_id"],"name":[266],"type":["chr"],"align":["left"]},{"label":["sack_player_name"],"name":[267],"type":["chr"],"align":["left"]},{"label":["half_sack_1_player_id"],"name":[268],"type":["chr"],"align":["left"]},{"label":["half_sack_1_player_name"],"name":[269],"type":["chr"],"align":["left"]},{"label":["half_sack_2_player_id"],"name":[270],"type":["chr"],"align":["left"]},{"label":["half_sack_2_player_name"],"name":[271],"type":["chr"],"align":["left"]},{"label":["return_team"],"name":[272],"type":["chr"],"align":["left"]},{"label":["return_yards"],"name":[273],"type":["dbl"],"align":["right"]},{"label":["penalty_team"],"name":[274],"type":["chr"],"align":["left"]},{"label":["penalty_player_id"],"name":[275],"type":["chr"],"align":["left"]},{"label":["penalty_player_name"],"name":[276],"type":["chr"],"align":["left"]},{"label":["penalty_yards"],"name":[277],"type":["dbl"],"align":["right"]},{"label":["replay_or_challenge"],"name":[278],"type":["dbl"],"align":["right"]},{"label":["replay_or_challenge_result"],"name":[279],"type":["chr"],"align":["left"]},{"label":["penalty_type"],"name":[280],"type":["chr"],"align":["left"]},{"label":["defensive_two_point_attempt"],"name":[281],"type":["dbl"],"align":["right"]},{"label":["defensive_two_point_conv"],"name":[282],"type":["dbl"],"align":["right"]},{"label":["defensive_extra_point_attempt"],"name":[283],"type":["dbl"],"align":["right"]},{"label":["defensive_extra_point_conv"],"name":[284],"type":["dbl"],"align":["right"]},{"label":["safety_player_name"],"name":[285],"type":["chr"],"align":["left"]},{"label":["safety_player_id"],"name":[286],"type":["chr"],"align":["left"]},{"label":["season"],"name":[287],"type":["int"],"align":["right"]},{"label":["cp"],"name":[288],"type":["dbl"],"align":["right"]},{"label":["cpoe"],"name":[289],"type":["dbl"],"align":["right"]},{"label":["series"],"name":[290],"type":["dbl"],"align":["right"]},{"label":["series_success"],"name":[291],"type":["dbl"],"align":["right"]},{"label":["series_result"],"name":[292],"type":["chr"],"align":["left"]},{"label":["order_sequence"],"name":[293],"type":["dbl"],"align":["right"]},{"label":["start_time"],"name":[294],"type":["chr"],"align":["left"]},{"label":["time_of_day"],"name":[295],"type":["chr"],"align":["left"]},{"label":["stadium"],"name":[296],"type":["chr"],"align":["left"]},{"label":["weather"],"name":[297],"type":["chr"],"align":["left"]},{"label":["nfl_api_id"],"name":[298],"type":["chr"],"align":["left"]},{"label":["play_clock"],"name":[299],"type":["chr"],"align":["left"]},{"label":["play_deleted"],"name":[300],"type":["dbl"],"align":["right"]},{"label":["play_type_nfl"],"name":[301],"type":["chr"],"align":["left"]},{"label":["special_teams_play"],"name":[302],"type":["dbl"],"align":["right"]},{"label":["st_play_type"],"name":[303],"type":["chr"],"align":["left"]},{"label":["end_clock_time"],"name":[304],"type":["chr"],"align":["left"]},{"label":["end_yard_line"],"name":[305],"type":["chr"],"align":["left"]},{"label":["fixed_drive"],"name":[306],"type":["dbl"],"align":["right"]},{"label":["fixed_drive_result"],"name":[307],"type":["chr"],"align":["left"]},{"label":["drive_real_start_time"],"name":[308],"type":["chr"],"align":["left"]},{"label":["drive_play_count"],"name":[309],"type":["dbl"],"align":["right"]},{"label":["drive_time_of_possession"],"name":[310],"type":["chr"],"align":["left"]},{"label":["drive_first_downs"],"name":[311],"type":["dbl"],"align":["right"]},{"label":["drive_inside20"],"name":[312],"type":["dbl"],"align":["right"]},{"label":["drive_ended_with_score"],"name":[313],"type":["dbl"],"align":["right"]},{"label":["drive_quarter_start"],"name":[314],"type":["dbl"],"align":["right"]},{"label":["drive_quarter_end"],"name":[315],"type":["dbl"],"align":["right"]},{"label":["drive_yards_penalized"],"name":[316],"type":["dbl"],"align":["right"]},{"label":["drive_start_transition"],"name":[317],"type":["chr"],"align":["left"]},{"label":["drive_end_transition"],"name":[318],"type":["chr"],"align":["left"]},{"label":["drive_game_clock_start"],"name":[319],"type":["chr"],"align":["left"]},{"label":["drive_game_clock_end"],"name":[320],"type":["chr"],"align":["left"]},{"label":["drive_start_yard_line"],"name":[321],"type":["chr"],"align":["left"]},{"label":["drive_end_yard_line"],"name":[322],"type":["chr"],"align":["left"]},{"label":["drive_play_id_started"],"name":[323],"type":["dbl"],"align":["right"]},{"label":["drive_play_id_ended"],"name":[324],"type":["dbl"],"align":["right"]},{"label":["away_score"],"name":[325],"type":["int"],"align":["right"]},{"label":["home_score"],"name":[326],"type":["int"],"align":["right"]},{"label":["location"],"name":[327],"type":["chr"],"align":["left"]},{"label":["result"],"name":[328],"type":["int"],"align":["right"]},{"label":["total"],"name":[329],"type":["int"],"align":["right"]},{"label":["spread_line"],"name":[330],"type":["dbl"],"align":["right"]},{"label":["total_line"],"name":[331],"type":["dbl"],"align":["right"]},{"label":["div_game"],"name":[332],"type":["int"],"align":["right"]},{"label":["roof"],"name":[333],"type":["chr"],"align":["left"]},{"label":["surface"],"name":[334],"type":["chr"],"align":["left"]},{"label":["temp"],"name":[335],"type":["int"],"align":["right"]},{"label":["wind"],"name":[336],"type":["int"],"align":["right"]},{"label":["home_coach"],"name":[337],"type":["chr"],"align":["left"]},{"label":["away_coach"],"name":[338],"type":["chr"],"align":["left"]},{"label":["stadium_id"],"name":[339],"type":["chr"],"align":["left"]},{"label":["game_stadium"],"name":[340],"type":["chr"],"align":["left"]},{"label":["aborted_play"],"name":[341],"type":["dbl"],"align":["right"]},{"label":["passer"],"name":[342],"type":["chr"],"align":["left"]},{"label":["passer_jersey_number"],"name":[343],"type":["int"],"align":["right"]},{"label":["rusher"],"name":[344],"type":["chr"],"align":["left"]},{"label":["rusher_jersey_number"],"name":[345],"type":["int"],"align":["right"]},{"label":["receiver"],"name":[346],"type":["chr"],"align":["left"]},{"label":["receiver_jersey_number"],"name":[347],"type":["int"],"align":["right"]},{"label":["pass"],"name":[348],"type":["dbl"],"align":["right"]},{"label":["rush"],"name":[349],"type":["dbl"],"align":["right"]},{"label":["first_down"],"name":[350],"type":["dbl"],"align":["right"]},{"label":["special"],"name":[351],"type":["dbl"],"align":["right"]},{"label":["play"],"name":[352],"type":["dbl"],"align":["right"]},{"label":["passer_id"],"name":[353],"type":["chr"],"align":["left"]},{"label":["rusher_id"],"name":[354],"type":["chr"],"align":["left"]},{"label":["receiver_id"],"name":[355],"type":["chr"],"align":["left"]},{"label":["name"],"name":[356],"type":["chr"],"align":["left"]},{"label":["jersey_number"],"name":[357],"type":["int"],"align":["right"]},{"label":["id"],"name":[358],"type":["chr"],"align":["left"]},{"label":["fantasy_player_name"],"name":[359],"type":["chr"],"align":["left"]},{"label":["fantasy_player_id"],"name":[360],"type":["chr"],"align":["left"]},{"label":["fantasy"],"name":[361],"type":["chr"],"align":["left"]},{"label":["fantasy_id"],"name":[362],"type":["chr"],"align":["left"]},{"label":["out_of_bounds"],"name":[363],"type":["dbl"],"align":["right"]},{"label":["home_opening_kickoff"],"name":[364],"type":["dbl"],"align":["right"]},{"label":["qb_epa"],"name":[365],"type":["dbl"],"align":["right"]},{"label":["xyac_epa"],"name":[366],"type":["dbl"],"align":["right"]},{"label":["xyac_mean_yardage"],"name":[367],"type":["dbl"],"align":["right"]},{"label":["xyac_median_yardage"],"name":[368],"type":["int"],"align":["right"]},{"label":["xyac_success"],"name":[369],"type":["dbl"],"align":["right"]},{"label":["xyac_fd"],"name":[370],"type":["dbl"],"align":["right"]},{"label":["xpass"],"name":[371],"type":["dbl"],"align":["right"]},{"label":["pass_oe"],"name":[372],"type":["dbl"],"align":["right"]}],"data":[{"1":"NYJ","2":"0","3":"0","4":"run","5":"774","6":"2025_01_PIT_NYJ","7":"2025090706","8":"NYJ","9":"PIT","10":"REG","11":"1","12":"home","13":"PIT","14":"PIT","15":"1","16":"2025-09-07","17":"25","18":"925","19":"2725","20":"Half1","21":"0","22":"3","23":"0","24":"1","25":"NA","26":"0","27":"00:25","28":"PIT 1","29":"0","30":"55","31":"TWO-POINT CONVERSION ATTEMPT. 0-B.Allen rushes up the middle. ATTEMPT FAILS.","32":"0","33":"0","34":"0","35":"0","36":"0","37":"0","38":"0","39":"NA","40":"NA","41":"NA","42":"NA","43":"NA","44":"NA","45":"NA","46":"NA","47":"NA","48":"failure","49":"3","50":"3","51":"0","52":"NA","53":"NA","54":"NA","55":"NA","56":"3","57":"3","58":"9","59":"7","60":"9","61":"7","62":"2","63":"9","64":"7","65":"2","66":"0","67":"0","68":"0","69":"0","70":"0","71":"0","72":"0","73":"0","74":"0.4735","75":"0.947","76":"-0.947","77":"-0.002858637","78":"0.002858637","79":"-0.4352666","80":"0.4352666","81":"-1.463799","82":"1.463799","83":"NA","84":"NA","85":"0","86":"0","87":"4.977137","88":"-4.977137","89":"-8.46164","90":"8.46164","91":"5.696594","92":"-5.696594","93":"-8.342536","94":"8.342536","95":"0.5939896","96":"0.4060104","97":"0.5939896","98":"0.4060104","99":"-0.03102132","100":"-0.02313234","101":"-0.02313234","102":"0.5629683","103":"0.4370317","104":"0.4611691","105":"0.4611691","106":"-0.03808304","107":"0.03808304","108":"-0.008565545","109":"0.008565545","110":"NA","111":"NA","112":"0","113":"0","114":"0.06090823","115":"-0.06090823","116":"-0.13196024","117":"0.13196024","118":"0.06090823","119":"-0.06090823","120":"-0.09944114","121":"0.09944114","122":"0","123":"0","124":"0","125":"0","126":"0","127":"0","128":"0","129":"0","130":"0","131":"0","132":"0","133":"0","134":"0","135":"0","136":"0","137":"0","138":"0","139":"0","140":"0","141":"0","142":"0","143":"0","144":"0","145":"0","146":"0","147":"0","148":"0","149":"0","150":"0","151":"0","152":"0","153":"1","154":"0","155":"0","156":"0","157":"0","158":"0","159":"0","160":"0","161":"1","162":"0","163":"0","164":"0","165":"0","166":"0","167":"0","168":"0","169":"0","170":"0","171":"0","172":"NA","173":"NA","174":"NA","175":"NA","176":"NA","177":"NA","178":"00-0039794","179":"B.Allen","180":"NA","181":"NA","182":"NA","183":"NA","184":"NA","185":"NA","186":"NA","187":"NA","188":"NA","189":"NA","190":"NA","191":"NA","192":"NA","193":"NA","194":"NA","195":"NA","196":"NA","197":"NA","198":"NA","199":"NA","200":"NA","201":"NA","202":"NA","203":"NA","204":"NA","205":"NA","206":"NA","207":"NA","208":"NA","209":"NA","210":"NA","211":"NA","212":"NA","213":"NA","214":"NA","215":"NA","216":"NA","217":"NA","218":"NA","219":"NA","220":"NA","221":"NA","222":"NA","223":"NA","224":"NA","225":"NA","226":"NA","227":"NA","228":"NA","229":"NA","230":"NA","231":"NA","232":"NA","233":"NA","234":"NA","235":"NA","236":"NA","237":"NA","238":"NA","239":"NA","240":"NA","241":"0","242":"NA","243":"NA","244":"NA","245":"NA","246":"NA","247":"NA","248":"NA","249":"NA","250":"NA","251":"NA","252":"NA","253":"NA","254":"NA","255":"NA","256":"NA","257":"NA","258":"NA","259":"NA","260":"NA","261":"NA","262":"NA","263":"NA","264":"NA","265":"NA","266":"NA","267":"NA","268":"NA","269":"NA","270":"NA","271":"NA","272":"NA","273":"0","274":"NA","275":"NA","276":"NA","277":"NA","278":"0","279":"NA","280":"NA","281":"0","282":"0","283":"0","284":"0","285":"NA","286":"NA","287":"2025","288":"NA","289":"NA","290":"11","291":"1","292":"Touchdown","293":"774","294":"9/7/25, 13:02:43","295":"2025-09-07T17:29:11Z","296":"MetLife Stadium","297":"Cloudy with more rain possible Temp: 67° F, Humidity: 79%, Wind: W 3 mph","298":"f591a382-311e-11f0-b670-ae1250fadad1","299":"0","300":"0","301":"PAT2","302":"0","303":"NA","304":"NA","305":"NA","306":"3","307":"Touchdown","308":"2025-09-07T17:22:30.213Z","309":"6","310":"3:13","311":"3","312":"0","313":"1","314":"1","315":"1","316":"0","317":"KICKOFF","318":"TOUCHDOWN","319":"03:38","320":"00:25","321":"NYJ 45","322":"PIT 33","323":"566","324":"774","325":"34","326":"32","327":"Home","328":"-2","329":"66","330":"-3","331":"37.5","332":"0","333":"outdoors","334":"","335":"NA","336":"NA","337":"Aaron Glenn","338":"Mike Tomlin","339":"NYC01","340":"MetLife Stadium","341":"0","342":"NA","343":"NA","344":"B.Allen","345":"0","346":"NA","347":"NA","348":"0","349":"1","350":"0","351":"0","352":"1","353":"NA","354":"00-0039794","355":"NA","356":"B.Allen","357":"0","358":"00-0039794","359":"B.Allen","360":"00-0039794","361":"B.Allen","362":"00-0039794","363":"0","364":"1","365":"-0.947","366":"NA","367":"NA","368":"NA","369":"NA","370":"NA","371":"NA","372":"NA"},{"1":"NYJ","2":"0","3":"0","4":"pass","5":"3431","6":"2025_01_PIT_NYJ","7":"2025090706","8":"NYJ","9":"PIT","10":"REG","11":"1","12":"home","13":"PIT","14":"PIT","15":"2","16":"2025-09-07","17":"421","18":"421","19":"421","20":"Half2","21":"0","22":"17","23":"0","24":"4","25":"NA","26":"0","27":"07:01","28":"PIT 2","29":"0","30":"67","31":"TWO-POINT CONVERSION ATTEMPT. 7-J.Fields pass to 5-G.Wilson is incomplete. ATTEMPT FAILS. ** Injury Update: PIT-97-Ca.Heyward has returned to the game.","32":"0","33":"0","34":"0","35":"1","36":"0","37":"0","38":"0","39":"NA","40":"NA","41":"NA","42":"NA","43":"NA","44":"NA","45":"NA","46":"NA","47":"NA","48":"failure","49":"1","50":"2","51":"0","52":"NA","53":"NA","54":"NA","55":"NA","56":"1","57":"2","58":"32","59":"31","60":"32","61":"31","62":"1","63":"32","64":"31","65":"1","66":"0","67":"0","68":"0","69":"0","70":"0","71":"0","72":"0","73":"0","74":"0.4735","75":"0.947","76":"-0.947","77":"-0.568359249","78":"0.568359249","79":"5.9776684","80":"-5.9776684","81":"-1.700276","82":"1.700276","83":"NA","84":"NA","85":"0","86":"0","87":"12.659831","88":"-12.659831","89":"-18.32160","90":"18.32160","91":"11.618237","92":"-11.618237","93":"-15.046731","94":"15.046731","95":"0.5951446","96":"0.4048554","97":"0.5951446","98":"0.4048554","99":"-0.06411125","100":"-0.05554858","101":"-0.05554858","102":"0.5310334","103":"0.4689666","104":"0.5222623","105":"0.5222623","106":"0.17130893","107":"-0.17130893","108":"-0.020316217","109":"0.020316217","110":"NA","111":"NA","112":"0","113":"0","114":"-0.05747068","115":"0.05747068","116":"0.01023507","117":"-0.01023507","118":"-0.05747068","119":"0.05747068","120":"0.03477945","121":"-0.03477945","122":"0","123":"0","124":"0","125":"0","126":"0","127":"0","128":"0","129":"0","130":"0","131":"0","132":"0","133":"0","134":"0","135":"0","136":"0","137":"0","138":"0","139":"0","140":"0","141":"0","142":"0","143":"0","144":"0","145":"0","146":"0","147":"0","148":"0","149":"0","150":"0","151":"0","152":"0","153":"0","154":"1","155":"0","156":"0","157":"0","158":"0","159":"0","160":"0","161":"1","162":"0","163":"0","164":"0","165":"0","166":"0","167":"0","168":"0","169":"0","170":"0","171":"0","172":"00-0036945","173":"J.Fields","174":"NA","175":"00-0037740","176":"G.Wilson","177":"NA","178":"NA","179":"NA","180":"NA","181":"NA","182":"NA","183":"NA","184":"NA","185":"NA","186":"NA","187":"NA","188":"NA","189":"NA","190":"NA","191":"NA","192":"NA","193":"NA","194":"NA","195":"NA","196":"NA","197":"NA","198":"NA","199":"NA","200":"NA","201":"NA","202":"NA","203":"NA","204":"NA","205":"NA","206":"NA","207":"NA","208":"NA","209":"NA","210":"NA","211":"NA","212":"NA","213":"NA","214":"NA","215":"NA","216":"NA","217":"NA","218":"NA","219":"NA","220":"NA","221":"NA","222":"NA","223":"NA","224":"NA","225":"NA","226":"NA","227":"NA","228":"NA","229":"NA","230":"NA","231":"NA","232":"NA","233":"NA","234":"NA","235":"NA","236":"NA","237":"NA","238":"NA","239":"NA","240":"NA","241":"0","242":"NA","243":"NA","244":"NA","245":"NA","246":"NA","247":"NA","248":"NA","249":"NA","250":"NA","251":"NA","252":"NA","253":"NA","254":"NA","255":"NA","256":"NA","257":"NA","258":"NA","259":"NA","260":"NA","261":"NA","262":"NA","263":"NA","264":"NA","265":"NA","266":"NA","267":"NA","268":"NA","269":"NA","270":"NA","271":"NA","272":"NA","273":"0","274":"NA","275":"NA","276":"NA","277":"NA","278":"0","279":"NA","280":"NA","281":"0","282":"0","283":"0","284":"0","285":"NA","286":"NA","287":"2025","288":"NA","289":"NA","290":"46","291":"1","292":"Touchdown","293":"3431","294":"9/7/25, 13:02:43","295":"2025-09-07T19:43:05.560Z","296":"MetLife Stadium","297":"Cloudy with more rain possible Temp: 67° F, Humidity: 79%, Wind: W 3 mph","298":"f591a382-311e-11f0-b670-ae1250fadad1","299":"0","300":"0","301":"PAT2","302":"0","303":"NA","304":"2025-09-07T19:43:09.733Z","305":"NA","306":"16","307":"Touchdown","308":"2025-09-07T19:27:30.667Z","309":"12","310":"7:06","311":"6","312":"1","313":"1","314":"4","315":"4","316":"5","317":"KICKOFF","318":"TOUCHDOWN","319":"14:07","320":"07:01","321":"NYJ 33","322":"PIT 1","323":"3079","324":"3431","325":"34","326":"32","327":"Home","328":"-2","329":"66","330":"-3","331":"37.5","332":"0","333":"outdoors","334":"","335":"NA","336":"NA","337":"Aaron Glenn","338":"Mike Tomlin","339":"NYC01","340":"MetLife Stadium","341":"0","342":"J.Fields","343":"7","344":"NA","345":"NA","346":"G.Wilson","347":"5","348":"1","349":"0","350":"0","351":"0","352":"1","353":"00-0036945","354":"NA","355":"00-0037740","356":"J.Fields","357":"7","358":"00-0036945","359":"G.Wilson","360":"00-0037740","361":"G.Wilson","362":"00-0037740","363":"0","364":"1","365":"-0.947","366":"NA","367":"NA","368":"NA","369":"NA","370":"NA","371":"NA","372":"NA"}],"options":{"columns":{"min":{},"max":[10],"total":[372]},"rows":{"min":[10],"max":[10],"total":[2]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MiwibmNvbCI6Mywic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyIyIMOXIDMiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTFRelVvRE1SQ2U3azlMRjFzRmZRZ3Z1eGM5ZUdzUFJha0hFYWxRUVNoeE42NkwyMlRaWkt0NDhnMThFNTlCRkMrK1JSL0NhOWRKbW9Ca0lNazMzK1NiTDVtcnlmd29ta2NBNEVNUTRCNGloUEI2ZGhxZkFBUWVKaDBJb0svT1p5enY2NXNBZTdnOFUvQXZiczR0dkp6TzhCaXE2bmdLT3NhVER6Q2grZEhQK3V6OTRHVTkrdjU4dXozOC9YSnNRa2FXVkJnTDM1QzlpZ3RKeWRLa082SkpVeXJFb2lhUzJpdGtsUzlvUlp4Mi9aby9KYmJsUVBtLzR0YTI3Y2IxVFVzaXJLOGxvNHhJa3R6WHFNZk1sZlI0SlF2T1VPU3B1WFFkY2FkMmlOMkdxWmRrY2ZyUXNNZjQyQ243RmN1VnA2YTJNVERZKzRmOTdTdTgxc2k3UnQ2bExDK1lIVWRZa2p0YTJzNFpYUms0eEhub2NTUlZYVEJwLzRtc1NDU1h4RXFpbEplVzBUK0h6Uis4YytGQ0xBSUFBQT09In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["success_rate"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["avg_epa"],"name":[3],"type":["dbl"],"align":["right"]}],"data":[{"1":"NYJ","2":"50.0","3":"0.21"},{"1":"PIT","2":"41.5","3":"0.17"}],"options":{"columns":{"min":{},"max":[10],"total":[3]},"rows":{"min":[10],"max":[10],"total":[2]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGxheV9ieV9wbGF5XzIwMjQgJT4lIFxuICBmaWx0ZXIoZ2FtZV9pZCA9PSAnMjAyNV8wMV9QSVRfTllKJyxcbiAgICAgICAgICFpcy5uYShwb3N0ZWFtKSkgJT4lIFxuICAjIHNlbGVjdChzdWNjZXNzLCBldmVyeXRoaW5nKCkpXG4gIGdyb3VwX2J5KHBvc3RlYW0sIGhvbWVfdGVhbSkgJT4lIFxuICBzdW1tYXJpc2Uoc3VjY2Vzc19yYXRlID0gbWVhbihzdWNjZXNzWyFpcy5uYShkb3duKV0sIG5hLnJtID0gVFJVRSksIFxuICAgICAgICAgICAgZXBhX3R1cm5vdmVyID0gc3VtKGVwYVtpbnRlcmNlcHRpb24gPT0gMSB8IGZ1bWJsZV9sb3N0ID09IDFdLCBuYS5ybSA9IFRSVUUpLFxuICAgICAgICAgICAgZXBhXzNyZF80dGggPSBzdW0oZXBhW2Rvd24gPT0gMyB8IGRvd24gPT0gNCAmIHBlbmFsdHkgPT0gMF0sIG5hLnJtID0gVFJVRSksXG4gICAgICAgICAgICBlcGFfc3BlY2lhbF9wZW5hbHRpZXMgPSBzdW0oZXBhW3NwZWNpYWwgPT0gMSB8IHBlbmFsdHkgPT0gMV0sIG5hLnJtID0gVFJVRSkpXG5cbmBgYCJ9 -->

```r
play_by_play_2024 %>% 
  filter(game_id == '2025_01_PIT_NYJ',
         !is.na(posteam)) %>% 
  # select(success, everything())
  group_by(posteam, home_team) %>% 
  summarise(success_rate = mean(success[!is.na(down)], na.rm = TRUE), 
            epa_turnover = sum(epa[interception == 1 | fumble_lost == 1], na.rm = TRUE),
            epa_3rd_4th = sum(epa[down == 3 | down == 4 & penalty == 0], na.rm = TRUE),
            epa_special_penalties = sum(epa[special == 1 | penalty == 1], na.rm = TRUE))

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiYHN1bW1hcmlzZSgpYCBoYXMgZ3JvdXBlZCBvdXRwdXQgYnkgJ3Bvc3RlYW0nLiBZb3UgY2FuIG92ZXJyaWRlIHVzaW5nIHRoZSBgLmdyb3Vwc2AgYXJndW1lbnQuXG4ifQ== -->

```
`summarise()` has grouped output by 'posteam'. You can override using the `.groups` argument.
```



<!-- rnb-output-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbImdyb3VwZWRfZGYiLCJ0YmxfZGYiLCJ0YmwiLCJkYXRhLmZyYW1lIl0sIm5yb3ciOjIsIm5jb2wiOjYsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMiDDlyA2Il0sIkdyb3VwcyI6WyJwb3N0ZWFtIFsyXSJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUEzMlJ2MHZEUUJUSHp6UnBhV3Byb2VnZzR1RGVMSFhRcVIxRVVGQkVLbFFRd3BtY2JXaDZGKzh1dFdNSC93Yi9DVGZSV1RkQi9STWN4TDlBaXBORDQxMlNzeVdEajl6bG04KzdlM2svam5jNkRiTmpBZ0J5UU5mRmJnZ0pqSlAyYm4wTEFGMFRId3RBQjBYNUhnbDNUWWk4V0ZXeHROU1JPenpkVi9Kb3IvMlBWMG9BS3RMYi9QaVNObW0rWHo2dmlVZnhwNVdIeG8vTVoyWXhiNjBmM0UydXg2QlZhZlpmWDJiODhYTzFWTHYxemxvYjN6ZjMzdHNvazdUaCtKQ3hOQ1VGVFJkeWFGMVFPRUNaNDBWS3Jpd3N1THhTbHZISFlvdWlhSnFOcXc1VjQ0WWtzQkFReGhFY3FHQTlNa0QySEZoa29lTWd4bXdLT1ZJTUJkRG1JY1ZraUdqS1NwSTFxR3R2OGw2S2xpVmlBWEk4Nk5zQnd0RG5YdnovYkdJRkVuQ1BZT0hTNW1mMU4wU2FBVXNobHFXNGRhY1g0bjU5TytQT0JiZ3JPeGFqeE1xcDF1WjBQc2xDanpJZHlTUGM5YkNxMWZEaE9mSlZaQmNOVTFrUlhZLzdhUVhVdzF4TlNWQm1jY0todW1JNnhGY2tyaHhNZndFejl3WVR3QUlBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["posteam"],"name":[1],"type":["chr"],"align":["left"]},{"label":["home_team"],"name":[2],"type":["chr"],"align":["left"]},{"label":["success_rate"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["epa_turnover"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["epa_3rd_4th"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["epa_special_penalties"],"name":[6],"type":["dbl"],"align":["right"]}],"data":[{"1":"NYJ","2":"NYJ","3":"0.5294118","4":"-5.676956","5":"7.575878","6":"-0.5656791"},{"1":"PIT","2":"NYJ","3":"0.4444444","4":"0.000000","5":"3.780967","6":"9.4777123"}],"options":{"columns":{"min":{},"max":[10],"total":[6]},"rows":{"min":[10],"max":[10],"total":[2]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



# Exploring summary statistics and totals using PFR stats


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGZyX3N0YXRzX3Bhc3MgPC0gbmZscmVhZHI6OmxvYWRfcGZyX2FkdnN0YXRzKHNlYXNvbnMgPSAyMDI1LFxuICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHN0YXRfdHlwZSA9ICdwYXNzJyxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBzdW1tYXJ5X2xldmVsID0gXCJ3ZWVrXCIpICU+JVxuICBsZWZ0X2pvaW4oeD0uLFxuICAgICAgICAgICAgeT1wbGF5ZXJfaWRzLFxuICAgICAgICAgICAgYnk9J3Bmcl9wbGF5ZXJfaWQnKVxuXG5wZnJfc3RhdHNfcmVjIDwtIG5mbHJlYWRyOjpsb2FkX3Bmcl9hZHZzdGF0cyhzZWFzb25zID0gMjAyNSxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBzdGF0X3R5cGUgPSAncmVjJyxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBzdW1tYXJ5X2xldmVsID0gXCJ3ZWVrXCIpICU+JVxuICBsZWZ0X2pvaW4oeD0uLFxuICAgICAgICAgICAgeT1wbGF5ZXJfaWRzLFxuICAgICAgICAgICAgYnk9J3Bmcl9wbGF5ZXJfaWQnKVxuXG5cbnBmcl9zdGF0c19ydXNoIDwtIG5mbHJlYWRyOjpsb2FkX3Bmcl9hZHZzdGF0cyhzZWFzb25zID0gMjAyNSxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBzdGF0X3R5cGUgPSAncnVzaCcsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgc3VtbWFyeV9sZXZlbCA9IFwid2Vla1wiKSAlPiVcbiAgbGVmdF9qb2luKHg9LixcbiAgICAgICAgICAgIHk9cGxheWVyX2lkcyxcbiAgICAgICAgICAgIGJ5PSdwZnJfcGxheWVyX2lkJylcbmBgYCJ9 -->

```r
pfr_stats_pass <- nflreadr::load_pfr_advstats(seasons = 2025,
                                              stat_type = 'pass',
                                              summary_level = "week") %>%
  left_join(x=.,
            y=player_ids,
            by='pfr_player_id')

pfr_stats_rec <- nflreadr::load_pfr_advstats(seasons = 2025,
                                              stat_type = 'rec',
                                              summary_level = "week") %>%
  left_join(x=.,
            y=player_ids,
            by='pfr_player_id')


pfr_stats_rush <- nflreadr::load_pfr_advstats(seasons = 2025,
                                              stat_type = 'rush',
                                              summary_level = "week") %>%
  left_join(x=.,
            y=player_ids,
            by='pfr_player_id')
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NywibmNvbCI6MTcsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiNyDDlyAxNyJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUErMVZ6V3NUUVJTZnB2bG9WdHNtV3NSRDhlQ2hDSkpsazdScEtrS2lscW90bG1vclZoSFc2V2FhTE5uc0xyT1RwdFdEUFlrWDc5cVRlQkRSaXhjL3dJUDE0RTMvQ0Qwb2VoQVJRVVZwbk1uT2JMdWpGOEdEQndkbTM3emYrL3J0bTluWlUrUHplV1ZlQVFCMGcyaVVQbU4wQ1dLbjV5WXlSUUNpRWFwMGdTaElNcmxNelR2cElrMW5pczRFTi9UbnROeUlybVgxbWVOeit2VFp5WDhJRGhQdHB2QmZXSWFUS3BxVzBiVDhTR0ZZQ3lPanhmeW9oT1J5eFRCU0tCWnlNakkySEVieXhSRTVhaXc3SnJGSWpxc25FREdndGNpQm5pUHFvYVpIVEZ2b2srb1ppREVTK3JiRDZtemRhV0hIUm5VT2JaOVJKekF5RVc0MFNZMWppVWwxdG1FR3FqS2xIb1dtM1VLV1JiVSs1bERlcFgyLzh4cUE4a0NtOWlSdGpwY1QxeS91djByMXhKVWZHMStwQkxmWDl0Q3pWUG80K09uaGhjSEg2OGtIQjg3ZFpLY005SFpld0o5eE92M1R4bzZpcjBlREdxbU9Qd2lrTDJoT3J2ZHdPUkRXUlR5US9HVXAyN2NNdi83Y3VwLzM1S292Q3lBc0QzS3Bobm4rd2wvd2xQbURzSlRybDk2ZHZ6WTcxWGhVZXYrMk1QM3MxZjNTbDNDUFMyL3l5L3NtNzk0clBiLzA0ZGpxME5UVGQwR1AvZnJETDloNFdjNXkva01TLzcwMzJGZ1QvRXFmZlg4UmY3bkRNM0hyVCtYLytOQU5Hck5oQTNuQS8zTFQ0Z3VyVWxBM0swSjFIWThnMk9EcURvd01aQzRockxzV1hLRWljQnlRTFN5NXVLYVFDL215MTNDYU50RUp4RlZFUEZIRWdNU29JYUVxeEdrYXRZclRzZ1hTdndKeHhkUDlFcVpkNVhCcTBjUWUwWm1uM2tuQjhUNWFUM2NwQjc5TU9BbkR0enJ2RHJMcUM5aXBJNXRHR1hVcllOTzNhYTlneHcwM1FxQzZhNGd5dlpzVzAvNE5pQ0dSOWlHSm5aWXE5b0pkUXBGVittaTMyOS9rRFRNczZJa05FNkJTZ1FTcWk1aTFHNEFOS1NUaHVNUjBhQ05CaFAwcjQxSndGNWFBVk5ObVRDb1pvOWEwNjVsc1hySjN1N1Q3dENqd3IwYkFHYk4xWXNzNjdkT0l0SGw0bklmSGtWMDFiWEV1WWhaY1FKYklYRUZMUWN2cGpySitxQzdlN0tGQ1VVOGxEb0VpUkRFY1N5Q2RWd2NiUHdHcFR6UnlRUWdBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["posteam"],"name":[2],"type":["chr"],"align":["left"]},{"label":["receiver_player_id"],"name":[3],"type":["chr"],"align":["left"]},{"label":["receiver_player_name"],"name":[4],"type":["chr"],"align":["left"]},{"label":["epa"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["count_targets"],"name":[6],"type":["int"],"align":["right"]},{"label":["catches"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["touchdowns"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["yards_receiving"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["first_down_catch"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["epa_per_target"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["yards_per_catch"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["receiving_broken_tackles"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["receiving_drop"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["receiving_drop_pct"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["receiving_int"],"name":[16],"type":["dbl"],"align":["right"]},{"label":["receiving_rat"],"name":[17],"type":["dbl"],"align":["right"]}],"data":[{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0035640","4":"D.Metcalf","5":"5.547835","6":"7","7":"4","8":"0","9":"83","10":"4","11":"0.7925479","12":"20.8","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0037837","4":"C.Austin","5":"5.044345","6":"6","7":"4","8":"1","9":"70","10":"3","11":"0.8407241","12":"17.5","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0037228","4":"J.Warren","5":"2.949452","6":"2","7":"2","8":"1","9":"22","10":"2","11":"1.4747259","12":"11.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0036862","4":"B.Skowronek","5":"2.940912","6":"1","7":"1","8":"1","9":"22","10":"1","11":"2.9409122","12":"22.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"2.081349","6":"3","7":"3","8":"0","9":"28","10":"2","11":"0.6937829","12":"9.3","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0033858","4":"J.Smith","5":"1.007067","6":"6","7":"5","8":"1","9":"15","10":"2","11":"0.1678446","12":"3.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0036919","4":"K.Gainwell","5":"-3.213490","6":"4","7":"3","8":"0","9":"4","10":"0","11":"-0.8033726","12":"1.3","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"}],"options":{"columns":{"min":{},"max":[10],"total":[17]},"rows":{"min":[10],"max":[10],"total":[7]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MSwibmNvbCI6MzgsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMSDDlyAzOCJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUE5MVVUNHNUTVJSUC83ZWozZFl1ZS9Dd3NBZnByYVc3MnhWN2tSVkUwSVBJc3NKNkN1bE0yb1pPSjlrazNXNUZzS0FYajM0Q3dRK3dGMEU4N3Bmd2V3amVkMDA2a3lFVFZ4QzhPVENUL0g2L2w1ZVhOeS92NlBISnZuZmlBUUFLb0ZoVTM1S2FndExMNHllZEJ3QVU4d3JrUUJIVTlIaXU1RTAxYWF1M2FRbU52ZDdlQWV6dHdoZFBqK0h6Vjg4Y3VhQm9oL0o2dlU2dnQ3ZmZQeGc0U3UxUjk0Z0dZOHlGQWh0YU9MdzMrWDV4OTl2QTRNdlc5Y1hsMXhWSTlmN0g3Wi92M216L3lmNXdzUFAreTZldER5bCtDTXdUNC9zT2JqcDQ1Ni90NDRPb1ExeXJSNDExalZleFpzOWR1My9GNnpqZS90Q3VLNS8vZjV5cHlsS0VabGdrU1drblpHV3NTRWdDQXhrVkVxTlpBcHNNQ1lFNVpDRmFxaUUxSzhlOEtWdk1rRm1QQ0ljV1hDTGZndVhUb1lXcTUxbTFpcVRFTXlaRmdtLzVkTVpDTEFtTkRPVkpPdmNuQVYya1RJTkVpUm1HT3FpRXJ0OUVsZ1R5cDZsM051SXdlL2l5d0VqUUtFSEZCY1pUYzlmV2huTEpzQkd0SkZVcFl6VENrVFFoYWM5SnhuVEtUVWdXblc1WjErR1JhQXdEVHBtd3MyNUl5SHpqZUlOakg1TXpveVJzSzh0YTlpM2paNGdDS0NlY0xzd09XNzhwMXJMYmtxZzZnVHBaT0kwejVvWWhrYTlkY2pMbm5LUmtMU0ZKbW82WVlCd0xNZWVwM2FaRFd3SGNDZkFJM3JTaEpXUTNiVmdDa2FkRHAvSnI2b0JkVS8yNnZlUlg2aE8zaE93VjhVTmRMazRMRHBCRTNSSFh2eEtBSzJkSmhiSzRRa0ZlZC95eXN6akhIYUk1ajNRa1FjZWZ6S05wWjdmdjZBVVdqZldtSUc1Y0lJazRsN3htM283RHlKc21WelkxaktNeGlVek5sVUkweEtIeEhPQ3p0SkxVRmRMNTZESk8wc0wxZElWMEpaWElMUEY4R2hwbWZYUnc5UXZIKzJ0RUJ3Y0FBQT09In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["posteam"],"name":[2],"type":["chr"],"align":["left"]},{"label":["passer_player_id"],"name":[3],"type":["chr"],"align":["left"]},{"label":["passer"],"name":[4],"type":["chr"],"align":["left"]},{"label":["epa"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["air_epa"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["yac_epa"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["qb_epa"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["xyac_epa"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["attempts"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["completions"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["touchdowns"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["incomplete_pass"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["complete_pass"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["sacks"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["pfr_game_id"],"name":[16],"type":["chr"],"align":["left"]},{"label":["season"],"name":[17],"type":["int"],"align":["right"]},{"label":["week"],"name":[18],"type":["int"],"align":["right"]},{"label":["game_type"],"name":[19],"type":["chr"],"align":["left"]},{"label":["team"],"name":[20],"type":["chr"],"align":["left"]},{"label":["opponent"],"name":[21],"type":["chr"],"align":["left"]},{"label":["pfr_player_name"],"name":[22],"type":["chr"],"align":["left"]},{"label":["pfr_player_id"],"name":[23],"type":["chr"],"align":["left"]},{"label":["passing_drops"],"name":[24],"type":["dbl"],"align":["right"]},{"label":["passing_drop_pct"],"name":[25],"type":["dbl"],"align":["right"]},{"label":["receiving_drop"],"name":[26],"type":["dbl"],"align":["right"]},{"label":["receiving_drop_pct"],"name":[27],"type":["dbl"],"align":["right"]},{"label":["passing_bad_throws"],"name":[28],"type":["dbl"],"align":["right"]},{"label":["passing_bad_throw_pct"],"name":[29],"type":["dbl"],"align":["right"]},{"label":["times_sacked"],"name":[30],"type":["dbl"],"align":["right"]},{"label":["times_blitzed"],"name":[31],"type":["dbl"],"align":["right"]},{"label":["times_hurried"],"name":[32],"type":["dbl"],"align":["right"]},{"label":["times_hit"],"name":[33],"type":["dbl"],"align":["right"]},{"label":["times_pressured"],"name":[34],"type":["dbl"],"align":["right"]},{"label":["times_pressured_pct"],"name":[35],"type":["dbl"],"align":["right"]},{"label":["def_times_blitzed"],"name":[36],"type":["dbl"],"align":["right"]},{"label":["def_times_hurried"],"name":[37],"type":["dbl"],"align":["right"]},{"label":["def_times_hitqb"],"name":[38],"type":["dbl"],"align":["right"]}],"data":[{"1":"2025_01_PIT_NYJ","2":"PIT","3":"00-0023459","4":"A.Rodgers","5":"10.20476","6":"-4.74969","7":"20.56686","8":"10.20476","9":"25.12702","10":"30","11":"22","12":"4","13":"8","14":"22","15":"4","16":"NA","17":"NA","18":"NA","19":"NA","20":"NA","21":"NA","22":"NA","23":"NA","24":"NA","25":"NA","26":"NA","27":"NA","28":"NA","29":"NA","30":"NA","31":"NA","32":"NA","33":"NA","34":"NA","35":"NA","36":"NA","37":"NA","38":"NA"}],"options":{"columns":{"min":{},"max":[10],"total":[38]},"rows":{"min":[10],"max":[10],"total":[1]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->




<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZGljdGlvbmFyeV9wZnJfcGFzc2luZ1xuYGBgIn0= -->

```r
dictionary_pfr_passing
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->

