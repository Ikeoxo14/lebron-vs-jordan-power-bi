# LeBron vs Jordan Power BI Analysis

I built this Power BI report to compare LeBron James and Michael Jordan using NBA regular-season statistics. The report examines the case for LeBron when longevity and all-around career production receive the most weight, while showing Jordan's higher scoring average.

**Author:** [Ike Okoroafor](https://github.com/Ikeoxo14)  
**Tools:** Microsoft Excel, Power Query, Power BI Desktop, DAX

[View the report PDF](LeBron_vs_Jordan.pdf.) · [Download the Power BI report](LeBron_vs_Jordan.pbix) · [Download the Excel source](LeBron_vs_Jordan_Season_Data.xlsx)

## Question

How do the players compare in career points, rebounds, assists, scoring averages, and active seasons, and how does the importance placed on longevity affect the argument for LeBron?

## Data scope

The dataset contains 38 player-season records: 23 LeBron seasons from 2003–04 through 2025–26 and 15 active Jordan seasons from 1984–85 through 2002–03. Each row represents one player's regular-season totals for one season.

The fields are Player, Season, Career Year, Games, Points, Rebounds, Assists, Steals, and Blocks. Career Year counts active seasons; seasons spent entirely in retirement are excluded. The report uses a fixed cutoff through 2025–26 and does not include playoffs.

## What I did

1. Organized the player-season data in Excel.
2. Imported the LeBron and Jordan tables into Power Query, removed a blank column, and assigned text and whole-number data types.
3. Appended the player tables into the combined PLAYERSTATS table.
4. Created DAX measures for games played, seasons played, career averages, and cumulative points.
5. Built three career-total bar charts, a comparison table, a cumulative scoring line chart, and a Player slicer.
6. Used consistent player colors and added the scope, sources, and interpretation to the report.
7. Compared the displayed career totals with source totals and exported a PDF preview.

## Findings

| Player | Active seasons | Games | Points | Rebounds | Assists |
|---|---:|---:|---:|---:|---:|
| LeBron James | 23 | 1,622 | 43,440 | 12,095 | 12,016 |
| Michael Jordan | 15 | 1,072 | 32,292 | 6,672 | 5,633 |

| Player | Points per game | Rebounds per game | Assists per game |
|---|---:|---:|---:|
| LeBron James | 26.8 | 7.5 | 7.4 |
| Michael Jordan | 30.1 | 6.2 | 5.3 |

LeBron leads these career totals and played more active seasons. He also leads in rebounds and assists per game. Jordan leads in points per game. These findings support the case for LeBron when longevity and sustained all-around production are the main criteria.

## Calculation approach

Career averages divide total production by total games. They are not simple averages of season averages.

```dax
Games Played = SUM(PLAYERSTATS[Games])
```

```dax
Seasons Played = DISTINCTCOUNT(PLAYERSTATS[Season])
```

```dax
PPG = DIVIDE(SUM(PLAYERSTATS[Points]), [Games Played])
```

RPG and APG use the same calculation with Rebounds and Assists. The cumulative points measure adds points through the current active Career Year while preserving the player's filter context. Jordan's series ends at active season 15; LeBron's ends at active season 23.

## Files and how to view them

| File | Purpose |
|---|---|
| README.md | Project question, method, sources, and findings |
| LeBron_vs_Jordan.pdf | Static report preview |
| LeBron_vs_Jordan.pbix | Power BI report with measures and interactive visuals |
| LeBron_vs_Jordan_Season_Data.xlsx | Player-season source data |

Open the PDF for a quick view. To explore the report, download the PBIX and open it in Power BI Desktop. Use the Player slicer to filter the visuals, then clear the selection to compare both players. To refresh the data, download the Excel workbook and update the report's Excel source path to its location on your computer.

## Sources

- [StatMuse — LeBron James season statistics](https://www.statmuse.com/nba/ask/lebron-career-points)
- [StatMuse — Michael Jordan season statistics](https://www.statmuse.com/nba/ask/michael-jordan-career-stats-year-by-year)
- [NBA.com — all-time regular-season leaders](https://www.nba.com/stats/alltime-leaders?PerMode=Totals&SeasonType=Regular+Season&StatCategory=PTS)

The workbook preserves the fixed dataset used for this report. Live source pages may show later totals.

## Limitations

The players have different career lengths, and career totals reward longevity. The report does not adjust for era, pace, minutes, or league environment, and it does not evaluate playoff performance, championships, awards, or overall defensive impact. Its conclusion depends on the comparison criteria rather than establishing an objective ranking of the greatest player.

