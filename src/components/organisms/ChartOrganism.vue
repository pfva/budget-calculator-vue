<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8 d-flex justify-content-center">
      <svg class="o-chart" v-show="showChart" v-bind:class="{'u-fadein': showChart}"></svg>
    </div>
  </div>
</template>

<script>
import * as d3 from "d3";
export default {
  data() {
    return {
      expensesData: []
    };
  },
  props: ["showChart", "expenses"],
  mounted() {
    window.onresize = () => {
      this.drawChart();
    };
  },
  updated() {
    this.transformData();
    this.drawChart();
  },
  watch: {
    expenses: function() {
      this.transformData();
      this.drawChart();
    }
  },
  methods: {
    transformData() {
      this.expensesData = [];
      this.expenses[1].forEach(item => {
        let percentage =
          ((item.value / this.expenses[0]) * 100).toFixed(0) + "%";

        this.expensesData.push({
          label: item.title,
          value: item.value,
          percentage: percentage
        });
      });
    },
    drawChart() {
      let data = this.expensesData;

      let chartEl = document.querySelector(".o-chart");
      chartEl.innerHTML = "";
      let chartStyles = window.getComputedStyle(chartEl);

      let color = d3
        .scaleOrdinal()
        .domain(data.map(d => d.name))
        .range(
          d3.quantize(t => d3.interpolateSpectral(t * 0.9), data.length + 1)
        );

      let width = parseInt(chartStyles.width);
      let height = parseInt(chartStyles.height);
      let radius = Math.min(width, height) / 2;

      let pie = d3
        .pie()
        .sort(null)
        .value(d => d.value);

      let arcs = pie(data);

      let arc = d3
        .arc()
        .innerRadius(0)
        .outerRadius(radius);

      let svg = d3.select("svg");

      let g = svg
        .append("g")
        .attr("transform", "translate(" + width / 2 + "," + height / 2 + ")");

      let pathIndex = 0;
      g.selectAll("path")
        .data(arcs)
        .enter()
        .append("path")
        .attr("fill", (d, i) => color(i))
        .attr("stroke", "lightgray")
        .attr("d", arc)
        .attr("data-key", function(i) {
          i = pathIndex++;
          return i;
        });

      let textIndex = 0;
      let text = g
        .selectAll("text")
        .data(arcs)
        .enter()
        .append("text")
        .attr("transform", function(d) {
          d.innerRadius = 0;
          d.outerRadius = radius;
          let c = arc.centroid(d);
          return "translate(" + c[0] * 1.4 + "," + c[1] * 1.4 + ")";
        })
        .attr("data-key", function(i) {
          i = textIndex++;
          return i;
        });

      text
        .append("tspan")
        .attr("text-anchor", "middle")
        .attr("x", 0)
        .attr("y", "-0.7em")
        .text((d, i) => data[i].label)
        .append("tspan")
        .attr("x", 0)
        .attr("y", "0.7em")
        .text(d => d.data.percentage);

      let oChart = document.querySelector(".o-chart");
      let oChartPaths = oChart.querySelectorAll("path");
      let oChartTexts = oChart.querySelectorAll("text");

      for (let k = 0; k < oChartPaths.length; k++) {
        oChartPaths[k].addEventListener("mouseenter", function() {
          for (let l = 0; l < oChartTexts.length; l++) {
            if (oChartTexts[l].dataset.key !== oChartPaths[k].dataset.key) {
              oChartTexts[l].classList.add("u-invisible");
            }
          }
        });
        oChartPaths[k].addEventListener("click", function() {
          for (let l = 0; l < oChartTexts.length; l++) {
            if (oChartTexts[l].dataset.key !== oChartPaths[k].dataset.key) {
              oChartTexts[l].classList.toggle("u-invisible");
            }
          }
        });
        oChartPaths[k].addEventListener("mouseleave", function() {
          for (let m = 0; m < oChartTexts.length; m++) {
            oChartTexts[m].classList.remove("u-invisible");
          }
        });
      }
    }
  }
};
</script>

<style lang="scss">
.o-chart {
  width: calc(100% - 18px);
  height: 460px;

  @media (min-width: 992px) {
    margin-top: $spacing * 6;
    height: 520px;
  }

  &--invisible-height {
    height: 0px;
  }

  g {
    path {
      transition: all 1s;
      &:hover {
        @media (min-width: 768px) {
          transform-origin: 50% 50% 50%;
          transform: scale(0.95);
        }
      }
    }

    text {
      fill: $white;
      font-family: $category-font-family;
      font-size: 12px;
      font-weight: 300;
      text-shadow: 0 0 10px #000;
      pointer-events: none;

      @media (min-width: 768px) {
        font-size: 16px;
      }
    }
  }
}
</style>
