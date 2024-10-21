
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


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubmZsX2FuYWx5dGljc190aGVtZSA8LSBmdW5jdGlvbiguLi4sIGJhc2Vfc2l6ZSA9IDEyKSB7XG4gIFxuICB0aGVtZShcbiAgICB0ZXh0ID0gZWxlbWVudF90ZXh0KGZhbWlseSA9IFwiTGV4ZW5kXCIsXG4gICAgICAgICAgICAgICAgICAgICAgICBzaXplID0gYmFzZV9zaXplLFxuICAgICAgICAgICAgICAgICAgICAgICAgY29sb3IgPSBcImJsYWNrXCIpLFxuICAgIGF4aXMudGlja3MgPSBlbGVtZW50X2JsYW5rKCksXG4gICAgYXhpcy50aXRsZSA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpLFxuICAgIGF4aXMudGV4dCA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpLFxuICAgIHBsb3QudGl0bGUucG9zaXRpb24gPSBcInBsb3RcIixcbiAgICBwbG90LnRpdGxlID0gZWxlbWVudF9tYXJrZG93bihzaXplID0gMTYsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgdmp1c3QgPSAuMDIsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaGp1c3QgPSAwLjUpLFxuICAgIHBsb3Quc3VidGl0bGUgPSBlbGVtZW50X21hcmtkb3duKGhqdXN0ID0gMC41KSxcbiAgICBwbG90LmNhcHRpb24gPSBlbGVtZW50X21hcmtkb3duKHNpemUgPSA4KSxcbiAgICBwYW5lbC5ncmlkLm1pbm9yID0gZWxlbWVudF9ibGFuaygpLFxuICAgIHBhbmVsLmdyaWQubWFqb3IgPSAgZWxlbWVudF9saW5lKGNvbG9yID0gXCIjZDBkMGQwXCIpLFxuICAgIHBhbmVsLmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoZmlsbCA9IFwiI2Y3ZjdmN1wiKSxcbiAgICBwbG90LmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoZmlsbCA9IFwiI2Y3ZjdmN1wiKSxcbiAgICBwYW5lbC5ib3JkZXIgPSBlbGVtZW50X2JsYW5rKCksXG4gICAgbGVnZW5kLmJhY2tncm91bmQgPSBlbGVtZW50X3JlY3QoY29sb3IgPSBcIiNGN0Y3RjdcIiksXG4gICAgbGVnZW5kLmtleSA9IGVsZW1lbnRfcmVjdChjb2xvciA9IFwiI0Y3RjdGN1wiKSxcbiAgICBsZWdlbmQudGl0bGUgPSBlbGVtZW50X3RleHQoZmFjZSA9IFwiYm9sZFwiKSxcbiAgICBsZWdlbmQudGl0bGUuYWxpZ24gPSAwLjUsXG4gICAgc3RyaXAudGV4dCA9IGVsZW1lbnRfdGV4dChmYWNlID0gXCJib2xkXCIpKVxufVxuYGBgIn0= -->

```r
nfl_analytics_theme <- function(..., base_size = 12) {
  
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
}
```

<!-- rnb-source-end -->

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



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->



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


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGZyX3N0YXRzX3Bhc3MgPC0gbmZscmVhZHI6OmxvYWRfcGZyX2FkdnN0YXRzKHNlYXNvbnMgPSAyMDI0LFxuICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHN0YXRfdHlwZSA9ICdwYXNzJyxcbiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBzdW1tYXJ5X2xldmVsID0gXCJ3ZWVrXCIpXG5cbnBmcl9zdGF0c19yZWMgPC0gbmZscmVhZHI6OmxvYWRfcGZyX2FkdnN0YXRzKHNlYXNvbnMgPSAyMDI0LFxuICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHN0YXRfdHlwZSA9ICdyZWMnLFxuICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHN1bW1hcnlfbGV2ZWwgPSBcIndlZWtcIilcblxuXG5wZnJfc3RhdHNfcnVzaCA8LSBuZmxyZWFkcjo6bG9hZF9wZnJfYWR2c3RhdHMoc2Vhc29ucyA9IDIwMjQsXG4gICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgc3RhdF90eXBlID0gJ3J1c2gnLFxuICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHN1bW1hcnlfbGV2ZWwgPSBcIndlZWtcIilcbmBgYCJ9 -->

```r
pfr_stats_pass <- nflreadr::load_pfr_advstats(seasons = 2024,
                                              stat_type = 'pass',
                                              summary_level = "week")

pfr_stats_rec <- nflreadr::load_pfr_advstats(seasons = 2024,
                                              stat_type = 'rec',
                                              summary_level = "week")


pfr_stats_rush <- nflreadr::load_pfr_advstats(seasons = 2024,
                                              stat_type = 'rush',
                                              summary_level = "week")
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

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NywibmNvbCI6MSwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyI3IMOXIDEiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTJSVFUrRFFCQ0dCOHBIU3FJMjhYZEFXbHF0VnlLYTFCQmlESnA2MmlBZ0VuRWhRSzFILzdhWDRyQmxvN3VIWFhhZmVkOWhadmJCM3k2dHJRVUFFOUEwM0hVOGd2NFkzZHBYQUpxS0Z3VTBtQTdmTHd5Zk13QXd3MldPZ1ROMzdxN0lmRUh1TnhIeG9rREVMc1ArVFNqaUpRbTg2eUVrNGhWVGIwSmZ4QmZFOTRKLzZ0TWp2bVRxNEVrVXIwbjRmTWZFWWdNNmpUK3lkaXllUXpOSFNJcFUwazZiYXU5dy9Ra3U5UnUzdnU5LzVLUkpHYmR5VWl1TnU5aDViZENQdDROa01hdTZLeXFLSm5VWXB5R1psVVlDc3gwZEtrbnQ1RzFIMyszRldvcFBhcG9QUHgyZkJzYUtGZlpFZjJmbFdJYmFqM1pqdEJzWnpRdWE4WDdLK0NVcmVlWTArK1FUeDRHd2VUaDFVOUNPTjRxMGRicXFpN25GU3FxU0U5WTZISDRCeFZaMFpHUUNBQUE9In0= -->

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


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxudG9wX3BsYXlzICU+JSBcbiAgIyBjaG9vc2UgdGhlIGdhbWVcbiAgZmlsdGVyKGdhbWVfaWQgPT0gJzIwMjRfMDdfTllKX1BJVCcpICU+JSBcbiAgc2VsZWN0KC1nYW1lX2lkKSAlPiUgXG4gIGd0KCkgJT4lIFxuICBndF9pbWdfcm93cyhjb2x1bW5zID0gdGVhbV93b3JkbWFyaykgJT4lIFxuICAjcmVuYW1lIGNvbHVtbnNcbiAgY29sc19sYWJlbCh0ZWFtX3dvcmRtYXJrID0gJ1Bvc3Nlc3NpbmcgdGVhbScsXG4gICAgICAgICAgICAgcXRyID0gJ1F0cicsXG4gICAgICAgICAgICAgdGltZSA9ICdUaW1lJyxcbiAgICAgICAgICAgICBkb3duX2Rpc3QgPSAnRG93bi1EaXN0JyxcbiAgICAgICAgICAgICB5cmRsbiA9ICdGaWVsZCBQb3MnLFxuICAgICAgICAgICAgIHBsYXlfdHlwZSA9ICdQbGF5JyxcbiAgICAgICAgICAgICBkZXNjID0gJ0Rlc2NyaXB0aW9uJyxcbiAgICAgICAgICAgICAjIHlkc25ldCA9ICdZYXJkcycsXG4gICAgICAgICAgICAgd3AgPSAnV2luIFByb2InLFxuICAgICAgICAgICAgIHdwX2NoZyA9ICdXaW4gUHJvYiBDaGFuZ2UnKSAlPiUgXG4gICNhZGQgdGFibGUgdGl0bGVcbiAgdGFiX2hlYWRlcih0aXRsZSA9IG1kKFwiKipCaWdnZXN0IFBsYXlzIG9mIHRoZSBHYW1lKipcIiksXG4gICAgICAgICAgICAgc3VidGl0bGUgPSBtZChcIlBsYXlzIHJhbmtlZCBieSBhYnNvbHV0ZSB2YWx1ZSBvZiBFeHBlY3RlZCBQb2ludHMgQWRkZWQ8YnI+RXhjbHVkaW5nIGdhcmJhZ2UgdGltZSB3aGVyZSB3aW4gcHJvYmFiaWx0eSBpcyAuMDUgPCB4IDwgLjk1XCIpKSAlPiUgXG4gIHRhYl9zb3VyY2Vfbm90ZShzb3VyY2Vfbm90ZSA9ICdSZXBsaWNhdGluZyB3b3JrIGRvbmUgYnkgS2V2aW4gQ29sZSBpbiB0aGUgVW5leHBlY3RlZCBQb2ludHMgU3Vic3RhY2sgbmV3c2xldHRlcicpICU+JSBcbiAgZm10X251bWJlcihjb2x1bW5zID0gZXBhLFxuICAgICAgICAgICAgIGRlY2ltYWxzID0gMikgJT4lIFxuICBmbXRfcGVyY2VudChjb2x1bW5zID0gYyh3cCwgd3BfY2hnKSxcbiAgICAgICAgICAgICAgZGVjaW1hbHMgPSAxKSAlPiUgXG4gICNhcHBseSBuZXcgc3R5bGUgdG8gYWxsIGNvbHVtbiBoZWFkZXJzXG4gIHRhYl9zdHlsZShcbiAgICBsb2NhdGlvbnMgPSBjZWxsc19jb2x1bW5fbGFiZWxzKGNvbHVtbnMgPSBldmVyeXRoaW5nKCkpLFxuICAgIHN0eWxlID0gbGlzdChcbiAgICAgICN0aGljayBib3JkZXJcbiAgICAgIGNlbGxfYm9yZGVycyhzaWRlcyA9IFwiYm90dG9tXCIsIHdlaWdodCA9IHB4KDMpKSxcbiAgICAgICNtYWtlIHRleHQgYm9sZFxuICAgICAgY2VsbF90ZXh0KHdlaWdodCA9IFwiYm9sZFwiKVxuICAgIClcbiAgKSAlPiUgXG4gICNhcHBseSBkaWZmZXJlbnQgc3R5bGUgdG8gdGl0bGVcbiAgdGFiX3N0eWxlKGxvY2F0aW9ucyA9IGNlbGxzX3RpdGxlKGdyb3VwcyA9IFwidGl0bGVcIiksXG4gICAgICAgICAgICBzdHlsZSA9IGxpc3QoXG4gICAgICAgICAgICAgIGNlbGxfdGV4dCh3ZWlnaHQgPSBcImJvbGRcIiwgc2l6ZSA9IDI0KVxuICAgICAgICAgICAgKSkgJT4lIFxuICBkYXRhX2NvbG9yKFxuICAgIGNvbHVtbnMgPSBlcGEsXG4gICAgZm4gPSBzY2FsZXM6OmNvbF9udW1lcmljKFxuICAgICAgcGFsZXR0ZSA9IGMoXCJyZWRcIiwgXCJ3aGl0ZVwiLCBcImRhcmtncmVlblwiKSxcbiAgICAgIGRvbWFpbiA9IGMobWluX2VwYSwgbWF4X2VwYSlcbiAgICApKSAlPiUgXG4gIG9wdF9hbGxfY2FwcygpICU+JSBcbiAgb3B0X3RhYmxlX2ZvbnQoXG4gICAgZm9udCA9IGxpc3QoXG4gICAgICBnb29nbGVfZm9udChcIlJvYm90byBDb25kZW5zZWRcIiksXG4gICAgICBkZWZhdWx0X2ZvbnRzKClcbiAgICApXG4gICkgJT4lIFxuICB0YWJfb3B0aW9ucyhcbiAgICAjcmVtb3ZlIGJvcmRlciBiZXR3ZWVuIGNvbHVtbiBoZWFkZXJzIGFuZCB0aXRsZVxuICAgIGNvbHVtbl9sYWJlbHMuYm9yZGVyLnRvcC53aWR0aCA9IHB4KDUpLFxuICAgIGNvbHVtbl9sYWJlbHMuYm9yZGVyLnRvcC5jb2xvciA9IFwidHJhbnNwYXJlbnRcIixcbiAgICAjcmVtb3ZlIGJvcmRlciBhcm91bmQgdGhlIHRhYmxlXG4gICAgdGFibGUuYm9yZGVyLnRvcC5jb2xvciA9IFwidHJhbnNwYXJlbnRcIixcbiAgICB0YWJsZS5ib3JkZXIuYm90dG9tLmNvbG9yID0gXCJ0cmFuc3BhcmVudFwiLFxuICAgICNhZGp1c3QgZm9udCBzaXplcyBhbmQgYWxpZ25tZW50XG4gICAgaGVhZGluZy50aXRsZS5mb250LnNpemUgPSBweCg2MCksXG4gICAgaGVhZGluZy5zdWJ0aXRsZS5mb250LnNpemUgPSBweCgxNiksXG4gICAgdGFibGUuZm9udC5zaXplID0gcHgoMTYpLFxuICAgIHNvdXJjZV9ub3Rlcy5mb250LnNpemUgPSBweCgxMiksXG4gICAgaGVhZGluZy5hbGlnbiA9IFwiY2VudGVyXCJcbiAgKVxuYGBgIn0= -->

```r
top_plays %>% 
  # choose the game
  filter(game_id == '2024_07_NYJ_PIT') %>% 
  select(-game_id) %>% 
  gt() %>% 
  gt_img_rows(columns = team_wordmark) %>% 
  #rename columns
  cols_label(team_wordmark = 'Possessing team',
             qtr = 'Qtr',
             time = 'Time',
             down_dist = 'Down-Dist',
             yrdln = 'Field Pos',
             play_type = 'Play',
             desc = 'Description',
             # ydsnet = 'Yards',
             wp = 'Win Prob',
             wp_chg = 'Win Prob Change') %>% 
  #add table title
  tab_header(title = md("**Biggest Plays of the Game**"),
             subtitle = md("Plays ranked by absolute value of Expected Points Added<br>Excluding garbage time where win probabilty is .05 < x < .95")) %>% 
  tab_source_note(source_note = 'Replicating work done by Kevin Cole in the Unexpected Points Substack newsletter') %>% 
  fmt_number(columns = epa,
             decimals = 2) %>% 
  fmt_percent(columns = c(wp, wp_chg),
              decimals = 1) %>% 
  #apply new style to all column headers
  tab_style(
    locations = cells_column_labels(columns = everything()),
    style = list(
      #thick border
      cell_borders(sides = "bottom", weight = px(3)),
      #make text bold
      cell_text(weight = "bold")
    )
  ) %>% 
  #apply different style to title
  tab_style(locations = cells_title(groups = "title"),
            style = list(
              cell_text(weight = "bold", size = 24)
            )) %>% 
  data_color(
    columns = epa,
    fn = scales::col_numeric(
      palette = c("red", "white", "darkgreen"),
      domain = c(min_epa, max_epa)
    )) %>% 
  opt_all_caps() %>% 
  opt_table_font(
    font = list(
      google_font("Roboto Condensed"),
      default_fonts()
    )
  ) %>% 
  tab_options(
    #remove border between column headers and title
    column_labels.border.top.width = px(5),
    column_labels.border.top.color = "transparent",
    #remove border around the table
    table.border.top.color = "transparent",
    table.border.bottom.color = "transparent",
    #adjust font sizes and alignment
    heading.title.font.size = px(60),
    heading.subtitle.font.size = px(16),
    table.font.size = px(16),
    source_notes.font.size = px(12),
    heading.align = "center"
  )
```

<!-- rnb-source-end -->

```{=html}

<!-- rnb-html-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInNoaW55LnRhZyJdLCJzaXppbmdQb2xpY3kiOltdfX0= -->

<div id="jemzmzbnru" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>@import url("https://fonts.googleapis.com/css2?family=Roboto+Condensed:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#jemzmzbnru table {
  font-family: 'Roboto Condensed', system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#jemzmzbnru thead, #jemzmzbnru tbody, #jemzmzbnru tfoot, #jemzmzbnru tr, #jemzmzbnru td, #jemzmzbnru th {
  border-style: none;
}

#jemzmzbnru p {
  margin: 0;
  padding: 0;
}

#jemzmzbnru .gt_table {
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

#jemzmzbnru .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#jemzmzbnru .gt_title {
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

#jemzmzbnru .gt_subtitle {
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

#jemzmzbnru .gt_heading {
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

#jemzmzbnru .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jemzmzbnru .gt_col_headings {
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

#jemzmzbnru .gt_col_heading {
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

#jemzmzbnru .gt_column_spanner_outer {
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

#jemzmzbnru .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#jemzmzbnru .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#jemzmzbnru .gt_column_spanner {
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

#jemzmzbnru .gt_spanner_row {
  border-bottom-style: hidden;
}

#jemzmzbnru .gt_group_heading {
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

#jemzmzbnru .gt_empty_group_heading {
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

#jemzmzbnru .gt_from_md > :first-child {
  margin-top: 0;
}

#jemzmzbnru .gt_from_md > :last-child {
  margin-bottom: 0;
}

#jemzmzbnru .gt_row {
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

#jemzmzbnru .gt_stub {
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

#jemzmzbnru .gt_stub_row_group {
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

#jemzmzbnru .gt_row_group_first td {
  border-top-width: 2px;
}

#jemzmzbnru .gt_row_group_first th {
  border-top-width: 2px;
}

#jemzmzbnru .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jemzmzbnru .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#jemzmzbnru .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#jemzmzbnru .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jemzmzbnru .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#jemzmzbnru .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#jemzmzbnru .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#jemzmzbnru .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#jemzmzbnru .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#jemzmzbnru .gt_footnotes {
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

#jemzmzbnru .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#jemzmzbnru .gt_sourcenotes {
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

#jemzmzbnru .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#jemzmzbnru .gt_left {
  text-align: left;
}

#jemzmzbnru .gt_center {
  text-align: center;
}

#jemzmzbnru .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#jemzmzbnru .gt_font_normal {
  font-weight: normal;
}

#jemzmzbnru .gt_font_bold {
  font-weight: bold;
}

#jemzmzbnru .gt_font_italic {
  font-style: italic;
}

#jemzmzbnru .gt_super {
  font-size: 65%;
}

#jemzmzbnru .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#jemzmzbnru .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#jemzmzbnru .gt_indent_1 {
  text-indent: 5px;
}

#jemzmzbnru .gt_indent_2 {
  text-indent: 10px;
}

#jemzmzbnru .gt_indent_3 {
  text-indent: 15px;
}

#jemzmzbnru .gt_indent_4 {
  text-indent: 20px;
}

#jemzmzbnru .gt_indent_5 {
  text-indent: 25px;
}

#jemzmzbnru .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#jemzmzbnru div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
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

<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuICAjIGd0c2F2ZSgnLi8vb3V0cHV0L3Rlc3QuaHRtbCcpXG5gYGAifQ== -->

```r
  # gtsave('.//output/test.html')
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MiwibmNvbCI6NSwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyIyIMOXIDUiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFBMTFRVFVzRE1SQk50N3N0WGR0UzBSL2hwUXZpcFJkcGtlTFhRVVFxVkJCSzNLYTF1TTJHVGJhS1h2d0gvUkdLUjY4ZUJjOTY4ZUxaSCtHMTYyUTNBKzBPSkpsNWIxN3lKbWZkL283YmR3a2hSV0xic0R1UUV1ZTh0OTlzRVdKYlVCU0lUU3I2dkFONlE3T3dHckFzUXhSUExvNHhQVDNxd1ZIWGJPZHdsRWFuU3pBeXZQT1M0WHZWVDRndnhMR3AvVDIvM1ByN21DUCsvdWJ1aXFjZnQvMTgvM3Z3dXZtUXMrVndPbVhTV0hJTVdCYWhWSXhPVGJrdVk5OW5VZzRpcXRoQVVDa04wVmdob3BnYnZFcG40d0VUZExsM0RUSGR0dXFoRW9XM0h2cW9hZE9Qc0NWSnNzaWI5UU45WVdZV1FYZElGZlZHRWVpaHlrdktvVkNUa0lQSTBwOWZ5b2tMVVE1b3hGdzdHVGI5NjVqZk5MZGJPYjRvK0ZnL21rSloxRXh1TGVWT1pzTktqTHhrNUNYR3h4UE9jSjZBWHJFQWJ4NnltVW5yOENIcGYzZ2ltbkNGZ3dJcVBSVXFpaExYRHdORTB0SEo0aDlSL3BFa2tnSUFBQT09In0= -->

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


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NTIsIm5jb2wiOjE3LCJzdW1tYXJ5Ijp7IkEgdGliYmxlIjpbIjUyIMOXIDE3Il19fSwicmRmIjoiSDRzSUFBQUFBQUFBQSsxYWZXd1V4eFdmczMzK3dnWTdjU3NLRVRoOHFwRjlPZDhIZDZRa3U4WU80QTljQjl2WWtLQmpjOTZ6VHh4MzE3MDExSzNhT0kyZ1NZV3NpQ29rRUVHb295U3FRa1VMVWdqLzVFeVFhVWdKS1NWT0dxT3FVQ2lVMW9rSlB0SkNtcml6dDIvTzN0bmIyejNiYXZ0SFJqcCsrMzR6ODk1djV1M01QWjFaVjkxbXoyL0xSd2hsb3F3cy9LOFpQeUp6Uy9PcWNqZENXUm5ZTUtFc2xDZmg5M0gzM2ZpaEdIK0s4TWNCSGJOc1ZwdkRZN1Y3Nml1clBJMDF6VXJhNVduWVVLdW1LeVRLVTlsY2I4aEplcjZkbnVyS2VzTk9iSEVsMVE4M0dITGlpSSt1YWFoT1RjK1U2V1Z4dW41OTZvZ3BCMnNFMUZDdE1WcGpvOUlTUXZ0SU9WaGo5OUpMbU1ZN1FvOU9LVVREaHdhdHNYMEdoVXhHbjBZZXArVXdwZmZxMENFbkl6czlJZE95U04zRHJyeXNNc2RIZnYzNDlhUEJSK1U3bEcrMWxsdXRkcGZiN3FJWW0wT1hjZHFXdTVYTU12ZHlod0hHcnVmWjdYVHFlbFpyVnM5eTJXd3FSclV1bFo5a0N2WDlHTktjWkZkcHowbjhPQ3FjZW96TDdyYnBScmRiZFhOUjRYUTcwMTlYa2gwemtCMGpPVFdpV2IySFZxZExIVXMvcCtwWTZuMVd2eTNxN0JqWWpTU2VWZTlHZkJYSzg1cGJaYW5zaW9qK0lOaDVxeTJOZnU4V1BoalJJbktiTEd2OWdRQXZnRjNRYUZrbDhINWUyTm9sZHFiZ2Noc3NhemhCOEdzNkxxaTJ0SEtSVG4rd1F3d0ZVem1pSkNlYmwxdUxPVUhnTlpkRk82SFY2VG93cWxZZG1mS2N6TkdNOVpaYTN1ZmpoVWdxS20rbHBUYlVHWXlrako5ZkZiS3M0YnUzYzBLNzFsTFhXaHFGTHI4b3Bwc0gybytCdkJqSnB3SEYxQmJPcUxJMGNxSTRjVy8wcHFpREpObGdXbG15SVRxYmtDeHQ5QnVoa0krTFMrbDRzcVV2UFY5MTlVdkV6b3NWakJ4QmlKMTl5M2Y4bys4MXNNWEhkaXl5WUx2US8rTG9lWXk1WjN1ZVhvY3h4OVQyNlFjWXM0Ty83bHo5MkVlcytlaTlwbEpzbTUxZnZOZUlNV3ZzaVFBKytHem10cGZtRFV1NGFQT2QzY3NlWVROT3ZUblNqMjMwWE5FUGQwbFkvSlR2SWtMTXY2KytQZHlMOGM3NTU4d0JDWGZsUFlUN21kdFAzait3QXVPdDJHdlh0aDladzhTTy8ra1RYQVF3TjRlV1lOMklHU2s0dUtZSDR5ZWZmdnZSOS92cW1hdFBNdk9zMkw0OFluN2U5TUlLNXZLeHZ6YmllTXlsNXNKWkVnN0czbGtnemZ0Z2Jxd1Q2MlhlN2RveFg3SlBmL05RSmNib2lXMmZ2NDkxUjgrMlBOQWsyZWMySFZwNkVPT0ZQUXN6c2Qvb2xiSzliVGhlOUxxdDdBMFc0OStQaGhhSE1ZN01mNk1XKzQ5K0Z0c3pLczI3dWIrZ2V6UEdVY2ZSdXBJdlk5SFIwejl3M2ZZTVJXTTF2WHV1VmE2SXhqWVd6OGVYWXpSMjlwQk53bHZMNjNyL2hsQS8yaW5tWUx2ZlBCQ28ySW14SkhUZ3hYUFNTbEZoL0JwRlNQcFpRRXBqRHY1a2dKMEp6eEpuQXRzRW5QU2NCZU95Z1pzQm5QVEpuVERlUE9HWjlHZkF4elFoWnNZRTM2VFBSUFdacURHWjRKLzR6QUZiZnYrSzRtdEViQW5nYkVBRVdFVFpTRG1ldVFGMkxtVWpKYSthVC9QM1VQR0trbytqNDZsNERiMmtQekd1SkRsUDY2ZDUwdlQ4YS9sSnpOT0luMWhYYmlKVVBFOWFPb3kycWM2ZmF0T0txNmZuZjZWM0VrMCtUNjM5Y1lOOUZMQ0ZsWkdSQjdGc2o0dzFnSldBOVlEa0hMb0JLNUJ5L2hMQUJ3RlhBdFlCMmdFZlk1WDlWZUMvRnRBQy9BTEFCMUJ5L2p1QUxrQXIxVS8wRXYyRW4wMzFXeWtlS1J0N0g2VWY1dlVYZ1Uyd0RKRGNGMDdLUDZ3M2NaNm9kU0dTSnhLWDhxODZwelJxM0hORzd3bDZ2T2I5cU9HWGprdkgwVHZuOUR5dE50M25raDZ2WlUvZzVYdnZ6Z3Mzc3gvaTlqSC9lR3J2bXdmY1Y1amhuV1VyNTd6Yng1cmsrb2k1OXRQRG42LzArWmdiejd4dWx1cVdmOHIxRWZQeHkzZjFQOUw3SzFJZk1jT3I3M1I4bzZXRjFFZk1xRndmTWRkM2ZQankxdjBubUwvSTlSRXo5UFFjenlyc2J6QncyRDdZMHNJTVEzMTA4aWY3aGwvdnU4NE1RWDMwTWRSSEExQWZYZWo3MFlyd2hQcm9uUSt2SHZSaFArZGpjM2YvTEdCUDFFY25vVDQ2Q2ZYUk9haVBCcWo2Nk1DRDl3VjIxeXhtamtOOTlCdW9qOTZDK3VqWTBtY2RXRi8wZHhyMTBSRFVSMytHK3VnU1ZSOWRodnBvaVB0WDdTOEdGMGF2UUgxMFljR0pIOS9DZm4vL3l2cmVuOXZ0MFVHNVBvcmVrT3VqNkI4dkhYVHZYYlE3ZW1ORDNlRWhuNC9raVhXZGtkcDc3REo3dkxGbHZuaGo3NWVUeVphQ3ZieEh0aXNBbDhBOGNrK1VBcEo3ajh3djNDdTFmV3c1MkRZS0Z3SmF2eVdQSS9mUVFwaFhjVlRXTlE5NDBuOHY2S0w1dWJDT3BaUXUrdDRqK3JYdXZWS0tSOHJHenFIMGE5MTc5MUM0R0RBUDFrZmZlMlJkSllsUThUd1I0NG40dUp3K1l0UG5rZTZuRzcyT3lYNVBhOFZKbDlmVE1WVjk3T1NtcStMcjZVYzZlZEx6TjlWNlNldGUxb3FUYnA3WXFjblRiQWIyZGJyOUdjdlRhZmw4cXZidjdiVi8rT3lYWDF5YnJENW1ZSFBsTTY2NjN5YnNZM1duWGh2WmYwUVZweisxUGszZEZ5ZXJMSFg3ZjgxVEd2Nm1wVTMzdlRmZDdiK1ZKN3JlWTcybkZlZUYzZFFrZnc5dk9pUi96N2J1aXVONFArRXZ4cDJ3bmxQeTl4NEhkUURwSjlqY0xmUHJldVR4alJ0a3U3bGU3dDhvKzJmYnVwVTZOcDZYZFRSRTRqak9GOGpqMXdXVXVnamZDblVIbWI5QlhpejdYVmJHRnRDOStiTGNUL2g2MEUrdzZUWmxuMUhHYXcwbzlWUGoyR2FJMzdSSzNwKzFTMlJzQVgzTnlqd2w1dGUrQ25VYlNaUGlQOFNZZzl4V1BvTGt2elVVQTVuVGdVbVBuL3pnbWhNT1JVU2Uyd3JtWFFMdjVmM2JlTUVURG5EZEdCSURTK2dleVRuNUV5UWY1dUN4MEJ2cUNvb2VrUk02ZUpIOHRwcmo1VVJ2SjAvTWZESFU1ZTFzRDIxUC9QZzZxNXNUMmlNZU9ZUS8yQUYwa2M4dlJFU1BOTklUZHdIOFRCelBFOFlhNURCS0p4SS9jZkRzaEZmUDQwSm9DeC9Fczd4YkFnazFNOGY3MjRWUVdMa1JoUFdFdlNSTTRYaVBQNWlFRkRpUnlrT2VFTnB1SWJtUWZyRE1rRjd2c2JHeE0zVEN2QUV1UWhKR3lQeDJUdVFzUGtIYWJvUytvcWJraE1LaVA0UTNFbVZJLy9VcG01cHNFaWlpcUNzb0tXa3Y5M1oyQmJlVU85eFVmMllZN3o0T2l1U2ZLaEVvbHA0ZEU1NkxaUmtaWXpBOUc2Wm44OEVPZjVDOEYrWUE5emdmSUo3YitXMkpMY2NabGZiREVoYkc5ekFmc3hHTEdCSTVNaVhmR3dvUUpyNTA5TlYvQU1JUXF2QVFKZ0FBIn0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["posteam"],"name":[2],"type":["chr"],"align":["left"]},{"label":["receiver_player_id"],"name":[3],"type":["chr"],"align":["left"]},{"label":["receiver_player_name"],"name":[4],"type":["chr"],"align":["left"]},{"label":["epa"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["count_targets"],"name":[6],"type":["int"],"align":["right"]},{"label":["catches"],"name":[7],"type":["dbl"],"align":["right"]},{"label":["touchdowns"],"name":[8],"type":["dbl"],"align":["right"]},{"label":["yards_receiving"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["first_down_catch"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["epa_per_target"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["yards_per_catch"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["receiving_broken_tackles"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["receiving_drop"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["receiving_drop_pct"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["receiving_int"],"name":[16],"type":["dbl"],"align":["right"]},{"label":["receiving_rat"],"name":[17],"type":["dbl"],"align":["right"]}],"data":[{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0037837","4":"C.Austin","5":"8.3117009","6":"5","7":"4","8":"1","9":"95","10":"2","11":"1.66234019","12":"23.8","13":"0","14":"0","15":"0.000","16":"0","17":"158.3"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"7.7383306","6":"9","7":"5","8":"1","9":"111","10":"4","11":"0.85981451","12":"22.2","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"6.2396497","6":"7","7":"6","8":"0","9":"85","10":"4","11":"0.89137853","12":"14.2","13":"0","14":"0","15":"0.000","16":"0","17":"117.3"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0035298","4":"S.Miller","5":"4.4292188","6":"2","7":"2","8":"0","9":"31","10":"1","11":"2.21460942","12":"15.5","13":"1","14":"0","15":"0.000","16":"0","17":"118.7"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"3.6765670","6":"5","7":"4","8":"0","9":"33","10":"2","11":"0.73531340","12":"8.2","13":"0","14":"1","15":"0.200","16":"0","17":"94.2"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"3.1008311","6":"3","7":"2","8":"0","9":"51","10":"2","11":"1.03361036","12":"25.5","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0036893","4":"N.Harris","5":"2.8756579","6":"2","7":"2","8":"0","9":"35","10":"2","11":"1.43782895","12":"17.5","13":"0","14":"0","15":"0.000","16":"0","17":"118.7"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"2.8040474","6":"7","7":"5","8":"0","9":"57","10":"3","11":"0.40057820","12":"11.4","13":"0","14":"1","15":"0.143","16":"0","17":"95.5"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0038558","4":"D.Washington","5":"2.7124653","6":"1","7":"1","8":"1","9":"5","10":"1","11":"2.71246529","12":"5.0","13":"0","14":"0","15":"0.000","16":"0","17":"127.1"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"2.6513592","6":"3","7":"3","8":"1","9":"24","10":"2","11":"0.88378639","12":"8.0","13":"2","14":"0","15":"0.000","16":"0","17":"136.8"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0037837","4":"C.Austin","5":"2.6247548","6":"1","7":"1","8":"0","9":"17","10":"1","11":"2.62475476","12":"17.0","13":"0","14":"0","15":"0.000","16":"0","17":"118.7"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0038558","4":"D.Washington","5":"2.4329207","6":"2","7":"2","8":"0","9":"31","10":"1","11":"1.21646034","12":"15.5","13":"1","14":"0","15":"0.000","16":"0","17":"118.7"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0037228","4":"J.Warren","5":"2.3927631","6":"3","7":"3","8":"0","9":"11","10":"0","11":"0.79758770","12":"3.7","13":"0","14":"0","15":"0.000","16":"0","17":"81.9"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"2.3470324","6":"4","7":"2","8":"0","9":"29","10":"2","11":"0.58675811","12":"14.5","13":"0","14":"0","15":"0.000","16":"0","17":"74.0"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0037837","4":"C.Austin","5":"2.0727853","6":"5","7":"2","8":"0","9":"36","10":"2","11":"0.41455707","12":"18.0","13":"0","14":"0","15":"0.000","16":"0","17":"65.4"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0036893","4":"N.Harris","5":"2.0085514","6":"6","7":"3","8":"0","9":"54","10":"2","11":"0.33475857","12":"18.0","13":"0","14":"1","15":"0.167","16":"0","17":"81.2"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0037228","4":"J.Warren","5":"1.8063382","6":"2","7":"2","8":"0","9":"19","10":"1","11":"0.90316912","12":"9.5","13":"0","14":"0","15":"0.000","16":"0","17":"106.2"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"1.6766558","6":"11","7":"7","8":"0","9":"113","10":"3","11":"0.15242325","12":"16.1","13":"0","14":"1","15":"0.091","16":"0","17":"97.9"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0038558","4":"D.Washington","5":"1.6591885","6":"4","7":"4","8":"0","9":"36","10":"2","11":"0.41479713","12":"9.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"1.5940397","6":"4","7":"4","8":"0","9":"39","10":"2","11":"0.39850992","12":"9.8","13":"0","14":"0","15":"0.000","16":"0","17":"107.3"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"1.3722304","6":"8","7":"3","8":"0","9":"53","10":"2","11":"0.17152880","12":"17.7","13":"0","14":"1","15":"0.125","16":"0","17":"60.9"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0037228","4":"J.Warren","5":"1.2953777","6":"3","7":"2","8":"0","9":"15","10":"1","11":"0.43179255","12":"7.5","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0038558","4":"D.Washington","5":"1.1782589","6":"1","7":"1","8":"0","9":"9","10":"1","11":"1.17825890","12":"9.0","13":"0","14":"0","15":"0.000","16":"0","17":"104.2"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0036415","4":"V.Jefferson","5":"0.9702913","6":"5","7":"3","8":"0","9":"26","10":"1","11":"0.19405825","12":"8.7","13":"0","14":"0","15":"0.000","16":"0","17":"73.7"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0036415","4":"V.Jefferson","5":"0.9353225","6":"3","7":"2","8":"1","9":"15","10":"2","11":"0.31177415","12":"7.5","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0037382","4":"B.Johnson","5":"0.7032772","6":"1","7":"1","8":"0","9":"9","10":"0","11":"0.70327717","12":"9.0","13":"0","14":"0","15":"0.000","16":"0","17":"104.2"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"0.6229275","6":"4","7":"4","8":"0","9":"27","10":"2","11":"0.15573187","12":"6.8","13":"0","14":"0","15":"0.000","16":"0","17":"94.8"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0037304","4":"Co.Heyward","5":"0.6161982","6":"4","7":"2","8":"1","9":"23","10":"1","11":"0.15404955","12":"11.5","13":"0","14":"2","15":"0.500","16":"0","17":"107.3"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0036893","4":"N.Harris","5":"0.5415101","6":"2","7":"2","8":"0","9":"16","10":"1","11":"0.27075507","12":"8.0","13":"1","14":"0","15":"0.000","16":"0","17":"100.0"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0031585","4":"M.Pruitt","5":"0.3430653","6":"2","7":"1","8":"0","9":"9","10":"0","11":"0.17153265","12":"9.0","13":"0","14":"0","15":"0.000","16":"0","17":"62.5"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0038558","4":"D.Washington","5":"0.3142062","6":"1","7":"1","8":"0","9":"5","10":"0","11":"0.31420622","12":"5.0","13":"0","14":"0","15":"0.000","16":"0","17":"87.5"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"0.2067114","6":"7","7":"5","8":"1","9":"57","10":"2","11":"0.02953020","12":"11.4","13":"1","14":"0","15":"0.000","16":"0","17":"135.1"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0036893","4":"N.Harris","5":"0.1960044","6":"2","7":"1","8":"0","9":"9","10":"0","11":"0.09800221","12":"9.0","13":"0","14":"0","15":"0.000","16":"0","17":"62.5"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0037837","4":"C.Austin","5":"-0.1364430","6":"2","7":"1","8":"0","9":"6","10":"0","11":"-0.06822150","12":"6.0","13":"0","14":"0","15":"0.000","16":"0","17":"56.2"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0038558","4":"D.Washington","5":"-0.2369759","6":"2","7":"1","8":"0","9":"5","10":"0","11":"-0.11848797","12":"5.0","13":"0","14":"0","15":"0.000","16":"0","17":"56.2"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0036894","4":"P.Freiermuth","5":"-0.2713423","6":"3","7":"2","8":"0","9":"16","10":"0","11":"-0.09044744","12":"8.0","13":"0","14":"0","15":"0.000","16":"0","17":"79.9"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0037837","4":"C.Austin","5":"-0.4310386","6":"2","7":"1","8":"0","9":"6","10":"1","11":"-0.21551931","12":"6.0","13":"0","14":"0","15":"0.000","16":"0","17":"56.2"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0037304","4":"Co.Heyward","5":"-0.6304442","6":"1","7":"1","8":"0","9":"2","10":"0","11":"-0.63044421","12":"2.0","13":"0","14":"0","15":"0.000","16":"0","17":"79.2"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0036893","4":"N.Harris","5":"-0.7873748","6":"1","7":"0","8":"0","9":"0","10":"0","11":"-0.78737484","12":"0.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0037228","4":"J.Warren","5":"-0.8344036","6":"2","7":"2","8":"0","9":"13","10":"0","11":"-0.41720179","12":"6.5","13":"2","14":"0","15":"0.000","16":"0","17":"93.7"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0030578","4":"C.Patterson","5":"-0.9726211","6":"2","7":"2","8":"0","9":"19","10":"1","11":"-0.48631055","12":"9.5","13":"0","14":"0","15":"0.000","16":"0","17":"106.2"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0036893","4":"N.Harris","5":"-1.1222143","6":"2","7":"1","8":"0","9":"5","10":"0","11":"-0.56110713","12":"5.0","13":"0","14":"0","15":"0.000","16":"0","17":"56.2"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0037228","4":"J.Warren","5":"-1.1633420","6":"1","7":"1","8":"0","9":"-4","10":"0","11":"-1.16334197","12":"-4.0","13":"0","14":"0","15":"0.000","16":"0","17":"79.2"},{"1":"2024_06_PIT_LV","2":"PIT","3":"00-0037304","4":"Co.Heyward","5":"-1.2003663","6":"2","7":"1","8":"0","9":"4","10":"0","11":"-0.60018315","12":"4.0","13":"0","14":"0","15":"0.000","16":"0","17":"83.3"},{"1":"2024_02_PIT_DEN","2":"PIT","3":"00-0036415","4":"V.Jefferson","5":"-1.2366888","6":"3","7":"2","8":"0","9":"14","10":"0","11":"-0.41222961","12":"7.0","13":"0","14":"0","15":"0.000","16":"0","17":"77.1"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0037837","4":"C.Austin","5":"-1.2679582","6":"2","7":"1","8":"0","9":"7","10":"0","11":"-0.63397912","12":"7.0","13":"0","14":"0","15":"0.000","16":"0","17":"58.3"},{"1":"2024_04_PIT_IND","2":"PIT","3":"00-0036415","4":"V.Jefferson","5":"-1.2719890","6":"3","7":"2","8":"0","9":"21","10":"1","11":"-0.42399633","12":"10.5","13":"0","14":"0","15":"0.000","16":"0","17":"86.8"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0036893","4":"N.Harris","5":"-1.3004572","6":"5","7":"5","8":"0","9":"16","10":"0","11":"-0.26009144","12":"3.2","13":"1","14":"0","15":"0.000","16":"0","17":"80.0"},{"1":"2024_07_NYJ_PIT","2":"PIT","3":"00-0037837","4":"C.Austin","5":"-1.3264881","6":"4","7":"1","8":"0","9":"36","10":"1","11":"-0.33162202","12":"36.0","13":"NA","14":"NA","15":"NA","16":"NA","17":"NA"},{"1":"2024_01_PIT_ATL","2":"PIT","3":"00-0036415","4":"V.Jefferson","5":"-2.0656510","6":"2","7":"1","8":"0","9":"1","10":"0","11":"-1.03282550","12":"1.0","13":"0","14":"0","15":"0.000","16":"0","17":"56.2"},{"1":"2024_05_DAL_PIT","2":"PIT","3":"00-0037247","4":"G.Pickens","5":"-2.7213978","6":"7","7":"3","8":"0","9":"26","10":"1","11":"-0.38877111","12":"8.7","13":"0","14":"0","15":"0.000","16":"0","17":"53.3"},{"1":"2024_03_LAC_PIT","2":"PIT","3":"00-0030578","4":"C.Patterson","5":"-5.1090035","6":"5","7":"3","8":"0","9":"15","10":"1","11":"-1.02180070","12":"5.0","13":"0","14":"0","15":"0.000","16":"1","17":"25.0"}],"options":{"columns":{"min":{},"max":[10],"total":[17]},"rows":{"min":[10],"max":[10],"total":[52]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->






<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxucGZyX3N0YXRzX3Bhc3NcblxuYGBgIn0= -->

```r
pfr_stats_pass

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoi4pSA4pSAIG5mbHZlcnNlIGFkdmFuY2VkIHBhc3Mgd2Vla2x5IHN0YXRzIHZpYSBQRlIg4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSA4pSAXG7ihLkgRGF0YSB1cGRhdGVkOiAyMDI0LTEwLTIxIDAzOjIwOjI5IEVEVFxuIn0= -->

```
── nflverse advanced pass weekly stats via PFR ─────────────────────────────────────────────────────────────────────────
ℹ Data updated: 2024-10-21 03:20:29 EDT
```



<!-- rnb-output-end -->

<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbIm5mbHZlcnNlX2RhdGEiLCJ0YmxfZGYiLCJ0YmwiLCJkYXRhLnRhYmxlIiwiZGF0YS5mcmFtZSJdLCJucm93IjoyMjMsIm5jb2wiOjI1LCJzdW1tYXJ5Ijp7IkEgdGliYmxlIjpbIjIyMyDDlyAyNSJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUErMWREWXhjVjNXZTdEcUo3WGp0U1VnaG9XazFwR21JYUd4bWQ3MS9JUFM4UC81Yjc2Nk5kMGtDcXJwOTNubnJIWFoyWm5remEzdHBCVVdvcWlxRUtrUnBLVDh0aE45UVNrTklRNENTT2lHRWtKQmdKdzZCRkpwRUNGSFVWb1hTbHJZVTZMMHo5OXg3MzNmdW5mZldpUVJWWnFUSm5mdTkrKzQ5OTV6dm5QdnJ6ZEdKbS9xMzNyUTFsOHQxNXpadEV2KzlVUHpNWGZpcXVYMDdoM081VFYwaWMwRnVVMjZMVEUrSng4OFRQNjRVMzd6NFBxa2ViTzhyOXUyZUwvYk9qNDFPelI4YXo0YnVINXMvY3VEZ2VhQTdDRDF5Y0c1K2RHNHFJeng2OU9EODJLdjJaWVRuOXM3TWovTW1rN0NXYjJidi9QakJtYmFvcnVMQTRWZk5INXlaeUFoUGp0NDBQMzF3dEQyc1d4d2ZQVG8vYy9oWlEzVnowd2RuNW1kZXZiODlyT3VZdW1GK2FwVFpPNEhxS2lhRVFtZjNzdjc1WU1HazhhbTk3V0hkNG8yanMvTnpZOW5RcVZIUjVsdzJkT2JWay9Peis4NERWUUwzU2NKeHEyYUV0eE1zRkNvOHF5MnFxeENhbDZadEQrczZaZzVMbFQ0VGRHNk1LMjVqcVBBRjRmWnRVZDBOWVh2cEVlMWhYY2VzMU9aTVJuVHZxSERqdHFodVRwcGF4SWZNOEg1SnhmYXdzZXFvREZSdFVWMkZqSDhUdk1Fa3JPc1FFWW9GWjBDTlFnOGNsSEVxSXl4aU1JL2FDS3NXKzJXd0ZKbzZEM1NIUm9YcVdIRFlLQ3o3d3NLd0Y1WkJleHBEL0RPRGRTZUZqbGg4QmxSWElmMVkyUGU4WUYyMWpMa1lHSDJvR0pEbmtFcytWQTRwVXplY0I2b0ZGc0dQandZYmhVV000ZDdpaGVXY1pRTGpLTUk5Qkl2Z01UVzZZVkQzK3RDNE5XRnhvMW9DT2ZLeitjcXpCTXVoa2MxWVBQRHU1cWpMSmdVSWJ5ZFlqQk9zajREcUttVDBZYU5WUmxoWExZSWptNm41VURtUndjRUdVTjJjMUIyTGRsNVlSbDBXT0RZS1N4OWtBUTloTGJZTUVlaXhnT29xcEdrWit4SHUwZGJhYStZeVRsQzNKcmpMcG9BK1ZBN1RHQWtBMVlMSnFSQ2IzanhMc0p6YnM5blhSbUU1TlRDem1ZM0JxdThEY2tiRWZDVVR1b05RT2VsZ1E4MUdZUm1NMlJwb283Q01tQ3g0K0dGaEd1WkZYbGpPQnRtOEx5T3NGU2lIQzV6aUFXcjZLRWpKSm0zUEROWXRpb2s3bTU1dERKVkxXWFJGUUhzSUZVTTFEazVKMENMSGZqNmNlbUVaL2RtVUl5T3M1UkNqZ3A1OFpnZFZqd2ZsR0dza2M2TTdDSlZobTdGMm83QU1seXlnSUt3RmtRYkJ3Y2FIeXJraGtqTVQya09vaUE5NnZ1Z0V0YmlTbDJ5KzdvV2xON0ZsalJlV1UwNjJKa0ZZOTBRT2d6Z2lBS3Fya01zSk5pbnd3bksyeDZaMXp4STg3dG9rOGNJeXBMRXhIV0hWOTZIV1VIOTRRMmh5aTI2YmZGb2NLUTRVbDhOcUJteXd1THBVUGs5c3VCZzJLcG13WTJ1TG1iQUZSeHRPckl6OThHQ1ZSaVpzcFJ4bXdxcTErTm5GMW85bnd1cWxqRmpFWlhaaEM1VW9FOVlJVnpKaHBZanJsR01qeGZwaTdmeXczajV1ajh6WVFERU9UMlRDRnNJNEUxWUtLK2VQb1Y0MmdCMnZIc3VFdlRZOGxRbGJRWi94WU5XVFVTYXMxaWhud2s2RzlVellRbHpLaEpVaUxyTUxZL0hQZ3kwMXVLNDQ1b2lKVG14RStQUnJ6dy9yNitOK3VTR3NrUWxqTm4rR0dJdDFIbXkxekdYSmlyRTQ1TUVZL3p4WUhKNC94bUxzQmpER1p3L0dZb2tIaXgwNnlJcXhzZHVKOWZPeCt4bGliT3gyWW9OOGJIUmlJdzZaM1JpTDdSdkIwTTg5R0l2UEhvekZGdy9HL1RjN3h1T0xHK04rNU1ZNFQ5MFlHODk5R001cFBCajNRUjkyNHRuRCtvdDhickVCakkzbjJiRGVZckVmdWJzQmJCRGo4NFl3NFBQR01GZDlEZ3c0N3NWZy9ySWhET1lxWGd6bUlNOFlnem5JaGpEd0R5OEdjZHlMd2RqanhXQ3MzUUEyaEhPcDdKaEFtU3hPcko5emJRTVkrTFFYZy9qc3hSaUhOb0lsNTBOZWJOWFJEeGNHY3hvdnhyam13U0NlZWpFWUc3MFl6RldlTVFianZnZmJqZU9iQnh0eTZONlA1WEk5T2JubmtydjRIenZmenJmei9YbDh5UWR6Ri95Q2ZidCtnYjdkLzArK20zNUJ2eGYrQW40ditqbC9MN2ErK1p3NWUrZyt1bmQvNTJmblorZG41MmZuWitkbjUyZm5aK2ZueisxbmNuTFdwZTlQZFp1N1N0M213aytYdnBSa2ZuV2JHNGZkNXZwV3Q3bFIzRzB1ajNhYisxTGQ1bUpRdDduNzE2WHZMSFdicTYvZDVyWmZ0N2xsMlcydTczWHBleS9tVjdlNThHUC9OSmR2dXMwbHgyNXpFYlZMWHlycU5oZkV1aWNzV2ZVL0UrZzIxMzY2OUdYYWJuT1pyOXRjNXV6U04rbTY5TzI3Ym5PengvNXBkZEQ2YVduVEdNYVMxZXFoNllzbG9DMnJVWkVSMEpaMXptRmp5eGhHN2JZdWpESk5EeTFqV3JxMDdHNTEyMUtiWlNMREhLTkIyeGlHYnhaekRadHM0bGpNTTN5MnVXdUVNWEpiUGJENmFnbG8vYlJVWkxVMTdSVEcrZE15akNXaDVWS1daUzNDR3VwWmlqRkt0bHhXMDhWTkhNdEdiaEphZm13eng1RE1wdVlvLzJXb2I5UnVSeHlMNCthblJUZWJlVWF0YnVaWVVsbU5wVVVIcTFwalE2c0h4aUhjZHJVa3RPaGcvYlNzYVpIZkdNNnlwczFTbzNqVFc2ZWZXYnc0NUFocEZvbkhYR2J6Mk1EaXdKeUxZKzVBWWhQSzhqUExISE11ZFZvL0xSVlpMcFZxT3FzL2xtM2NuSEtheVZLbzFYV0xhTlpQUzZYMjBHQXM2dkE2MnhNY0VjNmltYVZDaTl3V2k2eWZWb2czdG5lTmpLWlNTeEJMd1c2WHM3UnFrZENhQnBpZUdQV2xCRG8zM1MwOVdoeXpMR1VGT3VmSWJTbkZZb2pGUWVmQTZHR3hwZmR4SnpVTnNaemFsc0xDRnRpWXkxTDdYYXB3RHdTMk41blFZQkhjbmxzZGNKakZQVVM2QjNuTEE1eWU1K3gwd29sSmY1YUY3RW1La2RXZWNSbXpXSFN3aUdkbUtmYk13QkZkclRnNTZ3cHV6amhuaVdyeDNwSTZwZit1cVdGaXBOYUNXbEhITU1EcXNqWExuYlVFZGVqTXNxL0Z6c1IwYTc5RGtWT3U4ZDBPSzg1NXVqWGRNaFMxdUdRdkNsd01kRTkrYlY5enhsV3JNZC82d0RXUVdEOXRhYlM1TE1ONllxdGpoTGJzWmZ1YjAwY01uU3gzc3VpZVdHc1lQN2VjMnptVmQxRGJHa2FNalN4cmVJSzcweC9zWWM1bzBISk55N2VOTXEzRzdQblVRWWVLTFBJNTU4eVdpaTFoTFhPN3JlVWVLaXllV1NSd3J0eGNZNW1sNGtPT2ViakZVanQ0T1BYcW5udFpKSExQdjlQNDRndzF6aFZPY3NIcDVPNEIxNXJka3RhZWI1bWVwWTRtem9IRnZjeHl4djFFNUxyQjZHREc4ZE95b3JIZGZzZTRZWVVkOXhCay9iU1duQ2J3SDNMTXVrMjB0dXEwbHpCT0RWczl0WlJ0OWNSNGhEMmg0Z3RXaXd6V3FzZW85SWd6a3M2NVpsYWVGYmRSdiszeGhrTHU2WlJicStPdStZSk5MT2RxeVE3TDdCODU3VGdTTnVMeXduSmhPbHlxclVSMDc2NW5LbHdKNDhKa3VMQmNyOUdGcGtzbXcwcFVMUnhZaXh0MURkWGlVbGd0VE5WTzZHdFowMkdsdkZ5NHNWeXBsUFUxdmtQbGVMa3dYbHVybDZ1NmljbTFlcU5jTGV3clI1VVNnVnNuYS9XbHdtaWxZbTVSSFZxdlJIRmhlaTJPdzNXRmJSOFhnaHhyTlJHdTZIZGx2akFWblNoYnRVV0ZNZkZtN1NSMVYvU29kbXk5TUJhWDYvV29RZGZ1TGh1dE5wWnExZlhDMGZMQ1VoaVhyRDZQNzVyY1ZaaHR4TFUxdW91N2ZXNHRMTXlGeDJzbnduS2xScmZxZHN6RjBZbGFYSmdLVDhaUmRZRzBzWFVpaWlQUjlUQ09qUmFYbzhLQk1LcEdHaHFMMXhlaXdxdHJhOVhqQkkxV1MrdUZpYkRTMEtKc213aXJRbGVGeVZwVjIrbVMyWEJGbElxcnRZb1dUK24xUUJRZmkyTGR3LzJpVzFXcFNHR0JwZWhrNFNBUmUrditxRm9yeks2VUcwc0t1V2lzVnBncDA5WFA3Uk5SZlNsY3F4WnVEQnQxVzVqbHdwRTRxaS9VdEJhM2o0bWVpUmJDOVVWcFV5MVB1RjRTdEdsSmIwd1R4bEdwc0wrMlNGZlk4OU5ob3lFbG0yMkVpNHMxZmZWWktLY20rSGxrTFM2Ui9YdEd3N2hXTFJ5dGxZNUhzZWJZM0hwY0t3bkRyRmYwVlRPUHFXYVgxeXVDM1hPQzhhdW1TNXg3VGkvd2E5SmhScmN4WE1xN1pMeFdXeFcxSGwyckwzbTV3N1cyV1FwWDJGYzcxZFlHTHAvMGM5NURaVGNSSEF4MFdNempkNXg3M0ltZHhuYVR5dVVocnZqaG8xcVMrTTRBNVltWFBOSzRBb2N6YkRtaXFqTmN1dFRnVSt0RUxHT01JRUY3MnpuMTFhTEtUSGpNTk9PbmlxZExEazV3ZFZ3eUVRb3JDemVxR0FQT05xSkYwY3VKOHZIaldyV3VDSW9hYzlySzdYdzdXaEZDb09XcU1LVFdrTk54a296ZzVIUTZsamRBN0JndHk4SHk4SXZIYTlWcVZLR0x1STVZengzREU3UzJ6SlZYQ21PMWRmTXYxaHg4NTJIREZZR2MwYzRibGVmV0dtdUYwY1pKcXh2YzdWMUU5bnNRUk45THA4dU5oU1ZSZjJFdVhqdFdyaS9yWU9LT1QxdW13NFVFbGJsVGJpQnNPQlRrNm8yRG5keWFQWk8xcGFwd253UFI4bklVKzZWek9wUFhBbnpxbGMzdmZETVZLYysrU3Jpd1FQOHd3dS8yVG5kelJpaVlTemlkekJrQkhiTStwL0d5RHphZWNPQ21vOStKM2FIVTZUemJtcHlXeG04M3kvRHl2R2V1cVlRRGE5VkdKZExnZEZpWFdsNHIxU3FyL2xHVHUveWxveXUxNnM2am9TRERMcUdhMmtsL3JIRVJmYnZrbFJSeXVpYmNaTDI5UVRrUHQ4MDBkYndtKzkxK1pIZVBLTnlwSExNdDdsTHVkUXozQ1c2VnpGNnlZN1JVcTRibEFsbXhQUW1kTm5VemUvdDBHQytzaVFFeWpNdTFSdGlXZnFLR2xVZ01wamNLZ3hrVkpaM1BNL3EwbmMveWdKNTlOdVVJVUE2cU9XS3ZlMlVvVzA2dURCMGgyamU0WkZtRmNlRWNDbkRUTSt1STVLU2pKNjQ1VnRhdW9aMU45YkxOdEhiTXJrcEJ4WHBER0sraWRaQTVRTHRwNkZtQ0ovd0ZSZ1IzVUhaVDFVa00xMHJaRWIreXJybFkzT3c1RUZXRmh4Y08xR3BtOEhiUjFoRjlYQUhPRVdyY3RuQlFsSFNYM01QWkxNbCtKQ3dXS1MvNU5XWGxwZUVtcmJ6azFHU3QyRTk1YWJYcHNMZVA4bEp6aDhxbXZOVDM1SnJKUytIRis3cThaT1NoZGZOYzFqY2Vtdm9sSVc2MDZwTktFdS8zNnJ5SWtiWjhjcjR4V2pYdlN6S1BUNXJuY2tVL1o4a2ozVzR1Tm5ucDV4T1JrVS9xMEs1ZmpobGpzV2xma2tlMFovUW5yRG9SRmdmTTg3ZzZhK3RUa05YV2g0eWMrNjNuTW9ic2oweGVtT3pVV00zU2ovQ1pDZXU1cEtWb3I5ZlljMzF4ektwUGtrM0lyL3NqMlduM1J3YmVhU3N2QTlhWXBROUp3TkhRMXQ5NlpXN2RyMCs1eHBoZDl0c2IrWVg5Ui8yaXZyQy8wdi9HYTM3N1lYLzMxVTZkbW15akwrUXo4Z241Z3ZaQWU2TStrYTlvYitRNzZoL3RpWHhEZjBMN0lwL1FQekVlb0wraFA2Ry9ZcnpBZUlEOVFYM0kwV2lpalg2eHYzS3pZYnFOLzZOOGFCL3NqeHpvSml6OXl1MkUyVWFiK0FEOVJYMGlmK1hXd1Z5eXZ3bitvWDJRRDhoUDlKL0RZdGdiTGR0OFNjWW41QnY2cTl3UG1MUGVSejZoUDZFL29uOGovK1N5MzQ0WDZCL0lGK1FqeGhPNTdwbTJ5cU4vU3I1TVczeEJQcWY1RS9ZUDVVTStvTDdsdW4zU3NpZTJqL3hFZmVGNG04WmY3TCtjUDludG8zOGdYOUUva1kvSVYrUS84Z1gxbXhZUDJmZ0k5a2Urcy9nQS9KTXJhTkYvYmM4MC9zalZsUmpmclBHbFZFdllBL3lSajZlblRvMnUrUDJOOFZzc2lTZmF4QU8wdDF3R3o3U0pwenplSmZtSTR5dnlrZnR2a2wrb3Z6Uyt5YVh0YUttTnZVSGZ5QmU1Z3AyMi9BL3RMVmV0azIzNGl2RVErWU44VEJzLzBSL1J2aGcvWFBOZnUzNCtmMHZ5UFcwK2l1MWpmOWg4T2lVK292M1JIdGgvMUJlTzMybmpxMXkzeks1bWp5OW9mL1JINUIveUFlTUw4Z1B0aGY2RC9wczJIOFg0SUplQ0I5cndCZjBSL1J2OUQvV0gvTkQ5Rit0bDhYMXlUODc5MlpQM1BQQ1VDNzZ2OHJsa0hqK0UrNTVqT2QzTzVaRGY3SkVIeXFNOFdrNzF2ay8rTkhuUzhQTjlYOHVSVnluMG16NTdjc2x5MkMrc0QvdTNKK2YrMFBzK2U2YmkrV1NLOHFhOTcvdnNnUlJ4bmQvc3huM2wwOXBQbFF2MFRmVXovcWJVaTgreEh6NitNM255N25yVDVHSXA4c0RESzY4ZmJYWS8xKzBDcjlQOGo4bUw5VUU5aUdNN21NL0tYNTJIZnJIbm5uYlQ1R1AxWHc1NVQzbGZPMTc1VXVLRUwyWDFwTWlEOWZ2S3AvRXNMWS92ZS9QbTFlYjRGOXoyZzF0Ky9OM0tXNWc4cDk5OFdmVlAzM3JFSXk0ckY5emNxaWY0WkRPWkNONi9GTjlhdVBjOXJQejdqazAvOG9OYi9qZDR6OGMzOTE3N3ZYVnZ2VGNuNVFwT2YrZTNSLzl3YUVyblA3LzZnY2UzdnVKMTdMMlB2cjN4dDY5OXcvOEVuNzl0NS9ZYk5sMFpDQ0hlL2FGdnp3WHZhNzBmZk9oTkYxM3pyWmYrY3ZDNTBtdXVFaUlFZnhQODdyKzhiYWxPOGdaM3Z2S2ZmdjlYN3p6SzZtMVdkOFhiR1o3U0QxM3VrOWQrNzlTNW4vdzd3Ly95NmpOU01wMy9pN3RPM0gvN3lFM0JQVkpOUC81dWNFL3o4UkI3aitUKzlNUGZlUDRmL0VhWDF2OW5mMnRBUGtFOWFyMG9ld2VmYUJaYll2WGVJU3JiZHZDendYdVYvbFE1clI5Sy8rcWxMeFNpZmpuNGVLdi93V24xL3VjVmZ0ZC8vNzNzbWE1WE5DNlFzOEU3bFA1dmYvM1Qrejl4K2U5b3U2aitlUFYzcXpUMzZnZXBIb08zN0t2em56NTAzMGYrOWIyM0JaK1YxYi8rYWE3dkQzMTc5a2NQZjBQblNmNVAzYkgzL1ErY2ZqTXIvOGN0T2IxeWZlYlA1T2RkckQ3Z1ArRTYvNjZXb1hYK0ZxaUg3SkFpSDVNSC9EbjQyRlhOQ3JRZktQN3I1NFRmSWxtMGJWTGI1VmJscDJUdnU2RS9IMmcwTFJIY21aY0ZQeGJjbzNoMXM0Z0doNTk4dWVZRFBYLzQ4bWJGK3YwdlEzK0puNHIzM3Y1UnU5aFA4Z2VNR3gvNFVkTkJkRjdKaDNZSTNrbHhRL0gzN2xZYzArVStJdGduS0tqemQ1Nzd5US92Mkh1empuKzNKM25DNUNPNTBkK0J2eHBYOFMwNHJleEE3ZDJld2tkcTU0dlNyUTU5S2JoZHZ2YitCNWs4aWw4Ni8wRmw5ejl2QlVBZGh5aWx1QTF4RFB2amxVdkZTVzkvUHl5Q3F4QTl1TDBwL3E5cFhMV1BjdXI4dTF2K3JPTTYrUTNWZDRkS3o2anlSbi9OOGUrTjM1Zm94VGQzMGs3YVNUdHBKKzJrejRVMDF4bi9PbWtuN2FTZHRKTStCOU1jblAvdHVWYWx0Tjk4UlNzTnZxL3llVWh4Zi85cWxSYWczQlZRTDZWWFFacExma2dlbllmelBDWUgxVU55WEFQdjRYNjlUejZGNjM1ZkJlV3hIbCs5dnZNTjdCZnVUeGRBTHM4NUN0TUg2b0h5V0ErOVIzcnl5SzNUQXNpSDVTaFBjb0E5OVh2VS9yV1FoMzdRUjcrSDlzUHpOcC8rTWMybDRGUlBBWjVmbDdGOTFIY095aW05c0g1aFBaZ25PYTZBK3NCUGRYbzE1TkhQOGlBSDJvWDhCdXRGdVpBbnlBZVBIclQ4S0lmSFgzenZNWnhTMU5OMVNaemFZZjEvQ2RSelhYdjVXSC94T2NyaDgwL1VIOFpoZWorZlRIVzlCU2lQY1J2OUgrVFI5YUNjNFArb1AvM2UxVkFlOVVJcDllc0t3REgrK3NZVmtFdTNEMzZGYVp0ejU4VDVYM0MydFI4ZjNLZjJTKzlYKzgxVTMzM040NGZMZ2krcDg1WFQ2anlHOXFVZk8vemt5MHV2K1pYZ3JEci9VL3Zud1puYlIyN0tINXNKenFoeTl6WTNiTCtxNi8vYVl2TVR0STQzTGlQaGdpZTJIWlJIV1RwL09ubE9GSHloOVlJK1h6Z3JkNjFmK2MvQmcrcGM3NkhtTWNKSzhJWFcvaitkMCtoOWNUcGZPMDM5bzM2M3p2ODBUdlUrb3NyZks3c3ovYWplOTBkNTFMa0dPNjlVKytiQmc3RC9UL1dwODBXOVQwMzlvUDFza29mTzBSNVE1eFlmVmYwbnZIVWN1STNPQVlPdktKejYrNlZQTkE5aWdqUC9jYzhmL2VaMS82bWZrMzNWZWFOTzFibU5PUWRTZHFYNjZIMlNtL3IvMXk5dmRrRHpoL1Qra09MSlhlcWNnWENWYXIzUWZ2N2RVcXJxT3pYUHNCeloveTUxVHFuT0hZTUh1MW9Fb25NcGF1ZHo2cnlBeXBIZUhucWI3T0FYZFg5Skh3OHJPYWxmZUE1R3ZLSjZxSjFQd3ZrUjhaM3NTSHhXdkE4KzFkLzhhSDhrdTFPOVgwaWUvK2wyeUw4ZWVFT3pReHJYZHBXMCsrRWR3VmZrOGN1cHg4eDdvTCt6aXAvZklQNnE4eDZxbDg1VnFiLzNxL015OGkvaUZmR0M2dmVkOTl5cnpwdWVVdm1IbThjOGVmMzhETDZoY0tVbmhwTWZmZ1hPaDhtZTVFK2tENUpUbmFzR2p6N2VQT0RUNTlwUHFIN1RPYmc2RnpUeXF6aEdjUURQTTFFT09zOTcvSzFOQndqdVUvWWwvWkZkdnFyOGh2Ukw1N2ZVenIxdy9uVy84bVB5VitJeDFmZDNxajdpRWZVWHovL28zSmZzVEhLUkhlLzMrTi9ETnpRRHAvWlRpa3M2bmlnK1A5bzYrQS91VjN6VC9XbWQ5d1VQTnB2ZFNlZC9tbWRuNWR2amZ4S2NiWnB0SDlQei9aTFc1MzZxNHdYWmk4Ny8wRzdtL2NUNlQ0K1hrRWVjcFhuSXcvak4zcyszTDVlRGNqb1A4emEySGtHNVlONlQybytjV3c1c1Q4c0RjdUg3YWZlWWREMitkV0llMnZHdDV6ejMwTHo2d25rbHBsaXZaMzZGN2VoOElabW5qM2NmSVo5ODdpM3ZrL09xNUh1NmZaanZNcmxoUHVudG4yZTl4K1RNdGYvNDdobWpmTDdVVzIrYXY2WEk2VjIvVUFyemRmcXc5UVhLQTNubVAxbnZ6YWFzOTVrOGdLZmVCNFM4MTkreFhwUUg1VVJlWnJVUDZnL1hpNzUxRzlTVDgrUlQrZUs3VjU5UGx0TjRTcHhoOVVBN3ZuaUo3ZUw3cWVNSzRiQU90ejZ0OFkvZW8vVS82ZnNhYUJmakxPNDM0anI0S3Nqbm9CenV0eFJhcWU3WFN5QlAreGlYUS80YVQwclBxYjNyb2QwODRKNTl1eHprMmY0ZjdoY1Zrbm42NlBxdkE5eTNMNEI2SmYwUFFIMjc0RDFxL3pvb1I4OVJUdFFyMVhlMUo0LzdZcUMzUGYzSjhzeXZxVHk5ZjMyeVBIMzBjK0lsNkZtWDY0VVU2NmQrVXZsQndMRSt3cW1lSXRTSGNZMXcxRGYycCtCNWo5cno4UUQ0ck45SGZ0RDdJeUFIbFFjOXN2a1E4b3I2US9iSGZTcHFsK290UURsNkQrSTN5dStiVitvOHlrdHk0djRrNlFuUEY0YWhQOGhMa2hkNHk4NVBrQ2NZTjNaQnZUNzU2UDBDMUUveVhRL2xLUVY5TXZ0UmZYaStrSWNVN0tmN2cvRVUvWjNxdlI3ZUl4empFY1ozak1kOUlBK01BMHd2dVdRNTNYL1NGNjRQVUg0NDM4alIrSWZ0NTVQdHBhNEw4NUJDZkVoYkwzam5XNzd4d3pmLzlvM1BsSWY5WlYwdjRHbno3ajJZK3VZdEdDZDljUURuUVhsM25vMGZNTCtnajNjZWljL2RZaHU1ZlB2eG52a25mcnc4OGN5THZPdHJ6enhWbDRQeE9GVU96M3BaMTVmU1AvWThuOFM5ZlBid0pHMi9JWFgvQWQ3em52K2x6Szh4bnZyVzM2eDlmQi9rU1Z1LzBzZDdmdVB4VjkrSHhZMjh1NTA5K0I3MjJ5TWY1amVLczdpQXozMzNFQURYNzZPZjR2bGZzbmpxUHBUM25nSGxZZHowclI5OS9OL3d1aHZITzErN21LYXNQM093L21QeHdjTzd0SDBpMy94WTU2Rzl0SEZHNTNIZWs0ZjJjZDJKOHdhUC90bDhNT2VXRCtYUmN1V1RlVjkvY0I3bysxQTd2bnNFM3ZzMzJBNlUxL1huUFNtVTk0MFh2bjBIOU85VVAvZklyY3VuOUJQcnhkVGJycTkrd1BYN0tYR1JyYnVCcDdwY3luN2ZIc0I5OHhmdit5UUg4dGx6andMbHduVnlxai9nZkx2Z2ZzKzdmNDV4d1dOZnBrZlBQUS85SE43ejNkOWk3ZUsrUnNGZHI4NTc3SXoxMHNjN25xTy9RYjk4ODJCOFAvWCtWejVGamx5eUhPVjk4M0w5WHRxNGtQZmtQZnoybmIvazRMbk9lK3JENTQ1UGEveWpkU3F1VHpIdSt1NEw0bnFaOXFIUXI2Zzg3WmZnZmdyS2pmczl0RC9odTBkS2NsRDl0QStFKzBUWWJoRndrak1IS2RxTHl1RTRTeW51SDhOK2tjWUxyWlNOSDFUK3VtUTVMUy91NS9yMnpYRDlqL3NNK0I3dUgrRCtGczRIY2IrRjlqOXczb2J6RXV3WDhocjNYVEErWVh0VXp6WHdIT2UxeUJlVUgvY05zUjhGa05PbnB4eVV3M3J5a0tiTnUzMStqL3VvdUk5M1BaVERjUWYydGRpK0NlenJzbjNESXRTRC9rVjREdDczN1hmbm9SekdQODgrcm5mZmtmaEI3eGRVaXVNZThoSDNVVkVPei8xeTNhN3YvanJvZzUzdm9SMHdEbUJjd2ZpTDkwZDkrMkM0VHNSOVgvUTM4RnZkUHA0bjRYNHM0dGd2ZW81eGlQUXhBSEtpZjFJN1Y4Tnozem1lK2RtNi8vbTR2RFlWMzZydlNlbjdRODFyY2kvUS9EcjNsdkYzdk9taVg5ZjMvL1Q5VG5VdmlPN25mRlBkaTZKL2QwLzNRZWsrMG1PcTNudGFGOFAwdlRyOCt3bm5XdmNpZGY3cnFoMjZGMFgzdU81VDkwZS9wdTQ5MHIzR2J5cDV6OGpyZXUvK3NNYnAvaXJkM3pyWEZQT04rbDRTUGFmN2MzUXZrNTdUdlNUMTkwV0NzODFyaEdQNjc5N1EvU2wxLzFUTC8xUlR6UzhLSG9MN1NIU3ZsUDRPQjkxbk9wUFVRM0JHM1pkNlhOWC9UWFdmais1VGtyM29YaVBaaGZSTDk4L09xZmNlYVA0NWkxZG9lOU45TExJTDRXZGw4NC84bTI2SDlFWjYrSWZtbjlNb0dYbnBQaWpjSHo3WHZINzNZbjBQNytzS3AzdWFxajJ0RjlJLzNZZWovajJxN2tsK1c2VlVqKzVQMDF4cituNHAzV09qL2hCdnpqYk5keUQ0bHVvWDZZbjBUL2ZraUEvMGQzQWVTZjU5RW4zLzdRbDEvNDd1RDhQZjE5SDNrZWtlM21mVTMxdTVXMTViZStIN2d0dVUzdWxlSXQybkk1N0IzeC9TOTBpcFg2VC94OVQ5Ti9MSFIrWDF1WGU4U2V0UDNlZlU5WnhwR3ZTLzlQM3ZNOHEvNkQ3Z09YVWZqM0Q2T3g2a3J5ZVUzcjh1M2Z1K2orcDdqZVNuVkQvMWcvaWcvTkhvUi9XRDdFNzFxM3ZsdXR3RHFoN2lJZFZIZjBlSTdxSHJkaFFQNlY2bjFwTXFkN2U2MzMxRzJZM3NwK0tDYmhmK0xvM21EOW1KN3V0U3ZZK0Fub21IVHlsOXFMOHpwZTFDY2VNUnhRTzZ4MDM2ZkZUeEVmVkIrbm9BN1BDMGtvdnVHV3YvcHZ2ZHFwMm5WRDNrVitvZXJwYUw0amJGcWErMS9OM1lUZlVYN3dXZkJYN1RmV0txbC95Ry9JRHVsMUk5bEQ2dCtFejZJYjE4UjhXbCs1cmlIalB4WGQydkpYOVQ4VURMcSs2bDV6ci8vcjJUZHRKTzJrazc2WE13elhYR3YwN2FTVHRwSisya3o4RTAxeG4vT21rbjdhU2R0Sk0rQjlOYzh2OTd1N1ZZM0Zrczl2Y1BEL1Vua2QxREk0TkpaTEIvZUFTUXZzSGRTV1M0dDI4NGdmU05EQmFoek9ESTdnRm9hM2hnS0lrTTlFRTkvU01qdllqMER2UkJ6YnQzQTlMZjJ6dUNiNkhNQXVuSGZ2Vml6U05EdlVsRWRMUUlmUjhaNFJJbXkvUU5qYUNlQjRaNmk2aU5RZFJ6LzhBQTZnZHRVUndZaERLaUtkVEdRRC9vdWI4NE5NUnNnZldNb0lUOXZjVWtOd1FQc085RHcvMUpQZmYxN3g1SXl0dzMzSXMyNVpvWG5lQVNJc0s0eXZYRGJPSFFLdGRHLytCZ1g1cmRtOXJJNWJiOFRIelNkTW44dzhGSHpqVnVOODRScG04SDl4MGNRUi9pVm5MWW4zT1crYXVERVp5UFBCTHdPTVI5bXZzcmp3MHNWdkU0NU9pcEkxb01ENlRhZ210anBCL0xPS0lPazVuYjFCR1pobEdydlFQRGlEQ0dPaUkzMHp6M2h0N2hJb3RNTERZd20vS296RG5QdlZPNE5OaUxSMHJPM21ac2NIb2VIejlZekhMRlBvd2pEaFlQRHU5Tzh6ekhtT2NZWDFrVTYrZHhuMFVDZ2FTT2VWbjhsZlhkSVRQalVjc21UbjA3cFVpTkNIeitrTWtIVUN0OWc4SUowcU1xTU40VjZSaWJPZU81THpubktzVVVqamhpaldNOFlxemhudU1ZR3ppTCt4MmVuTXErZ1pFUk5pZEVQbkp2NTM0Mk9JSVdaSjdzbWlYMkYwZlNiTUhaSXBvZlNiVXlZeWFQTlk3WkFtTTRuM1Z3cm5JOVoyTHY4QWliWXlCYnVIVTQ2L3I2QmpFS01yYUlqbUk5ekF0WWRIYndrRE04eTV5QVJ3QWU1WG4wY3F3Z0J0ak1qYy9sbURkbG1jTTdSaDNXVThmOEkwUGtkdkNIV1pEcnh4RnQyQndseTd4aHBIOElXczhTNnpoLytBelN3V2MrODJPeGpuT01SMnptcDY2Uk5zTWNuc2NvMGZYVU1aTkZBRWRzNGY3TzlleFlKMHI5NURaMUNlUUM5ZVRDYXJnU3lmOHBYbDU4cjFUZ3hjY0ZPRjh1cWV3bHE0dnhmQks2cUI2RjlWcFY1VGFkaktKbDlYdExzMkJqZlRXaWg0MG9YRkcvTjlkV1YydlZxTnBRK1IyeTV0Vkt1QjdGODFJUUJmZFlzRzZ5WnpXczE4dlY0L09sdUxaYVYyRGVCdWRYRjZqaTdYRzBFSlZQMEJPRlhwWkVyZktYVVQzSHd0SjhZeW11bmFRV2ZvazlzVjdiMWlnTDdjM1h3NFhsU012WndvNVZ5bzNYSTdpMEZzZGxEVzVSWUZtcm93V3N4bEc5dmhicmNzOEQyQkxnMGxLME9POXEwSHFRYkhTSDlhRGNlTjB4a3NXb08wbVFMYUxIdTRna1BlTGI5WHZpUDJKaTlpSW9lT211Y3JVUnhkV3dzcXNlVlJiamFGR0F6MWZmbjZxdlpOa1ZIWlk5OTFpVzVFcFBkYkZ5SW9ycnlvUzU3cnoxOE9xd2RDS3NMa1NsZ2xSS1FWcTlzbDZvTjhKR3ZYQ2lIQmFPN0R1S1FXeWhJa29xZW5VUkk0NVgxc2pVV3hhV3dqaGNFUFJzOFREeDltVkdHQ2x3STF4WlZWVlJpUmYwRmZ0Mjcrd3Q3dXpyTFJUN1g5WlhmRm5mU0dIdnhGeXJvczAvZytKYlMyRWozTFVZUzZyeDVpNnVyVGJLdGFvUXQrdDVrdVB3OGdVeEFQbTFxaVJ0YWVmQzBscDFlZWRBSHp6dlhxMGVsNDAyb2RhblIvMSswdnA5WlV1TUxoTDJJdkt4cUhxOFhDVkZYVmdKajBVVnFya1VuZEJNcjUxc0JvRmRxM0ZaTzlaV3llQmRqVm9qcEZlMkx0UXFoQ2l2L3o4QlJHSjBndWNBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["game_id"],"name":[1],"type":["chr"],"align":["left"]},{"label":["pfr_game_id"],"name":[2],"type":["chr"],"align":["left"]},{"label":["season"],"name":[3],"type":["int"],"align":["right"]},{"label":["week"],"name":[4],"type":["int"],"align":["right"]},{"label":["game_type"],"name":[5],"type":["chr"],"align":["left"]},{"label":["team"],"name":[6],"type":["chr"],"align":["left"]},{"label":["opponent"],"name":[7],"type":["chr"],"align":["left"]},{"label":["pfr_player_name"],"name":[8],"type":["chr"],"align":["left"]},{"label":["pfr_player_id"],"name":[9],"type":["chr"],"align":["left"]},{"label":["passing_drops"],"name":[10],"type":["dbl"],"align":["right"]},{"label":["passing_drop_pct"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["receiving_drop"],"name":[12],"type":["dbl"],"align":["right"]},{"label":["receiving_drop_pct"],"name":[13],"type":["dbl"],"align":["right"]},{"label":["passing_bad_throws"],"name":[14],"type":["dbl"],"align":["right"]},{"label":["passing_bad_throw_pct"],"name":[15],"type":["dbl"],"align":["right"]},{"label":["times_sacked"],"name":[16],"type":["dbl"],"align":["right"]},{"label":["times_blitzed"],"name":[17],"type":["dbl"],"align":["right"]},{"label":["times_hurried"],"name":[18],"type":["dbl"],"align":["right"]},{"label":["times_hit"],"name":[19],"type":["dbl"],"align":["right"]},{"label":["times_pressured"],"name":[20],"type":["dbl"],"align":["right"]},{"label":["times_pressured_pct"],"name":[21],"type":["dbl"],"align":["right"]},{"label":["def_times_blitzed"],"name":[22],"type":["dbl"],"align":["right"]},{"label":["def_times_hurried"],"name":[23],"type":["dbl"],"align":["right"]},{"label":["def_times_hitqb"],"name":[24],"type":["dbl"],"align":["right"]},{"label":["player_id"],"name":[25],"type":["chr"],"align":["left"]}],"data":[{"1":"2024_01_BAL_KC","2":"202409050kan","3":"2024","4":"1","5":"REG","6":"KC","7":"BAL","8":"Patrick Mahomes","9":"MahoPa00","10":"2","11":"0.074","12":"NA","13":"NA","14":"2","15":"0.074","16":"2","17":"4","18":"5","19":"4","20":"11","21":"0.367","22":"NA","23":"NA","24":"NA","25":"00-0033873"},{"1":"2024_01_BAL_KC","2":"202409050kan","3":"2024","4":"1","5":"REG","6":"BAL","7":"KC","8":"Lamar Jackson","9":"JackLa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"11","15":"0.275","16":"1","17":"13","18":"10","19":"1","20":"12","21":"0.235","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_01_GB_PHI","2":"202409060phi","3":"2024","4":"1","5":"REG","6":"PHI","7":"GB","8":"Jalen Hurts","9":"HurtJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.172","16":"2","17":"7","18":"4","19":"3","20":"9","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0036389"},{"1":"2024_01_GB_PHI","2":"202409060phi","3":"2024","4":"1","5":"REG","6":"GB","7":"PHI","8":"Jordan Love","9":"LoveJo03","10":"4","11":"0.129","12":"NA","13":"NA","14":"6","15":"0.194","16":"1","17":"10","18":"2","19":"3","20":"6","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0036264"},{"1":"2024_01_GB_PHI","2":"202409060phi","3":"2024","4":"1","5":"REG","6":"GB","7":"PHI","8":"Malik Willis","9":"WillMa12","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"1.000","16":"1","17":"0","18":"1","19":"0","20":"2","21":"1.000","22":"NA","23":"NA","24":"NA","25":"00-0038128"},{"1":"2024_01_PIT_ATL","2":"202409080atl","3":"2024","4":"1","5":"REG","6":"ATL","7":"PIT","8":"Kirk Cousins","9":"CousKi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.174","16":"2","17":"3","18":"2","19":"5","20":"9","21":"0.321","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_01_PIT_ATL","2":"202409080atl","3":"2024","4":"1","5":"REG","6":"PIT","7":"ATL","8":"Justin Fields","9":"FielJu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.182","16":"2","17":"4","18":"1","19":"1","20":"4","21":"0.138","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_01_ARI_BUF","2":"202409080buf","3":"2024","4":"1","5":"REG","6":"BUF","7":"ARI","8":"Josh Allen","9":"AlleJo02","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.130","16":"2","17":"7","18":"1","19":"1","20":"4","21":"0.138","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_01_ARI_BUF","2":"202409080buf","3":"2024","4":"1","5":"REG","6":"ARI","7":"BUF","8":"Kyler Murray","9":"MurrKy00","10":"4","11":"0.129","12":"NA","13":"NA","14":"3","15":"0.097","16":"4","17":"9","18":"4","19":"2","20":"10","21":"0.263","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_01_TEN_CHI","2":"202409080chi","3":"2024","4":"1","5":"REG","6":"CHI","7":"TEN","8":"Caleb Williams","9":"WillCa03","10":"1","11":"0.037","12":"NA","13":"NA","14":"9","15":"0.333","16":"2","17":"9","18":"4","19":"3","20":"9","21":"0.273","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_01_TEN_CHI","2":"202409080chi","3":"2024","4":"1","5":"REG","6":"TEN","7":"CHI","8":"Will Levis","9":"LeviWi00","10":"2","11":"0.069","12":"NA","13":"NA","14":"8","15":"0.276","16":"3","17":"5","18":"7","19":"7","20":"17","21":"0.447","22":"NA","23":"NA","24":"NA","25":"00-0039152"},{"1":"2024_01_NE_CIN","2":"202409080cin","3":"2024","4":"1","5":"REG","6":"CIN","7":"NE","8":"Joe Burrow","9":"BurrJo01","10":"1","11":"0.034","12":"NA","13":"NA","14":"4","15":"0.138","16":"3","17":"7","18":"0","19":"0","20":"3","21":"0.086","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_01_NE_CIN","2":"202409080cin","3":"2024","4":"1","5":"REG","6":"NE","7":"CIN","8":"Jacoby Brissett","9":"BrisJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.261","16":"1","17":"5","18":"1","19":"6","20":"8","21":"0.276","22":"NA","23":"NA","24":"NA","25":"00-0033119"},{"1":"2024_01_HOU_IND","2":"202409080clt","3":"2024","4":"1","5":"REG","6":"IND","7":"HOU","8":"Anthony Richardson","9":"RichAn03","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.263","16":"2","17":"2","18":"2","19":"0","20":"4","21":"0.167","22":"NA","23":"NA","24":"NA","25":"00-0039164"},{"1":"2024_01_HOU_IND","2":"202409080clt","3":"2024","4":"1","5":"REG","6":"HOU","7":"IND","8":"C.J. Stroud","9":"StroCJ00","10":"1","11":"0.032","12":"NA","13":"NA","14":"5","15":"0.161","16":"4","17":"9","18":"5","19":"4","20":"13","21":"0.342","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_01_JAX_MIA","2":"202409080mia","3":"2024","4":"1","5":"REG","6":"MIA","7":"JAX","8":"Tua Tagovailoa","9":"TagoTu00","10":"1","11":"0.028","12":"NA","13":"NA","14":"7","15":"0.194","16":"3","17":"11","18":"2","19":"1","20":"6","21":"0.146","22":"NA","23":"NA","24":"NA","25":"00-0036212"},{"1":"2024_01_JAX_MIA","2":"202409080mia","3":"2024","4":"1","5":"REG","6":"JAX","7":"MIA","8":"Trevor Lawrence","9":"LawrTr00","10":"0","11":"0.000","12":"NA","13":"NA","14":"7","15":"0.350","16":"3","17":"10","18":"1","19":"1","20":"5","21":"0.200","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_01_CAR_NO","2":"202409080nor","3":"2024","4":"1","5":"REG","6":"NO","7":"CAR","8":"Derek Carr","9":"CarrDe02","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.087","16":"1","17":"8","18":"1","19":"0","20":"2","21":"0.080","22":"NA","23":"NA","24":"NA","25":"00-0031280"},{"1":"2024_01_CAR_NO","2":"202409080nor","3":"2024","4":"1","5":"REG","6":"NO","7":"CAR","8":"Jake Haener","9":"HaenJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0038998"},{"1":"2024_01_CAR_NO","2":"202409080nor","3":"2024","4":"1","5":"REG","6":"CAR","7":"NO","8":"Bryce Young","9":"YounBr01","10":"1","11":"0.037","12":"NA","13":"NA","14":"11","15":"0.407","16":"4","17":"13","18":"6","19":"2","20":"12","21":"0.316","22":"NA","23":"NA","24":"NA","25":"00-0039150"},{"1":"2024_01_CAR_NO","2":"202409080nor","3":"2024","4":"1","5":"REG","6":"CAR","7":"NO","8":"Andy Dalton","9":"DaltAn00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0027973"},{"1":"2024_01_MIN_NYG","2":"202409080nyg","3":"2024","4":"1","5":"REG","6":"NYG","7":"MIN","8":"Daniel Jones","9":"JoneDa05","10":"5","11":"0.132","12":"NA","13":"NA","14":"5","15":"0.132","16":"5","17":"12","18":"7","19":"7","20":"19","21":"0.388","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_01_MIN_NYG","2":"202409080nyg","3":"2024","4":"1","5":"REG","6":"MIN","7":"NYG","8":"Sam Darnold","9":"DarnSa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.083","16":"1","17":"5","18":"3","19":"1","20":"5","21":"0.192","22":"NA","23":"NA","24":"NA","25":"00-0034869"},{"1":"2024_01_LV_LAC","2":"202409080sdg","3":"2024","4":"1","5":"REG","6":"LAC","7":"LV","8":"Justin Herbert","9":"HerbJu00","10":"3","11":"0.115","12":"NA","13":"NA","14":"4","15":"0.154","16":"1","17":"12","18":"0","19":"4","20":"5","21":"0.179","22":"NA","23":"NA","24":"NA","25":"00-0036355"},{"1":"2024_01_LV_LAC","2":"202409080sdg","3":"2024","4":"1","5":"REG","6":"LV","7":"LAC","8":"Gardner Minshew II","9":"MinsGa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.094","16":"4","17":"10","18":"1","19":"2","20":"7","21":"0.175","22":"NA","23":"NA","24":"NA","25":"00-0035289"},{"1":"2024_01_DEN_SEA","2":"202409080sea","3":"2024","4":"1","5":"REG","6":"SEA","7":"DEN","8":"Geno Smith","9":"SmitGe00","10":"0","11":"0.000","12":"NA","13":"NA","14":"7","15":"0.280","16":"2","17":"10","18":"3","19":"5","20":"10","21":"0.357","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_01_DEN_SEA","2":"202409080sea","3":"2024","4":"1","5":"REG","6":"DEN","7":"SEA","8":"Bo Nix","9":"NixxBo00","10":"2","11":"0.048","12":"NA","13":"NA","14":"9","15":"0.214","16":"2","17":"10","18":"4","19":"7","20":"13","21":"0.265","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_01_DAL_CLE","2":"202409080cle","3":"2024","4":"1","5":"REG","6":"CLE","7":"DAL","8":"Deshaun Watson","9":"WatsDe00","10":"5","11":"0.116","12":"NA","13":"NA","14":"10","15":"0.233","16":"6","17":"12","18":"7","19":"12","20":"25","21":"0.446","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_01_DAL_CLE","2":"202409080cle","3":"2024","4":"1","5":"REG","6":"DAL","7":"CLE","8":"Dak Prescott","9":"PresDa01","10":"2","11":"0.063","12":"NA","13":"NA","14":"5","15":"0.156","16":"3","17":"9","18":"4","19":"2","20":"9","21":"0.257","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_01_WAS_TB","2":"202409080tam","3":"2024","4":"1","5":"REG","6":"TB","7":"WAS","8":"Baker Mayfield","9":"MayfBa00","10":"1","11":"0.033","12":"NA","13":"NA","14":"3","15":"0.100","16":"1","17":"14","18":"5","19":"3","20":"9","21":"0.265","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_01_WAS_TB","2":"202409080tam","3":"2024","4":"1","5":"REG","6":"WAS","7":"TB","8":"Jayden Daniels","9":"DaniJa02","10":"1","11":"0.042","12":"NA","13":"NA","14":"4","15":"0.167","16":"2","17":"11","18":"3","19":"1","20":"6","21":"0.182","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_01_LA_DET","2":"202409080det","3":"2024","4":"1","5":"REG","6":"DET","7":"LA","8":"Jared Goff","9":"GoffJa00","10":"3","11":"0.107","12":"NA","13":"NA","14":"4","15":"0.143","16":"2","17":"4","18":"0","19":"3","20":"5","21":"0.161","22":"NA","23":"NA","24":"NA","25":"00-0033106"},{"1":"2024_01_LA_DET","2":"202409080det","3":"2024","4":"1","5":"REG","6":"LA","7":"DET","8":"Matthew Stafford","9":"StafMa00","10":"4","11":"0.083","12":"NA","13":"NA","14":"6","15":"0.125","16":"2","17":"14","18":"5","19":"9","20":"16","21":"0.314","22":"NA","23":"NA","24":"NA","25":"00-0026498"},{"1":"2024_01_NYJ_SF","2":"202409090sfo","3":"2024","4":"1","5":"REG","6":"SF","7":"NYJ","8":"Brock Purdy","9":"PurdBr00","10":"1","11":"0.034","12":"NA","13":"NA","14":"5","15":"0.172","16":"2","17":"7","18":"3","19":"1","20":"6","21":"0.188","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_01_NYJ_SF","2":"202409090sfo","3":"2024","4":"1","5":"REG","6":"NYJ","7":"SF","8":"Aaron Rodgers","9":"RodgAa00","10":"2","11":"0.095","12":"NA","13":"NA","14":"4","15":"0.190","16":"1","17":"2","18":"1","19":"2","20":"4","21":"0.182","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_01_NYJ_SF","2":"202409090sfo","3":"2024","4":"1","5":"REG","6":"NYJ","7":"SF","8":"Tyrod Taylor","9":"TaylTy00","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.125","16":"0","17":"1","18":"1","19":"1","20":"2","21":"0.222","22":"NA","23":"NA","24":"NA","25":"00-0028118"},{"1":"2024_02_BUF_MIA","2":"202409120mia","3":"2024","4":"2","5":"REG","6":"MIA","7":"BUF","8":"Tua Tagovailoa","9":"TagoTu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"7","15":"0.280","16":"1","17":"0","18":"0","19":"1","20":"2","21":"0.071","22":"NA","23":"NA","24":"NA","25":"00-0036212"},{"1":"2024_02_BUF_MIA","2":"202409120mia","3":"2024","4":"2","5":"REG","6":"MIA","7":"BUF","8":"Skylar Thompson","9":"ThomSk00","10":"1","11":"0.071","12":"NA","13":"NA","14":"4","15":"0.286","16":"1","17":"1","18":"0","19":"2","20":"3","21":"0.188","22":"NA","23":"NA","24":"NA","25":"00-0037327"},{"1":"2024_02_BUF_MIA","2":"202409120mia","3":"2024","4":"2","5":"REG","6":"BUF","7":"MIA","8":"Josh Allen","9":"AlleJo02","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.158","16":"0","17":"4","18":"2","19":"0","20":"2","21":"0.100","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_02_LV_BAL","2":"202409150rav","3":"2024","4":"2","5":"REG","6":"BAL","7":"LV","8":"Lamar Jackson","9":"JackLa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.129","16":"2","17":"5","18":"2","19":"0","20":"4","21":"0.105","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_02_LV_BAL","2":"202409150rav","3":"2024","4":"2","5":"REG","6":"LV","7":"BAL","8":"Gardner Minshew II","9":"MinsGa00","10":"1","11":"0.028","12":"NA","13":"NA","14":"3","15":"0.083","16":"5","17":"10","18":"3","19":"4","20":"12","21":"0.279","22":"NA","23":"NA","24":"NA","25":"00-0035289"},{"1":"2024_02_LAC_CAR","2":"202409150car","3":"2024","4":"2","5":"REG","6":"CAR","7":"LAC","8":"Bryce Young","9":"YounBr01","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.154","16":"2","17":"6","18":"0","19":"0","20":"2","21":"0.069","22":"NA","23":"NA","24":"NA","25":"00-0039150"},{"1":"2024_02_LAC_CAR","2":"202409150car","3":"2024","4":"2","5":"REG","6":"LAC","7":"CAR","8":"Justin Herbert","9":"HerbJu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.200","16":"1","17":"8","18":"0","19":"1","20":"2","21":"0.091","22":"NA","23":"NA","24":"NA","25":"00-0036355"},{"1":"2024_02_NO_DAL","2":"202409150dal","3":"2024","4":"2","5":"REG","6":"DAL","7":"NO","8":"Dak Prescott","9":"PresDa01","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.132","16":"3","17":"6","18":"7","19":"0","20":"10","21":"0.233","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_02_NO_DAL","2":"202409150dal","3":"2024","4":"2","5":"REG","6":"DAL","7":"NO","8":"Cooper Rush","9":"RushCo00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0033662"},{"1":"2024_02_NO_DAL","2":"202409150dal","3":"2024","4":"2","5":"REG","6":"NO","7":"DAL","8":"Derek Carr","9":"CarrDe02","10":"1","11":"0.067","12":"NA","13":"NA","14":"1","15":"0.067","16":"1","17":"7","18":"7","19":"1","20":"9","21":"0.529","22":"NA","23":"NA","24":"NA","25":"00-0031280"},{"1":"2024_02_TB_DET","2":"202409150det","3":"2024","4":"2","5":"REG","6":"DET","7":"TB","8":"Jared Goff","9":"GoffJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"11","15":"0.212","16":"0","17":"12","18":"3","19":"10","20":"13","21":"0.228","22":"NA","23":"NA","24":"NA","25":"00-0033106"},{"1":"2024_02_TB_DET","2":"202409150det","3":"2024","4":"2","5":"REG","6":"DET","7":"TB","8":"Jack Fox","9":"FoxxJa01","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"NA"},{"1":"2024_02_TB_DET","2":"202409150det","3":"2024","4":"2","5":"REG","6":"TB","7":"DET","8":"Baker Mayfield","9":"MayfBa00","10":"1","11":"0.053","12":"NA","13":"NA","14":"3","15":"0.158","16":"5","17":"11","18":"3","19":"0","20":"8","21":"0.286","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_02_IND_GB","2":"202409150gnb","3":"2024","4":"2","5":"REG","6":"GB","7":"IND","8":"Malik Willis","9":"WillMa12","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.071","16":"0","17":"6","18":"1","19":"0","20":"1","21":"0.063","22":"NA","23":"NA","24":"NA","25":"00-0038128"},{"1":"2024_02_IND_GB","2":"202409150gnb","3":"2024","4":"2","5":"REG","6":"IND","7":"GB","8":"Anthony Richardson","9":"RichAn03","10":"1","11":"0.031","12":"NA","13":"NA","14":"8","15":"0.250","16":"1","17":"4","18":"4","19":"2","20":"7","21":"0.189","22":"NA","23":"NA","24":"NA","25":"00-0039164"},{"1":"2024_02_CLE_JAX","2":"202409150jax","3":"2024","4":"2","5":"REG","6":"JAX","7":"CLE","8":"Trevor Lawrence","9":"LawrTr00","10":"4","11":"0.143","12":"NA","13":"NA","14":"6","15":"0.214","16":"4","17":"9","18":"1","19":"4","20":"9","21":"0.250","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_02_CLE_JAX","2":"202409150jax","3":"2024","4":"2","5":"REG","6":"CLE","7":"JAX","8":"Deshaun Watson","9":"WatsDe00","10":"5","11":"0.147","12":"NA","13":"NA","14":"3","15":"0.088","16":"2","17":"9","18":"4","19":"6","20":"12","21":"0.316","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_02_SF_MIN","2":"202409150min","3":"2024","4":"2","5":"REG","6":"MIN","7":"SF","8":"Sam Darnold","9":"DarnSa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.125","16":"3","17":"3","18":"3","19":"2","20":"8","21":"0.258","22":"NA","23":"NA","24":"NA","25":"00-0034869"},{"1":"2024_02_SF_MIN","2":"202409150min","3":"2024","4":"2","5":"REG","6":"SF","7":"MIN","8":"Brock Purdy","9":"PurdBr00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.111","16":"6","17":"21","18":"7","19":"3","20":"16","21":"0.364","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_02_SEA_NE","2":"202409150nwe","3":"2024","4":"2","5":"REG","6":"NE","7":"SEA","8":"Jacoby Brissett","9":"BrisJa00","10":"2","11":"0.083","12":"NA","13":"NA","14":"5","15":"0.208","16":"3","17":"7","18":"7","19":"4","20":"14","21":"0.438","22":"NA","23":"NA","24":"NA","25":"00-0033119"},{"1":"2024_02_SEA_NE","2":"202409150nwe","3":"2024","4":"2","5":"REG","6":"SEA","7":"NE","8":"Geno Smith","9":"SmitGe00","10":"4","11":"0.093","12":"NA","13":"NA","14":"2","15":"0.047","16":"3","17":"15","18":"5","19":"3","20":"11","21":"0.229","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_02_NYJ_TEN","2":"202409150oti","3":"2024","4":"2","5":"REG","6":"TEN","7":"NYJ","8":"Will Levis","9":"LeviWi00","10":"1","11":"0.037","12":"NA","13":"NA","14":"3","15":"0.111","16":"4","17":"4","18":"0","19":"2","20":"6","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0039152"},{"1":"2024_02_NYJ_TEN","2":"202409150oti","3":"2024","4":"2","5":"REG","6":"NYJ","7":"TEN","8":"Aaron Rodgers","9":"RodgAa00","10":"3","11":"0.103","12":"NA","13":"NA","14":"7","15":"0.241","16":"2","17":"8","18":"1","19":"1","20":"4","21":"0.121","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_02_NYG_WAS","2":"202409150was","3":"2024","4":"2","5":"REG","6":"WAS","7":"NYG","8":"Jayden Daniels","9":"DaniJa02","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.103","16":"5","17":"12","18":"3","19":"2","20":"10","21":"0.263","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_02_NYG_WAS","2":"202409150was","3":"2024","4":"2","5":"REG","6":"NYG","7":"WAS","8":"Daniel Jones","9":"JoneDa05","10":"1","11":"0.037","12":"NA","13":"NA","14":"6","15":"0.222","16":"1","17":"7","18":"2","19":"3","20":"6","21":"0.200","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_02_LA_ARI","2":"202409150crd","3":"2024","4":"2","5":"REG","6":"ARI","7":"LA","8":"Kyler Murray","9":"MurrKy00","10":"1","11":"0.048","12":"NA","13":"NA","14":"3","15":"0.143","16":"1","17":"4","18":"2","19":"0","20":"3","21":"0.115","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_02_LA_ARI","2":"202409150crd","3":"2024","4":"2","5":"REG","6":"LA","7":"ARI","8":"Matthew Stafford","9":"StafMa00","10":"2","11":"0.074","12":"NA","13":"NA","14":"5","15":"0.185","16":"5","17":"6","18":"1","19":"4","20":"10","21":"0.313","22":"NA","23":"NA","24":"NA","25":"00-0026498"},{"1":"2024_02_PIT_DEN","2":"202409150den","3":"2024","4":"2","5":"REG","6":"DEN","7":"PIT","8":"Bo Nix","9":"NixxBo00","10":"2","11":"0.059","12":"NA","13":"NA","14":"9","15":"0.265","16":"2","17":"8","18":"2","19":"4","20":"8","21":"0.205","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_02_PIT_DEN","2":"202409150den","3":"2024","4":"2","5":"REG","6":"PIT","7":"DEN","8":"Justin Fields","9":"FielJu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.222","16":"2","17":"12","18":"0","19":"4","20":"6","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_02_CIN_KC","2":"202409150kan","3":"2024","4":"2","5":"REG","6":"KC","7":"CIN","8":"Patrick Mahomes","9":"MahoPa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.174","16":"2","17":"5","18":"0","19":"2","20":"4","21":"0.129","22":"NA","23":"NA","24":"NA","25":"00-0033873"},{"1":"2024_02_CIN_KC","2":"202409150kan","3":"2024","4":"2","5":"REG","6":"CIN","7":"KC","8":"Joe Burrow","9":"BurrJo01","10":"3","11":"0.088","12":"NA","13":"NA","14":"5","15":"0.147","16":"3","17":"15","18":"0","19":"3","20":"6","21":"0.146","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_02_CHI_HOU","2":"202409150htx","3":"2024","4":"2","5":"REG","6":"HOU","7":"CHI","8":"C.J. Stroud","9":"StroCJ00","10":"1","11":"0.029","12":"NA","13":"NA","14":"5","15":"0.147","16":"3","17":"9","18":"5","19":"1","20":"9","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_02_CHI_HOU","2":"202409150htx","3":"2024","4":"2","5":"REG","6":"CHI","7":"HOU","8":"Caleb Williams","9":"WillCa03","10":"2","11":"0.059","12":"NA","13":"NA","14":"8","15":"0.235","16":"7","17":"15","18":"3","19":"3","20":"13","21":"0.271","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_02_ATL_PHI","2":"202409160phi","3":"2024","4":"2","5":"REG","6":"PHI","7":"ATL","8":"Jalen Hurts","9":"HurtJa00","10":"1","11":"0.034","12":"NA","13":"NA","14":"1","15":"0.034","16":"1","17":"9","18":"3","19":"4","20":"8","21":"0.229","22":"NA","23":"NA","24":"NA","25":"00-0036389"},{"1":"2024_02_ATL_PHI","2":"202409160phi","3":"2024","4":"2","5":"REG","6":"ATL","7":"PHI","8":"Kirk Cousins","9":"CousKi00","10":"1","11":"0.034","12":"NA","13":"NA","14":"4","15":"0.138","16":"1","17":"6","18":"3","19":"1","20":"5","21":"0.161","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_03_NE_NYJ","2":"202409190nyj","3":"2024","4":"3","5":"REG","6":"NYJ","7":"NE","8":"Aaron Rodgers","9":"RodgAa00","10":"2","11":"0.057","12":"NA","13":"NA","14":"5","15":"0.143","16":"2","17":"6","18":"0","19":"2","20":"4","21":"0.100","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_03_NE_NYJ","2":"202409190nyj","3":"2024","4":"3","5":"REG","6":"NE","7":"NYJ","8":"Jacoby Brissett","9":"BrisJa00","10":"1","11":"0.056","12":"NA","13":"NA","14":"4","15":"0.222","16":"5","17":"7","18":"2","19":"4","20":"11","21":"0.478","22":"NA","23":"NA","24":"NA","25":"00-0033119"},{"1":"2024_03_NE_NYJ","2":"202409190nyj","3":"2024","4":"3","5":"REG","6":"NE","7":"NYJ","8":"Drake Maye","9":"MayeDr00","10":"1","11":"0.125","12":"NA","13":"NA","14":"2","15":"0.250","16":"2","17":"2","18":"0","19":"1","20":"3","21":"0.250","22":"NA","23":"NA","24":"NA","25":"00-0039851"},{"1":"2024_03_NYG_CLE","2":"202409220cle","3":"2024","4":"3","5":"REG","6":"CLE","7":"NYG","8":"Deshaun Watson","9":"WatsDe00","10":"4","11":"0.114","12":"NA","13":"NA","14":"7","15":"0.200","16":"8","17":"19","18":"0","19":"7","20":"15","21":"0.319","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_03_NYG_CLE","2":"202409220cle","3":"2024","4":"3","5":"REG","6":"NYG","7":"CLE","8":"Daniel Jones","9":"JoneDa05","10":"4","11":"0.121","12":"NA","13":"NA","14":"2","15":"0.061","16":"2","17":"9","18":"1","19":"7","20":"10","21":"0.263","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_03_NYG_CLE","2":"202409220cle","3":"2024","4":"3","5":"REG","6":"NYG","7":"CLE","8":"Malik Nabers","9":"NabeMa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"1.000","16":"0","17":"1","18":"1","19":"0","20":"1","21":"1.000","22":"NA","23":"NA","24":"NA","25":"00-0039337"},{"1":"2024_03_CHI_IND","2":"202409220clt","3":"2024","4":"3","5":"REG","6":"IND","7":"CHI","8":"Anthony Richardson","9":"RichAn03","10":"2","11":"0.111","12":"NA","13":"NA","14":"3","15":"0.167","16":"1","17":"3","18":"4","19":"2","20":"7","21":"0.318","22":"NA","23":"NA","24":"NA","25":"00-0039164"},{"1":"2024_03_CHI_IND","2":"202409220clt","3":"2024","4":"3","5":"REG","6":"CHI","7":"IND","8":"Caleb Williams","9":"WillCa03","10":"1","11":"0.021","12":"NA","13":"NA","14":"11","15":"0.229","16":"4","17":"7","18":"7","19":"1","20":"12","21":"0.214","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_03_HOU_MIN","2":"202409220min","3":"2024","4":"3","5":"REG","6":"MIN","7":"HOU","8":"Sam Darnold","9":"DarnSa00","10":"2","11":"0.080","12":"NA","13":"NA","14":"3","15":"0.120","16":"4","17":"6","18":"5","19":"3","20":"12","21":"0.375","22":"NA","23":"NA","24":"NA","25":"00-0034869"},{"1":"2024_03_HOU_MIN","2":"202409220min","3":"2024","4":"3","5":"REG","6":"HOU","7":"MIN","8":"C.J. Stroud","9":"StroCJ00","10":"1","11":"0.033","12":"NA","13":"NA","14":"5","15":"0.167","16":"4","17":"14","18":"2","19":"2","20":"8","21":"0.211","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_03_HOU_MIN","2":"202409220min","3":"2024","4":"3","5":"REG","6":"HOU","7":"MIN","8":"Davis Mills","9":"MillDa02","10":"1","11":"0.083","12":"NA","13":"NA","14":"2","15":"0.167","16":"1","17":"9","18":"1","19":"1","20":"3","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0036898"},{"1":"2024_03_HOU_MIN","2":"202409220min","3":"2024","4":"3","5":"REG","6":"HOU","7":"MIN","8":"Stefon Diggs","9":"DiggSt00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0031588"},{"1":"2024_03_PHI_NO","2":"202409220nor","3":"2024","4":"3","5":"REG","6":"NO","7":"PHI","8":"Derek Carr","9":"CarrDe02","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.042","16":"1","17":"6","18":"2","19":"3","20":"6","21":"0.222","22":"NA","23":"NA","24":"NA","25":"00-0031280"},{"1":"2024_03_PHI_NO","2":"202409220nor","3":"2024","4":"3","5":"REG","6":"PHI","7":"NO","8":"Jalen Hurts","9":"HurtJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.139","16":"4","17":"13","18":"3","19":"4","20":"11","21":"0.244","22":"NA","23":"NA","24":"NA","25":"00-0036389"},{"1":"2024_03_LAC_PIT","2":"202409220pit","3":"2024","4":"3","5":"REG","6":"PIT","7":"LAC","8":"Justin Fields","9":"FielJu00","10":"2","11":"0.065","12":"NA","13":"NA","14":"3","15":"0.097","16":"2","17":"10","18":"1","19":"3","20":"6","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_03_LAC_PIT","2":"202409220pit","3":"2024","4":"3","5":"REG","6":"LAC","7":"PIT","8":"Justin Herbert","9":"HerbJu00","10":"2","11":"0.111","12":"NA","13":"NA","14":"3","15":"0.167","16":"2","17":"6","18":"2","19":"2","20":"6","21":"0.300","22":"NA","23":"NA","24":"NA","25":"00-0036355"},{"1":"2024_03_LAC_PIT","2":"202409220pit","3":"2024","4":"3","5":"REG","6":"LAC","7":"PIT","8":"Taylor Heinicke","9":"HeinTa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"3","17":"0","18":"0","19":"0","20":"3","21":"0.600","22":"NA","23":"NA","24":"NA","25":"00-0031800"},{"1":"2024_03_DEN_TB","2":"202409220tam","3":"2024","4":"3","5":"REG","6":"TB","7":"DEN","8":"Baker Mayfield","9":"MayfBa00","10":"2","11":"0.063","12":"NA","13":"NA","14":"3","15":"0.094","16":"7","17":"17","18":"6","19":"2","20":"15","21":"0.375","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_03_DEN_TB","2":"202409220tam","3":"2024","4":"3","5":"REG","6":"DEN","7":"TB","8":"Bo Nix","9":"NixxBo00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.118","16":"0","17":"17","18":"6","19":"2","20":"8","21":"0.205","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_03_GB_TEN","2":"202409220oti","3":"2024","4":"3","5":"REG","6":"TEN","7":"GB","8":"Will Levis","9":"LeviWi00","10":"3","11":"0.091","12":"NA","13":"NA","14":"4","15":"0.121","16":"8","17":"7","18":"0","19":"2","20":"10","21":"0.227","22":"NA","23":"NA","24":"NA","25":"00-0039152"},{"1":"2024_03_GB_TEN","2":"202409220oti","3":"2024","4":"3","5":"REG","6":"GB","7":"TEN","8":"Malik Willis","9":"WillMa12","10":"2","11":"0.105","12":"NA","13":"NA","14":"4","15":"0.211","16":"3","17":"6","18":"0","19":"0","20":"3","21":"0.120","22":"NA","23":"NA","24":"NA","25":"00-0038128"},{"1":"2024_03_CAR_LV","2":"202409220rai","3":"2024","4":"3","5":"REG","6":"LV","7":"CAR","8":"Gardner Minshew II","9":"MinsGa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.148","16":"2","17":"8","18":"1","19":"2","20":"5","21":"0.156","22":"NA","23":"NA","24":"NA","25":"00-0035289"},{"1":"2024_03_CAR_LV","2":"202409220rai","3":"2024","4":"3","5":"REG","6":"LV","7":"CAR","8":"Aidan O'Connell","9":"OConAi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.167","16":"1","17":"2","18":"1","19":"1","20":"3","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0038579"},{"1":"2024_03_CAR_LV","2":"202409220rai","3":"2024","4":"3","5":"REG","6":"CAR","7":"LV","8":"Andy Dalton","9":"DaltAn00","10":"2","11":"0.054","12":"NA","13":"NA","14":"4","15":"0.108","16":"2","17":"22","18":"3","19":"2","20":"7","21":"0.179","22":"NA","23":"NA","24":"NA","25":"00-0027973"},{"1":"2024_03_MIA_SEA","2":"202409220sea","3":"2024","4":"3","5":"REG","6":"SEA","7":"MIA","8":"Geno Smith","9":"SmitGe00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.121","16":"3","17":"8","18":"4","19":"3","20":"10","21":"0.270","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_03_MIA_SEA","2":"202409220sea","3":"2024","4":"3","5":"REG","6":"MIA","7":"SEA","8":"Skylar Thompson","9":"ThomSk00","10":"1","11":"0.056","12":"NA","13":"NA","14":"2","15":"0.111","16":"5","17":"6","18":"2","19":"4","20":"11","21":"0.458","22":"NA","23":"NA","24":"NA","25":"00-0037327"},{"1":"2024_03_MIA_SEA","2":"202409220sea","3":"2024","4":"3","5":"REG","6":"MIA","7":"SEA","8":"Tim Boyle","9":"BoylTi00","10":"1","11":"0.077","12":"NA","13":"NA","14":"3","15":"0.231","16":"1","17":"0","18":"0","19":"2","20":"3","21":"0.200","22":"NA","23":"NA","24":"NA","25":"NA"},{"1":"2024_03_DET_ARI","2":"202409220crd","3":"2024","4":"3","5":"REG","6":"ARI","7":"DET","8":"Kyler Murray","9":"MurrKy00","10":"0","11":"0.000","12":"NA","13":"NA","14":"8","15":"0.235","16":"1","17":"8","18":"3","19":"3","20":"7","21":"0.189","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_03_DET_ARI","2":"202409220crd","3":"2024","4":"3","5":"REG","6":"DET","7":"ARI","8":"Jared Goff","9":"GoffJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.174","16":"2","17":"7","18":"0","19":"0","20":"2","21":"0.077","22":"NA","23":"NA","24":"NA","25":"00-0033106"},{"1":"2024_03_BAL_DAL","2":"202409220dal","3":"2024","4":"3","5":"REG","6":"DAL","7":"BAL","8":"Dak Prescott","9":"PresDa01","10":"1","11":"0.020","12":"NA","13":"NA","14":"12","15":"0.240","16":"3","17":"16","18":"2","19":"5","20":"10","21":"0.182","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_03_BAL_DAL","2":"202409220dal","3":"2024","4":"3","5":"REG","6":"BAL","7":"DAL","8":"Lamar Jackson","9":"JackLa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.200","16":"0","17":"6","18":"0","19":"1","20":"1","21":"0.059","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_03_SF_LA","2":"202409220ram","3":"2024","4":"3","5":"REG","6":"LA","7":"SF","8":"Matthew Stafford","9":"StafMa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.136","16":"3","17":"7","18":"3","19":"2","20":"8","21":"0.286","22":"NA","23":"NA","24":"NA","25":"00-0026498"},{"1":"2024_03_SF_LA","2":"202409220ram","3":"2024","4":"3","5":"REG","6":"LA","7":"SF","8":"Tutu Atwell","9":"AtweTu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0036849"},{"1":"2024_03_SF_LA","2":"202409220ram","3":"2024","4":"3","5":"REG","6":"SF","7":"LA","8":"Brock Purdy","9":"PurdBr00","10":"3","11":"0.100","12":"NA","13":"NA","14":"3","15":"0.100","16":"1","17":"6","18":"4","19":"4","20":"9","21":"0.237","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_03_KC_ATL","2":"202409220atl","3":"2024","4":"3","5":"REG","6":"ATL","7":"KC","8":"Kirk Cousins","9":"CousKi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.111","16":"2","17":"12","18":"3","19":"8","20":"13","21":"0.419","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_03_KC_ATL","2":"202409220atl","3":"2024","4":"3","5":"REG","6":"KC","7":"ATL","8":"Patrick Mahomes","9":"MahoPa00","10":"2","11":"0.056","12":"NA","13":"NA","14":"6","15":"0.167","16":"0","17":"7","18":"1","19":"7","20":"8","21":"0.190","22":"NA","23":"NA","24":"NA","25":"00-0033873"},{"1":"2024_03_JAX_BUF","2":"202409230buf","3":"2024","4":"3","5":"REG","6":"BUF","7":"JAX","8":"Josh Allen","9":"AlleJo02","10":"1","11":"0.034","12":"NA","13":"NA","14":"2","15":"0.069","16":"0","17":"9","18":"1","19":"1","20":"2","21":"0.059","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_03_JAX_BUF","2":"202409230buf","3":"2024","4":"3","5":"REG","6":"BUF","7":"JAX","8":"Mitchell Trubisky","9":"TrubMi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0033869"},{"1":"2024_03_JAX_BUF","2":"202409230buf","3":"2024","4":"3","5":"REG","6":"JAX","7":"BUF","8":"Trevor Lawrence","9":"LawrTr00","10":"2","11":"0.056","12":"NA","13":"NA","14":"7","15":"0.194","16":"4","17":"8","18":"3","19":"3","20":"10","21":"0.233","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_03_JAX_BUF","2":"202409230buf","3":"2024","4":"3","5":"REG","6":"JAX","7":"BUF","8":"Mac Jones","9":"JoneMa05","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.125","16":"1","17":"0","18":"0","19":"0","20":"1","21":"0.111","22":"NA","23":"NA","24":"NA","25":"00-0036972"},{"1":"2024_03_WAS_CIN","2":"202409230cin","3":"2024","4":"3","5":"REG","6":"CIN","7":"WAS","8":"Joe Burrow","9":"BurrJo01","10":"1","11":"0.026","12":"NA","13":"NA","14":"5","15":"0.132","16":"2","17":"6","18":"0","19":"2","20":"4","21":"0.098","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_03_WAS_CIN","2":"202409230cin","3":"2024","4":"3","5":"REG","6":"WAS","7":"CIN","8":"Jayden Daniels","9":"DaniJa02","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.087","16":"2","17":"8","18":"1","19":"1","20":"4","21":"0.133","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_04_DAL_NYG","2":"202409260nyg","3":"2024","4":"4","5":"REG","6":"NYG","7":"DAL","8":"Daniel Jones","9":"JoneDa05","10":"2","11":"0.050","12":"NA","13":"NA","14":"3","15":"0.075","16":"1","17":"11","18":"0","19":"2","20":"3","21":"0.073","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_04_DAL_NYG","2":"202409260nyg","3":"2024","4":"4","5":"REG","6":"DAL","7":"NYG","8":"Dak Prescott","9":"PresDa01","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.074","16":"1","17":"6","18":"1","19":"2","20":"4","21":"0.143","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_04_NO_ATL","2":"202409290atl","3":"2024","4":"4","5":"REG","6":"ATL","7":"NO","8":"Kirk Cousins","9":"CousKi00","10":"3","11":"0.088","12":"NA","13":"NA","14":"3","15":"0.088","16":"1","17":"4","18":"1","19":"3","20":"5","21":"0.139","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_04_NO_ATL","2":"202409290atl","3":"2024","4":"4","5":"REG","6":"NO","7":"ATL","8":"Derek Carr","9":"CarrDe02","10":"2","11":"0.056","12":"NA","13":"NA","14":"4","15":"0.111","16":"1","17":"10","18":"1","19":"2","20":"4","21":"0.105","22":"NA","23":"NA","24":"NA","25":"00-0031280"},{"1":"2024_04_CIN_CAR","2":"202409290car","3":"2024","4":"4","5":"REG","6":"CAR","7":"CIN","8":"Andy Dalton","9":"DaltAn00","10":"3","11":"0.077","12":"NA","13":"NA","14":"6","15":"0.154","16":"0","17":"12","18":"1","19":"2","20":"3","21":"0.071","22":"NA","23":"NA","24":"NA","25":"00-0027973"},{"1":"2024_04_CIN_CAR","2":"202409290car","3":"2024","4":"4","5":"REG","6":"CAR","7":"CIN","8":"Johnny Hekker","9":"HekkJo00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"NA"},{"1":"2024_04_CIN_CAR","2":"202409290car","3":"2024","4":"4","5":"REG","6":"CIN","7":"CAR","8":"Joe Burrow","9":"BurrJo01","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.167","16":"0","17":"9","18":"2","19":"2","20":"4","21":"0.125","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_04_LA_CHI","2":"202409290chi","3":"2024","4":"4","5":"REG","6":"CHI","7":"LA","8":"Caleb Williams","9":"WillCa03","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.261","16":"3","17":"9","18":"2","19":"1","20":"6","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_04_LA_CHI","2":"202409290chi","3":"2024","4":"4","5":"REG","6":"LA","7":"CHI","8":"Matthew Stafford","9":"StafMa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.207","16":"3","17":"11","18":"1","19":"4","20":"8","21":"0.250","22":"NA","23":"NA","24":"NA","25":"00-0026498"},{"1":"2024_04_MIN_GB","2":"202409290gnb","3":"2024","4":"4","5":"REG","6":"GB","7":"MIN","8":"Jordan Love","9":"LoveJo03","10":"4","11":"0.074","12":"NA","13":"NA","14":"9","15":"0.167","16":"1","17":"25","18":"9","19":"9","20":"19","21":"0.339","22":"NA","23":"NA","24":"NA","25":"00-0036264"},{"1":"2024_04_MIN_GB","2":"202409290gnb","3":"2024","4":"4","5":"REG","6":"MIN","7":"GB","8":"Sam Darnold","9":"DarnSa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.222","16":"2","17":"7","18":"6","19":"1","20":"9","21":"0.273","22":"NA","23":"NA","24":"NA","25":"00-0034869"},{"1":"2024_04_JAX_HOU","2":"202409290htx","3":"2024","4":"4","5":"REG","6":"HOU","7":"JAX","8":"C.J. Stroud","9":"StroCJ00","10":"2","11":"0.051","12":"NA","13":"NA","14":"7","15":"0.179","16":"2","17":"2","18":"7","19":"5","20":"14","21":"0.311","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_04_JAX_HOU","2":"202409290htx","3":"2024","4":"4","5":"REG","6":"JAX","7":"HOU","8":"Trevor Lawrence","9":"LawrTr00","10":"2","11":"0.063","12":"NA","13":"NA","14":"7","15":"0.219","16":"1","17":"13","18":"3","19":"2","20":"6","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_04_PIT_IND","2":"202409290clt","3":"2024","4":"4","5":"REG","6":"IND","7":"PIT","8":"Joe Flacco","9":"FlacJo00","10":"1","11":"0.042","12":"NA","13":"NA","14":"4","15":"0.167","16":"2","17":"10","18":"0","19":"4","20":"6","21":"0.207","22":"NA","23":"NA","24":"NA","25":"00-0026158"},{"1":"2024_04_PIT_IND","2":"202409290clt","3":"2024","4":"4","5":"REG","6":"IND","7":"PIT","8":"Anthony Richardson","9":"RichAn03","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.250","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0039164"},{"1":"2024_04_PIT_IND","2":"202409290clt","3":"2024","4":"4","5":"REG","6":"PIT","7":"IND","8":"Justin Fields","9":"FielJu00","10":"2","11":"0.063","12":"NA","13":"NA","14":"3","15":"0.094","16":"4","17":"5","18":"4","19":"3","20":"11","21":"0.262","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_04_DEN_NYJ","2":"202409290nyj","3":"2024","4":"4","5":"REG","6":"NYJ","7":"DEN","8":"Aaron Rodgers","9":"RodgAa00","10":"2","11":"0.049","12":"NA","13":"NA","14":"11","15":"0.268","16":"5","17":"21","18":"1","19":"8","20":"14","21":"0.275","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_04_DEN_NYJ","2":"202409290nyj","3":"2024","4":"4","5":"REG","6":"DEN","7":"NYJ","8":"Bo Nix","9":"NixxBo00","10":"2","11":"0.080","12":"NA","13":"NA","14":"10","15":"0.400","16":"0","17":"7","18":"5","19":"2","20":"7","21":"0.259","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_04_PHI_TB","2":"202409290tam","3":"2024","4":"4","5":"REG","6":"TB","7":"PHI","8":"Baker Mayfield","9":"MayfBa00","10":"3","11":"0.064","12":"NA","13":"NA","14":"6","15":"0.128","16":"2","17":"12","18":"1","19":"1","20":"4","21":"0.080","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_04_PHI_TB","2":"202409290tam","3":"2024","4":"4","5":"REG","6":"PHI","7":"TB","8":"Jalen Hurts","9":"HurtJa00","10":"1","11":"0.034","12":"NA","13":"NA","14":"6","15":"0.207","16":"6","17":"15","18":"4","19":"2","20":"12","21":"0.324","22":"NA","23":"NA","24":"NA","25":"00-0036389"},{"1":"2024_04_WAS_ARI","2":"202409290crd","3":"2024","4":"4","5":"REG","6":"ARI","7":"WAS","8":"Kyler Murray","9":"MurrKy00","10":"3","11":"0.136","12":"NA","13":"NA","14":"2","15":"0.091","16":"4","17":"6","18":"2","19":"1","20":"7","21":"0.259","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_04_WAS_ARI","2":"202409290crd","3":"2024","4":"4","5":"REG","6":"WAS","7":"ARI","8":"Jayden Daniels","9":"DaniJa02","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.100","16":"0","17":"5","18":"0","19":"1","20":"1","21":"0.028","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_04_NE_SF","2":"202409290sfo","3":"2024","4":"4","5":"REG","6":"SF","7":"NE","8":"Brock Purdy","9":"PurdBr00","10":"1","11":"0.038","12":"NA","13":"NA","14":"5","15":"0.192","16":"1","17":"9","18":"2","19":"3","20":"6","21":"0.200","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_04_NE_SF","2":"202409290sfo","3":"2024","4":"4","5":"REG","6":"NE","7":"SF","8":"Jacoby Brissett","9":"BrisJa00","10":"3","11":"0.094","12":"NA","13":"NA","14":"5","15":"0.156","16":"6","17":"13","18":"4","19":"6","20":"16","21":"0.410","22":"NA","23":"NA","24":"NA","25":"00-0033119"},{"1":"2024_04_KC_LAC","2":"202409290sdg","3":"2024","4":"4","5":"REG","6":"LAC","7":"KC","8":"Justin Herbert","9":"HerbJu00","10":"4","11":"0.148","12":"NA","13":"NA","14":"5","15":"0.185","16":"2","17":"8","18":"1","19":"8","20":"11","21":"0.379","22":"NA","23":"NA","24":"NA","25":"00-0036355"},{"1":"2024_04_KC_LAC","2":"202409290sdg","3":"2024","4":"4","5":"REG","6":"KC","7":"LAC","8":"Patrick Mahomes","9":"MahoPa00","10":"1","11":"0.036","12":"NA","13":"NA","14":"4","15":"0.143","16":"3","17":"6","18":"2","19":"1","20":"6","21":"0.176","22":"NA","23":"NA","24":"NA","25":"00-0033873"},{"1":"2024_04_CLE_LV","2":"202409290rai","3":"2024","4":"4","5":"REG","6":"LV","7":"CLE","8":"Gardner Minshew II","9":"MinsGa00","10":"3","11":"0.125","12":"NA","13":"NA","14":"6","15":"0.250","16":"2","17":"15","18":"1","19":"2","20":"5","21":"0.192","22":"NA","23":"NA","24":"NA","25":"00-0035289"},{"1":"2024_04_CLE_LV","2":"202409290rai","3":"2024","4":"4","5":"REG","6":"CLE","7":"LV","8":"Deshaun Watson","9":"WatsDe00","10":"3","11":"0.094","12":"NA","13":"NA","14":"2","15":"0.063","16":"3","17":"7","18":"1","19":"7","20":"11","21":"0.262","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_04_BUF_BAL","2":"202409290rav","3":"2024","4":"4","5":"REG","6":"BAL","7":"BUF","8":"Lamar Jackson","9":"JackLa00","10":"4","11":"0.235","12":"NA","13":"NA","14":"0","15":"0.000","16":"1","17":"3","18":"0","19":"1","20":"2","21":"0.105","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_04_BUF_BAL","2":"202409290rav","3":"2024","4":"4","5":"REG","6":"BAL","7":"BUF","8":"Josh Johnson","9":"JohnJo05","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"1","20":"1","21":"1.000","22":"NA","23":"NA","24":"NA","25":"00-0026300"},{"1":"2024_04_BUF_BAL","2":"202409290rav","3":"2024","4":"4","5":"REG","6":"BUF","7":"BAL","8":"Josh Allen","9":"AlleJo02","10":"5","11":"0.200","12":"NA","13":"NA","14":"4","15":"0.160","16":"3","17":"9","18":"0","19":"6","20":"9","21":"0.265","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_04_BUF_BAL","2":"202409290rav","3":"2024","4":"4","5":"REG","6":"BUF","7":"BAL","8":"Mitchell Trubisky","9":"TrubMi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.500","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0033869"},{"1":"2024_04_TEN_MIA","2":"202409300mia","3":"2024","4":"4","5":"REG","6":"MIA","7":"TEN","8":"Tyler Huntley","9":"HuntTy01","10":"1","11":"0.048","12":"NA","13":"NA","14":"5","15":"0.238","16":"2","17":"0","18":"1","19":"3","20":"6","21":"0.231","22":"NA","23":"NA","24":"NA","25":"00-0035993"},{"1":"2024_04_TEN_MIA","2":"202409300mia","3":"2024","4":"4","5":"REG","6":"TEN","7":"MIA","8":"Mason Rudolph","9":"RudoMa00","10":"2","11":"0.143","12":"NA","13":"NA","14":"0","15":"0.000","16":"1","17":"2","18":"1","19":"2","20":"4","21":"0.222","22":"NA","23":"NA","24":"NA","25":"00-0034771"},{"1":"2024_04_TEN_MIA","2":"202409300mia","3":"2024","4":"4","5":"REG","6":"TEN","7":"MIA","8":"Will Levis","9":"LeviWi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.250","16":"0","17":"0","18":"1","19":"0","20":"1","21":"0.200","22":"NA","23":"NA","24":"NA","25":"00-0039152"},{"1":"2024_04_SEA_DET","2":"202409300det","3":"2024","4":"4","5":"REG","6":"DET","7":"SEA","8":"Jared Goff","9":"GoffJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"3","17":"10","18":"3","19":"1","20":"7","21":"0.333","22":"NA","23":"NA","24":"NA","25":"00-0033106"},{"1":"2024_04_SEA_DET","2":"202409300det","3":"2024","4":"4","5":"REG","6":"DET","7":"SEA","8":"Amon-Ra St. Brown","9":"StxxAm00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0036963"},{"1":"2024_04_SEA_DET","2":"202409300det","3":"2024","4":"4","5":"REG","6":"SEA","7":"DET","8":"Geno Smith","9":"SmitGe00","10":"2","11":"0.038","12":"NA","13":"NA","14":"4","15":"0.075","16":"3","17":"21","18":"5","19":"5","20":"13","21":"0.210","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_05_TB_ATL","2":"202410030atl","3":"2024","4":"5","5":"REG","6":"ATL","7":"TB","8":"Kirk Cousins","9":"CousKi00","10":"4","11":"0.074","12":"NA","13":"NA","14":"0","15":"0.000","16":"4","17":"12","18":"0","19":"6","20":"10","21":"0.161","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_05_TB_ATL","2":"202410030atl","3":"2024","4":"5","5":"REG","6":"ATL","7":"TB","8":"Darnell Mooney","9":"MoonDa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"1","20":"1","21":"1.000","22":"NA","23":"NA","24":"NA","25":"00-0036309"},{"1":"2024_05_TB_ATL","2":"202410030atl","3":"2024","4":"5","5":"REG","6":"TB","7":"ATL","8":"Baker Mayfield","9":"MayfBa00","10":"2","11":"0.083","12":"NA","13":"NA","14":"2","15":"0.083","16":"1","17":"10","18":"0","19":"0","20":"1","21":"0.033","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_05_NYJ_MIN","2":"202410060min","3":"2024","4":"5","5":"REG","6":"MIN","7":"NYJ","8":"Sam Darnold","9":"DarnSa00","10":"1","11":"0.037","12":"NA","13":"NA","14":"6","15":"0.222","16":"4","17":"11","18":"6","19":"2","20":"12","21":"0.333","22":"NA","23":"NA","24":"NA","25":"00-0034869"},{"1":"2024_05_NYJ_MIN","2":"202410060min","3":"2024","4":"5","5":"REG","6":"MIN","7":"NYJ","8":"Nick Mullens","9":"MullNi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"1","20":"1","21":"1.000","22":"NA","23":"NA","24":"NA","25":"00-0033319"},{"1":"2024_05_NYJ_MIN","2":"202410060min","3":"2024","4":"5","5":"REG","6":"NYJ","7":"MIN","8":"Aaron Rodgers","9":"RodgAa00","10":"2","11":"0.039","12":"NA","13":"NA","14":"12","15":"0.235","16":"3","17":"24","18":"4","19":"8","20":"15","21":"0.263","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_05_CAR_CHI","2":"202410060chi","3":"2024","4":"5","5":"REG","6":"CHI","7":"CAR","8":"Caleb Williams","9":"WillCa03","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.214","16":"1","17":"12","18":"0","19":"1","20":"2","21":"0.057","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_05_CAR_CHI","2":"202410060chi","3":"2024","4":"5","5":"REG","6":"CAR","7":"CHI","8":"Andy Dalton","9":"DaltAn00","10":"1","11":"0.036","12":"NA","13":"NA","14":"5","15":"0.179","16":"3","17":"9","18":"1","19":"4","20":"8","21":"0.250","22":"NA","23":"NA","24":"NA","25":"00-0027973"},{"1":"2024_05_CAR_CHI","2":"202410060chi","3":"2024","4":"5","5":"REG","6":"CAR","7":"CHI","8":"Bryce Young","9":"YounBr01","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.143","16":"1","17":"1","18":"2","19":"0","20":"3","21":"0.333","22":"NA","23":"NA","24":"NA","25":"00-0039150"},{"1":"2024_05_BAL_CIN","2":"202410060cin","3":"2024","4":"5","5":"REG","6":"CIN","7":"BAL","8":"Joe Burrow","9":"BurrJo01","10":"1","11":"0.026","12":"NA","13":"NA","14":"3","15":"0.077","16":"3","17":"6","18":"0","19":"3","20":"6","21":"0.140","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_05_BAL_CIN","2":"202410060cin","3":"2024","4":"5","5":"REG","6":"BAL","7":"CIN","8":"Lamar Jackson","9":"JackLa00","10":"1","11":"0.024","12":"NA","13":"NA","14":"13","15":"0.310","16":"1","17":"19","18":"5","19":"6","20":"12","21":"0.255","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_05_BUF_HOU","2":"202410060htx","3":"2024","4":"5","5":"REG","6":"HOU","7":"BUF","8":"C.J. Stroud","9":"StroCJ00","10":"4","11":"0.114","12":"NA","13":"NA","14":"2","15":"0.057","16":"1","17":"9","18":"1","19":"6","20":"8","21":"0.190","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_05_BUF_HOU","2":"202410060htx","3":"2024","4":"5","5":"REG","6":"BUF","7":"HOU","8":"Josh Allen","9":"AlleJo02","10":"4","11":"0.138","12":"NA","13":"NA","14":"12","15":"0.414","16":"1","17":"10","18":"2","19":"8","20":"11","21":"0.314","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_05_IND_JAX","2":"202410060jax","3":"2024","4":"5","5":"REG","6":"JAX","7":"IND","8":"Trevor Lawrence","9":"LawrTr00","10":"0","11":"0.000","12":"NA","13":"NA","14":"1","15":"0.029","16":"0","17":"5","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_05_IND_JAX","2":"202410060jax","3":"2024","4":"5","5":"REG","6":"IND","7":"JAX","8":"Joe Flacco","9":"FlacJo00","10":"2","11":"0.045","12":"NA","13":"NA","14":"5","15":"0.114","16":"4","17":"6","18":"1","19":"2","20":"7","21":"0.143","22":"NA","23":"NA","24":"NA","25":"00-0026158"},{"1":"2024_05_IND_JAX","2":"202410060jax","3":"2024","4":"5","5":"REG","6":"IND","7":"JAX","8":"Adonai Mitchell","9":"MitcAd00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0039890"},{"1":"2024_05_MIA_NE","2":"202410060nwe","3":"2024","4":"5","5":"REG","6":"NE","7":"MIA","8":"Jacoby Brissett","9":"BrisJa00","10":"3","11":"0.097","12":"NA","13":"NA","14":"5","15":"0.161","16":"2","17":"14","18":"1","19":"7","20":"10","21":"0.270","22":"NA","23":"NA","24":"NA","25":"00-0033119"},{"1":"2024_05_MIA_NE","2":"202410060nwe","3":"2024","4":"5","5":"REG","6":"MIA","7":"NE","8":"Tyler Huntley","9":"HuntTy01","10":"4","11":"0.129","12":"NA","13":"NA","14":"4","15":"0.129","16":"3","17":"7","18":"1","19":"1","20":"5","21":"0.139","22":"NA","23":"NA","24":"NA","25":"00-0035993"},{"1":"2024_05_CLE_WAS","2":"202410060was","3":"2024","4":"5","5":"REG","6":"WAS","7":"CLE","8":"Jayden Daniels","9":"DaniJa02","10":"2","11":"0.080","12":"NA","13":"NA","14":"5","15":"0.200","16":"3","17":"15","18":"0","19":"0","20":"3","21":"0.088","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_05_CLE_WAS","2":"202410060was","3":"2024","4":"5","5":"REG","6":"WAS","7":"CLE","8":"Marcus Mariota","9":"MariMa01","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"1","19":"0","20":"1","21":"0.333","22":"NA","23":"NA","24":"NA","25":"00-0032268"},{"1":"2024_05_CLE_WAS","2":"202410060was","3":"2024","4":"5","5":"REG","6":"CLE","7":"WAS","8":"Deshaun Watson","9":"WatsDe00","10":"2","11":"0.074","12":"NA","13":"NA","14":"6","15":"0.222","16":"7","17":"12","18":"1","19":"3","20":"11","21":"0.289","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_05_CLE_WAS","2":"202410060was","3":"2024","4":"5","5":"REG","6":"CLE","7":"WAS","8":"Jameis Winston","9":"WinsJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0031503"},{"1":"2024_05_LV_DEN","2":"202410060den","3":"2024","4":"5","5":"REG","6":"DEN","7":"LV","8":"Bo Nix","9":"NixxBo00","10":"1","11":"0.038","12":"NA","13":"NA","14":"3","15":"0.115","16":"3","17":"10","18":"1","19":"1","20":"5","21":"0.156","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_05_LV_DEN","2":"202410060den","3":"2024","4":"5","5":"REG","6":"LV","7":"DEN","8":"Aidan O'Connell","9":"OConAi00","10":"1","11":"0.053","12":"NA","13":"NA","14":"7","15":"0.368","16":"1","17":"2","18":"7","19":"3","20":"11","21":"0.524","22":"NA","23":"NA","24":"NA","25":"00-0038579"},{"1":"2024_05_LV_DEN","2":"202410060den","3":"2024","4":"5","5":"REG","6":"LV","7":"DEN","8":"Gardner Minshew II","9":"MinsGa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.176","16":"2","17":"8","18":"0","19":"0","20":"2","21":"0.095","22":"NA","23":"NA","24":"NA","25":"00-0035289"},{"1":"2024_05_ARI_SF","2":"202410060sfo","3":"2024","4":"5","5":"REG","6":"SF","7":"ARI","8":"Brock Purdy","9":"PurdBr00","10":"2","11":"0.063","12":"NA","13":"NA","14":"5","15":"0.156","16":"2","17":"5","18":"2","19":"3","20":"7","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_05_ARI_SF","2":"202410060sfo","3":"2024","4":"5","5":"REG","6":"ARI","7":"SF","8":"Kyler Murray","9":"MurrKy00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.167","16":"1","17":"12","18":"1","19":"1","20":"3","21":"0.091","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_05_GB_LA","2":"202410060ram","3":"2024","4":"5","5":"REG","6":"LA","7":"GB","8":"Matthew Stafford","9":"StafMa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"11","15":"0.244","16":"3","17":"14","18":"5","19":"6","20":"14","21":"0.292","22":"NA","23":"NA","24":"NA","25":"00-0026498"},{"1":"2024_05_GB_LA","2":"202410060ram","3":"2024","4":"5","5":"REG","6":"GB","7":"LA","8":"Jordan Love","9":"LoveJo03","10":"3","11":"0.115","12":"NA","13":"NA","14":"5","15":"0.192","16":"2","17":"10","18":"4","19":"1","20":"7","21":"0.241","22":"NA","23":"NA","24":"NA","25":"00-0036264"},{"1":"2024_05_NYG_SEA","2":"202410060sea","3":"2024","4":"5","5":"REG","6":"SEA","7":"NYG","8":"Geno Smith","9":"SmitGe00","10":"5","11":"0.128","12":"NA","13":"NA","14":"2","15":"0.051","16":"7","17":"10","18":"1","19":"1","20":"9","21":"0.176","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_05_NYG_SEA","2":"202410060sea","3":"2024","4":"5","5":"REG","6":"NYG","7":"SEA","8":"Daniel Jones","9":"JoneDa05","10":"3","11":"0.097","12":"NA","13":"NA","14":"4","15":"0.129","16":"3","17":"15","18":"5","19":"4","20":"12","21":"0.308","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_05_DAL_PIT","2":"202410060pit","3":"2024","4":"5","5":"REG","6":"PIT","7":"DAL","8":"Justin Fields","9":"FielJu00","10":"2","11":"0.080","12":"NA","13":"NA","14":"4","15":"0.160","16":"3","17":"7","18":"4","19":"3","20":"10","21":"0.333","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_05_DAL_PIT","2":"202410060pit","3":"2024","4":"5","5":"REG","6":"PIT","7":"DAL","8":"Kyle Allen","9":"AlleKy00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0034577"},{"1":"2024_05_DAL_PIT","2":"202410060pit","3":"2024","4":"5","5":"REG","6":"DAL","7":"PIT","8":"Dak Prescott","9":"PresDa01","10":"0","11":"0.000","12":"NA","13":"NA","14":"8","15":"0.195","16":"2","17":"5","18":"5","19":"3","20":"10","21":"0.222","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_05_NO_KC","2":"202410070kan","3":"2024","4":"5","5":"REG","6":"KC","7":"NO","8":"Patrick Mahomes","9":"MahoPa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.147","16":"2","17":"8","18":"3","19":"4","20":"9","21":"0.205","22":"NA","23":"NA","24":"NA","25":"00-0033873"},{"1":"2024_05_NO_KC","2":"202410070kan","3":"2024","4":"5","5":"REG","6":"NO","7":"KC","8":"Derek Carr","9":"CarrDe02","10":"1","11":"0.038","12":"NA","13":"NA","14":"6","15":"0.231","16":"1","17":"11","18":"6","19":"4","20":"11","21":"0.379","22":"NA","23":"NA","24":"NA","25":"00-0031280"},{"1":"2024_05_NO_KC","2":"202410070kan","3":"2024","4":"5","5":"REG","6":"NO","7":"KC","8":"Jake Haener","9":"HaenJa00","10":"1","11":"0.167","12":"NA","13":"NA","14":"1","15":"0.167","16":"0","17":"3","18":"1","19":"4","20":"5","21":"0.556","22":"NA","23":"NA","24":"NA","25":"00-0038998"},{"1":"2024_06_SF_SEA","2":"202410100sea","3":"2024","4":"6","5":"REG","6":"SEA","7":"SF","8":"Geno Smith","9":"SmitGe00","10":"4","11":"0.082","12":"NA","13":"NA","14":"6","15":"0.122","16":"1","17":"4","18":"2","19":"4","20":"7","21":"0.132","22":"NA","23":"NA","24":"NA","25":"00-0030565"},{"1":"2024_06_SF_SEA","2":"202410100sea","3":"2024","4":"6","5":"REG","6":"SF","7":"SEA","8":"Brock Purdy","9":"PurdBr00","10":"2","11":"0.074","12":"NA","13":"NA","14":"3","15":"0.111","16":"0","17":"4","18":"0","19":"4","20":"4","21":"0.129","22":"NA","23":"NA","24":"NA","25":"00-0037834"},{"1":"2024_06_JAX_CHI","2":"202410130chi","3":"2024","4":"6","5":"REG","6":"CHI","7":"JAX","8":"Caleb Williams","9":"WillCa03","10":"0","11":"0.000","12":"NA","13":"NA","14":"2","15":"0.077","16":"3","17":"5","18":"1","19":"1","20":"5","21":"0.147","22":"NA","23":"NA","24":"NA","25":"00-0039918"},{"1":"2024_06_JAX_CHI","2":"202410130chi","3":"2024","4":"6","5":"REG","6":"JAX","7":"CHI","8":"Trevor Lawrence","9":"LawrTr00","10":"3","11":"0.088","12":"NA","13":"NA","14":"3","15":"0.088","16":"3","17":"9","18":"0","19":"3","20":"6","21":"0.146","22":"NA","23":"NA","24":"NA","25":"00-0036971"},{"1":"2024_06_JAX_CHI","2":"202410130chi","3":"2024","4":"6","5":"REG","6":"JAX","7":"CHI","8":"Mac Jones","9":"JoneMa05","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"1","17":"0","18":"0","19":"0","20":"1","21":"0.500","22":"NA","23":"NA","24":"NA","25":"00-0036972"},{"1":"2024_06_WAS_BAL","2":"202410130rav","3":"2024","4":"6","5":"REG","6":"BAL","7":"WAS","8":"Lamar Jackson","9":"JackLa00","10":"1","11":"0.040","12":"NA","13":"NA","14":"2","15":"0.080","16":"2","17":"12","18":"5","19":"2","20":"9","21":"0.300","22":"NA","23":"NA","24":"NA","25":"00-0034796"},{"1":"2024_06_WAS_BAL","2":"202410130rav","3":"2024","4":"6","5":"REG","6":"WAS","7":"BAL","8":"Jayden Daniels","9":"DaniJa02","10":"1","11":"0.030","12":"NA","13":"NA","14":"3","15":"0.091","16":"3","17":"10","18":"3","19":"4","20":"10","21":"0.238","22":"NA","23":"NA","24":"NA","25":"00-0039910"},{"1":"2024_06_ARI_GB","2":"202410130gnb","3":"2024","4":"6","5":"REG","6":"GB","7":"ARI","8":"Jordan Love","9":"LoveJo03","10":"1","11":"0.031","12":"NA","13":"NA","14":"5","15":"0.156","16":"0","17":"9","18":"4","19":"2","20":"6","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0036264"},{"1":"2024_06_ARI_GB","2":"202410130gnb","3":"2024","4":"6","5":"REG","6":"ARI","7":"GB","8":"Kyler Murray","9":"MurrKy00","10":"1","11":"0.031","12":"NA","13":"NA","14":"8","15":"0.250","16":"0","17":"6","18":"5","19":"1","20":"6","21":"0.167","22":"NA","23":"NA","24":"NA","25":"00-0035228"},{"1":"2024_06_HOU_NE","2":"202410130nwe","3":"2024","4":"6","5":"REG","6":"NE","7":"HOU","8":"Drake Maye","9":"MayeDr00","10":"1","11":"0.032","12":"NA","13":"NA","14":"6","15":"0.194","16":"4","17":"11","18":"4","19":"4","20":"12","21":"0.286","22":"NA","23":"NA","24":"NA","25":"00-0039851"},{"1":"2024_06_HOU_NE","2":"202410130nwe","3":"2024","4":"6","5":"REG","6":"HOU","7":"NE","8":"C.J. Stroud","9":"StroCJ00","10":"2","11":"0.067","12":"NA","13":"NA","14":"5","15":"0.167","16":"2","17":"14","18":"9","19":"1","20":"12","21":"0.353","22":"NA","23":"NA","24":"NA","25":"00-0039163"},{"1":"2024_06_HOU_NE","2":"202410130nwe","3":"2024","4":"6","5":"REG","6":"HOU","7":"NE","8":"Davis Mills","9":"MillDa02","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"0","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0036898"},{"1":"2024_06_TB_NO","2":"202410130nor","3":"2024","4":"6","5":"REG","6":"NO","7":"TB","8":"Spencer Rattler","9":"RattSp00","10":"2","11":"0.053","12":"NA","13":"NA","14":"9","15":"0.237","16":"5","17":"11","18":"1","19":"5","20":"11","21":"0.229","22":"NA","23":"NA","24":"NA","25":"00-0039376"},{"1":"2024_06_TB_NO","2":"202410130nor","3":"2024","4":"6","5":"REG","6":"TB","7":"NO","8":"Baker Mayfield","9":"MayfBa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.139","16":"1","17":"7","18":"2","19":"1","20":"4","21":"0.100","22":"NA","23":"NA","24":"NA","25":"00-0034855"},{"1":"2024_06_CLE_PHI","2":"202410130phi","3":"2024","4":"6","5":"REG","6":"PHI","7":"CLE","8":"Jalen Hurts","9":"HurtJa00","10":"0","11":"0.000","12":"NA","13":"NA","14":"5","15":"0.208","16":"1","17":"15","18":"3","19":"1","20":"5","21":"0.192","22":"NA","23":"NA","24":"NA","25":"00-0036389"},{"1":"2024_06_CLE_PHI","2":"202410130phi","3":"2024","4":"6","5":"REG","6":"CLE","7":"PHI","8":"Deshaun Watson","9":"WatsDe00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.174","16":"5","17":"11","18":"1","19":"2","20":"8","21":"0.267","22":"NA","23":"NA","24":"NA","25":"00-0033537"},{"1":"2024_06_IND_TEN","2":"202410130oti","3":"2024","4":"6","5":"REG","6":"TEN","7":"IND","8":"Will Levis","9":"LeviWi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.148","16":"0","17":"10","18":"0","19":"4","20":"4","21":"0.133","22":"NA","23":"NA","24":"NA","25":"00-0039152"},{"1":"2024_06_IND_TEN","2":"202410130oti","3":"2024","4":"6","5":"REG","6":"IND","7":"TEN","8":"Joe Flacco","9":"FlacJo00","10":"1","11":"0.028","12":"NA","13":"NA","14":"11","15":"0.306","16":"0","17":"12","18":"3","19":"2","20":"5","21":"0.128","22":"NA","23":"NA","24":"NA","25":"00-0026158"},{"1":"2024_06_LAC_DEN","2":"202410130den","3":"2024","4":"6","5":"REG","6":"DEN","7":"LAC","8":"Bo Nix","9":"NixxBo00","10":"2","11":"0.063","12":"NA","13":"NA","14":"6","15":"0.188","16":"2","17":"9","18":"1","19":"4","20":"7","21":"0.171","22":"NA","23":"NA","24":"NA","25":"00-0039732"},{"1":"2024_06_LAC_DEN","2":"202410130den","3":"2024","4":"6","5":"REG","6":"LAC","7":"DEN","8":"Justin Herbert","9":"HerbJu00","10":"0","11":"0.000","12":"NA","13":"NA","14":"4","15":"0.129","16":"3","17":"18","18":"3","19":"3","20":"9","21":"0.237","22":"NA","23":"NA","24":"NA","25":"00-0036355"},{"1":"2024_06_PIT_LV","2":"202410130rai","3":"2024","4":"6","5":"REG","6":"LV","7":"PIT","8":"Aidan O'Connell","9":"OConAi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"6","15":"0.162","16":"1","17":"5","18":"1","19":"2","20":"4","21":"0.098","22":"NA","23":"NA","24":"NA","25":"00-0038579"},{"1":"2024_06_PIT_LV","2":"202410130rai","3":"2024","4":"6","5":"REG","6":"PIT","7":"LV","8":"Justin Fields","9":"FielJu00","10":"1","11":"0.043","12":"NA","13":"NA","14":"5","15":"0.217","16":"3","17":"10","18":"1","19":"2","20":"6","21":"0.194","22":"NA","23":"NA","24":"NA","25":"00-0036945"},{"1":"2024_06_ATL_CAR","2":"202410130car","3":"2024","4":"6","5":"REG","6":"CAR","7":"ATL","8":"Andy Dalton","9":"DaltAn00","10":"3","11":"0.081","12":"NA","13":"NA","14":"3","15":"0.081","16":"0","17":"8","18":"1","19":"3","20":"4","21":"0.100","22":"NA","23":"NA","24":"NA","25":"00-0027973"},{"1":"2024_06_ATL_CAR","2":"202410130car","3":"2024","4":"6","5":"REG","6":"ATL","7":"CAR","8":"Kirk Cousins","9":"CousKi00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.100","16":"0","17":"5","18":"0","19":"3","20":"3","21":"0.100","22":"NA","23":"NA","24":"NA","25":"00-0029604"},{"1":"2024_06_DET_DAL","2":"202410130dal","3":"2024","4":"6","5":"REG","6":"DAL","7":"DET","8":"Dak Prescott","9":"PresDa01","10":"1","11":"0.031","12":"NA","13":"NA","14":"9","15":"0.281","16":"4","17":"12","18":"10","19":"7","20":"21","21":"0.553","22":"NA","23":"NA","24":"NA","25":"00-0033077"},{"1":"2024_06_DET_DAL","2":"202410130dal","3":"2024","4":"6","5":"REG","6":"DAL","7":"DET","8":"Cooper Rush","9":"RushCo00","10":"0","11":"0.000","12":"NA","13":"NA","14":"3","15":"0.273","16":"0","17":"2","18":"1","19":"0","20":"1","21":"0.091","22":"NA","23":"NA","24":"NA","25":"00-0033662"},{"1":"2024_06_DET_DAL","2":"202410130dal","3":"2024","4":"6","5":"REG","6":"DET","7":"DAL","8":"Jared Goff","9":"GoffJa00","10":"1","11":"0.040","12":"NA","13":"NA","14":"5","15":"0.200","16":"2","17":"10","18":"2","19":"3","20":"7","21":"0.241","22":"NA","23":"NA","24":"NA","25":"00-0033106"},{"1":"2024_06_DET_DAL","2":"202410130dal","3":"2024","4":"6","5":"REG","6":"DET","7":"DAL","8":"Hendon Hooker","9":"HookHe00","10":"0","11":"0.000","12":"NA","13":"NA","14":"0","15":"0.000","16":"1","17":"1","18":"1","19":"0","20":"2","21":"0.667","22":"NA","23":"NA","24":"NA","25":"00-0038550"},{"1":"2024_06_CIN_NYG","2":"202410130nyg","3":"2024","4":"6","5":"REG","6":"NYG","7":"CIN","8":"Daniel Jones","9":"JoneDa05","10":"1","11":"0.027","12":"NA","13":"NA","14":"7","15":"0.189","16":"2","17":"14","18":"2","19":"4","20":"8","21":"0.178","22":"NA","23":"NA","24":"NA","25":"00-0035710"},{"1":"2024_06_CIN_NYG","2":"202410130nyg","3":"2024","4":"6","5":"REG","6":"CIN","7":"NYG","8":"Joe Burrow","9":"BurrJo01","10":"1","11":"0.042","12":"NA","13":"NA","14":"1","15":"0.042","16":"4","17":"3","18":"2","19":"3","20":"9","21":"0.265","22":"NA","23":"NA","24":"NA","25":"00-0036442"},{"1":"2024_06_BUF_NYJ","2":"202410140nyj","3":"2024","4":"6","5":"REG","6":"NYJ","7":"BUF","8":"Aaron Rodgers","9":"RodgAa00","10":"3","11":"0.088","12":"NA","13":"NA","14":"1","15":"0.029","16":"3","17":"6","18":"2","19":"2","20":"7","21":"0.184","22":"NA","23":"NA","24":"NA","25":"00-0023459"},{"1":"2024_06_BUF_NYJ","2":"202410140nyj","3":"2024","4":"6","5":"REG","6":"BUF","7":"NYJ","8":"Josh Allen","9":"AlleJo02","10":"1","11":"0.043","12":"NA","13":"NA","14":"1","15":"0.043","16":"2","17":"9","18":"5","19":"0","20":"7","21":"0.233","22":"NA","23":"NA","24":"NA","25":"00-0034857"},{"1":"2024_07_DEN_NO","2":"202410170nor","3":"2024","4":"7","5":"REG","6":"NO","7":"DEN","8":"Spencer Rattler","9":"RattSp00","10":"3","11":"0.086","12":"NA","13":"NA","14":"4","15":"0.114","16":"6","17":"6","18":"0","19":"4","20":"10","21":"0.227","22":"NA","23":"NA","24":"NA","25":"00-0039376"},{"1":"2024_07_DEN_NO","2":"202410170nor","3":"2024","4":"7","5":"REG","6":"NO","7":"DEN","8":"Jake Haener","9":"HaenJa00","10":"1","11":"0.250","12":"NA","13":"NA","14":"0","15":"0.000","16":"0","17":"3","18":"0","19":"0","20":"0","21":"0.000","22":"NA","23":"NA","24":"NA","25":"00-0038998"},{"1":"2024_07_DEN_NO","2":"202410170nor","3":"2024","4":"7","5":"REG","6":"DEN","7":"NO","8":"Bo Nix","9":"NixxBo00","10":"2","11":"0.080","12":"NA","13":"NA","14":"5","15":"0.200","16":"0","17":"8","18":"2","19":"0","20":"2","21":"0.061","22":"NA","23":"NA","24":"NA","25":"00-0039732"}],"options":{"columns":{"min":{},"max":[10],"total":[25]},"rows":{"min":[10],"max":[10],"total":[223]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->







<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbImRhdGEuZnJhbWUiXSwibnJvdyI6MjgsIm5jb2wiOjMsInN1bW1hcnkiOnsiRGVzY3JpcHRpb24iOlsiZGYgWzI4IMOXIDNdIl19fSwicmRmIjoiSDRzSUFBQUFBQUFBQSsxVlhXdmJNQlJWODlYRnFidEE2VVpZeHZRSEVoaURzdGVWVXRqTEdySU91aWVqMklvdDZzaENrcHRsVC92bDNTUkhVbTA1Wlc5N21zR0o3cm5uWG4zNG5xdmwxZDJINEM0QUFIUkJyNmQrKzJvSSt0OXVyMmNmQWVoMWxIRUVlbUNvLzM4bzkxbkZCR0NzM3FseERGaU9kcGdicXljeDJqalBta2NrTVZiSWtCQVJraEp2bUJRR1BGbHBJSWxXS004dEZzaU1GMXUwUlR1TERBUWo5OWhhL1lRWHpCb3Z0Qkd4V05yZ0ZVcWlLb0ZsaEE2cDBjS0NSaktWVFdaZ3dDZmFRR0FrQ21xc0VTdmllNnlDeUFiYlBIb3NvbFZPNUUrY05NR3M1Snc0Y0doQVluTy8zQU9NWXlGSzduZ25GcWd0WThoWkVlbGpGblZnaDNqaXpyRmltQU0yMktuRFdreGVpc3huVmxpZE9XTElUeGxhYU05ckZzSXd6aEJIc1hTMThIZmdtSlliekVuODMveEhadk9MalJhVmRDRkZycUF0VkpOeHVMaGV3cjNJNGVjckI2b3lnTDZhTHlzMXc0YWFiMXRxL2xwWDgybmxGMURybURrVlRCYVl4NWhLV0t5aFBFUUlMbEVDRytwOTF3NlJHWkp3aXpsV0s3S0I0eHNLSmVJcGxzM3dOKzN3d2pMZHd1dmQ0TlduQjh4UmlxSFdNU1FVN3J1RDhiNytVbTVXNnNCME5xMXoyR3dSTFhleldaeTEzSzV0VEh5WDMwRGVOalppbHVlVGFoTXNGemV3M2x2QzcxcmJldlBLNHc3M2ljL3FIOTZqbmV1cUlEU0Z1d001enBlcXd6d2JxWjNQUlU1MFVVTFZPSWpDMllIQ2F4RmNKdThXNit0U3Q0MnJhOEUxd2JucjB3bVNLSkk3NWhTUllCRnp3blJ1TDl0UWxjbmNaZ3pWMi9rRnFtZnFUeHZuYWxGbVdnc0dlcWI1bW12eEFmRG9oUndYMVl3cXFLTnYzWUVYZk1ROVlGeFN2WkprRm1jbHZaKzl2L0Q4WFVaVFBXa0Y3Wi9RaktlMWNYZS9qTTV2RXo2d3RZOXBTcWc5azM2T1ZqaTNtUlA4NEM2U1lsdWR4NXh4UXQyZHJOVTBsNFZFTmlTSWk5d2kxZGJCNHgrbzIrTjBpd2dBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["field"],"name":[1],"type":["chr"],"align":["left"]},{"label":["data_type"],"name":[2],"type":["chr"],"align":["left"]},{"label":["description"],"name":[3],"type":["chr"],"align":["left"]}],"data":[{"1":"player","2":"character","3":"Player name"},{"1":"team","2":"character","3":"Player team"},{"1":"pfr_id","2":"character","3":"PFR player ID"},{"1":"pass_attempts","2":"numeric","3":"Pass attempts"},{"1":"batted_balls","2":"numeric","3":"Batted balls"},{"1":"throwaways","2":"numeric","3":"Throwaways"},{"1":"spikes","2":"numeric","3":"Spikes"},{"1":"drops","2":"numeric","3":"Throws dropped"},{"1":"drop_pct","2":"numeric","3":"Percent of throws dropped"},{"1":"bad_throws","2":"numeric","3":"Bad throws"},{"1":"bad_throw_pct","2":"numeric","3":"Percent of throws that were bad"},{"1":"on_tgt_throws","2":"numeric","3":"On target throws"},{"1":"on_tgt_pct","2":"numeric","3":"Percent of throws on target"},{"1":"season","2":"numeric","3":"Season"},{"1":"pocket_time","2":"numeric","3":"Average time in pocket"},{"1":"times_blitzed","2":"numeric","3":"Number of times blitzed"},{"1":"times_hurried","2":"numeric","3":"Number of times hurried"},{"1":"times_hit","2":"numeric","3":"Number of times hit"},{"1":"times_pressured","2":"numeric","3":"Number of times pressured"},{"1":"pressure_pct","2":"numeric","3":"Percent of the time pressured"},{"1":"rpo_plays","2":"numeric","3":"Number of RPO plays"},{"1":"rpo_yards","2":"numeric","3":"Yards on RPOs"},{"1":"rpo_pass_att","2":"numeric","3":"Number of pass attempts on RPOs"},{"1":"rpo_pass_yards","2":"numeric","3":"Passing yards on RPOs"},{"1":"rpo_rush_att","2":"numeric","3":"Rush attempts on RPOs"},{"1":"rpo_rush_yards","2":"numeric","3":"Rushing yards on RPOs"},{"1":"pa_pass_att","2":"numeric","3":"Play action pass attempts"},{"1":"pa_pass_yards","2":"numeric","3":"Play action passing yards"}],"options":{"columns":{"min":{},"max":[10],"total":[3]},"rows":{"min":[10],"max":[10],"total":[28]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->



<!-- rnb-text-end -->

