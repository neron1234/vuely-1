<!-- Product Sales Widget -->
<script>
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  data () {
    return {
      gradient1: null,
      gradient2: null,
      options: {
        scales: {
          yAxes: [{
            gridLines: {
              display: true,
              drawBorder: false
            },
            ticks: {
              stepSize: 50
            }
          }],
          xAxes: [{
            gridLines: {
              display: false,
              drawBorder: false
            }
          }]
        },
        tooltip: {
          enabled: true
        },
        legend: {
          display: false
        },
        responsive: true,
        maintainAspectRatio: true
      }
    }
  },
  mounted () {
    this.gradient1 = this.$refs.canvas.getContext('2d').createLinearGradient(0, 0, 0, 300)
    this.gradient2 = this.$refs.canvas.getContext('2d').createLinearGradient(0, 0, 0, 600)

    this.gradient1.addColorStop(0, 'rgba(60, 290, 160, 0.7)')
    this.gradient1.addColorStop(1, '#307FCF')

    this.gradient2.addColorStop(0, 'rgba(254, 140, 72, 0.8)')
    this.gradient2.addColorStop(1, '#Fc6373')

    this.renderChart({
      labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
      datasets: [
        {
          label: 'Data',
          lineTension: 0,
          pointRadius: 0,
          fill: true,
          backgroundColor: this.gradient1,
          borderWidth: 0,
          data: [80, 80, 160, 130, 50, 140, 100]
        },
        {
          label: 'Data 2',
          lineTension: 0,
          pointRadius: 0,
          fill: true,
          backgroundColor: this.gradient2,
          borderWidth: 0,
          data: [90, 140, 50, 120, 160, 90, 90]
        }
      ]
    }, this.options)
  }
}
</script>
