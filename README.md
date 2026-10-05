# College Football Strength of Record

## Ranking Methodology
- Each matchup defines an optimal distance, $d_{ij}=\text{sign}(m_{ij})\log(|m_{ij}|+1)$, between teams $i$ and $j$ based on the margin of victory, $m_{ij}$, in points. This transformation factors in win margin while diminishing the importance of running up the score too much. If a pair of teams plays more than once during the season, $m_{ij}$ is the average margin of victory across all matchups.
- Every team is started at position $x_i = 0$, then small updates are iteratively made to the positions. For each iteration, a team's optimal position update is computed based on the current positions of teams it has played and optimal distances: $\Delta x_i = \sum_j d_{ij}-(x_i-x_j)$. Then the positions are updated like $x_{i,\text{ new}} = x_i + \alpha \Delta x_i$, where $\alpha = 0.01$ is a small relaxation rate that could be changed. This relaxation is repeated for a fixed number of iterations (1,000).
- The final $x_i$ values are rounded to one decimal place, giving the final rankings and allowing for ties.
