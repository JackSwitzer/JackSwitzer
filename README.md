### contributions-heatmap.html ###
<div class="heatmap-container">
  <canvas id="heatmapCanvas" style="width: 100%; height: auto;"></canvas>
</div>

<script>
  const canvas = document.getElementById('heatmapCanvas');
  const ctx = canvas.getContext('2d');

  // Sample data for contributions heatmap
  const contributions = [
    { day: 'Monday', value: 5 },
    { day: 'Tuesday', value: 15 },
    { day: 'Wednesday', value: 7 },
    { day: 'Thursday', value: 20 },
    { day: 'Friday', value: 10 },
    { day: 'Saturday', value: 12 },
    { day: 'Sunday', value: 8 }
  ];

  // Heatmap colors
  const colors = ['#f4f4f4', '#c6e48b', '#7bc96f', '#239a3b', '#196127'];

  function drawHeatmap(data) {
    const barWidth = canvas.width / data.length;
    data.forEach((contribution, index) => {
      const colorIndex = Math.min(Math.floor(contribution.value / 5), colors.length - 1);
      ctx.fillStyle = colors[colorIndex];
      ctx.fillRect(index * barWidth, canvas.height - contribution.value * 10, barWidth, contribution.value * 10);
      ctx.fillStyle = '#000';
      ctx.fillText(contribution.day, index * barWidth + barWidth / 4, canvas.height - 5);
    });
  }

  drawHeatmap(contributions);
</script>

### github-stats.html ###
<div class="stats-container">
  <canvas id="statsCanvas" style="width: 100%; height: auto;"></canvas>
</div>

<script>
  const statsCanvas = document.getElementById('statsCanvas');
  const statsCtx = statsCanvas.getContext('2d');

  // Sample data for GitHub stats
  const statsData = [
    { label: 'Commits', value: 120 },
    { label: 'Pull Requests', value: 45 },
    { label: 'Issues', value: 30 },
    { label: 'Stars', value: 75 }
  ];

  function drawStatsChart(data) {
    const total = data.reduce((acc, stat) => acc + stat.value, 0);
    let currentAngle = 0;

    data.forEach((stat) => {
      const sliceAngle = (stat.value / total) * 2 * Math.PI;
      statsCtx.beginPath();
      statsCtx.moveTo(statsCanvas.width / 2, statsCanvas.height / 2);
      statsCtx.arc(statsCanvas.width / 2, statsCanvas.height / 2, statsCanvas.width / 3, currentAngle, currentAngle + sliceAngle);
      currentAngle += sliceAngle;
      statsCtx.closePath();
      statsCtx.fillStyle = `hsl(${Math.random() * 360}, 70%, 70%)`;
      statsCtx.fill();
    });
  }

  drawStatsChart(statsData);
</script>

### README.md ###
# Jack Switzer
3rd Year Applied Math & Comp Eng @ Queen's University

Part-time NYT Connections Warrior

## Contributions Heatmap:
<div class="heatmap-container">
  <canvas id="heatmapCanvas" style="width: 100%; height: auto;"></canvas>
</div>
<script src="contributions-heatmap.html"></script>

## GitHub Stats:
<div class="stats-container">
  <canvas id="statsCanvas" style="width: 100%; height: auto;"></canvas>
</div>
<script src="github-stats.html"></script>

---
