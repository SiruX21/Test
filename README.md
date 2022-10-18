## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
719.23 sec
<br>
<sup><sub>(
11:59 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [462.20]},
      {label: 'FML stuff:', data: [257.03]}
    ]
  },
  options: {
    scales: {
      xAxes: [{display: false,stacked: true}],
      yAxes: [{display: false,stacked: true}],
    },
    elements: {rectangle: {borderWidth: 2}},
    legend: {display: false,},
    plugins: {datalabels: {color: 'white',formatter: (value, context) =>
      [context.dataset.label, value].join(' ')
    }}
  }
}"/>
</p>

<br>

# Mods Loading Time
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=300&c={
  type: 'outlabeledPie',
  options: {
    cutoutPercentage: 25,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v,i)=>[
          v.labels[v.dataIndex],' ',
          (v.percent*1000|0)/10,
          String.fromCharCode(37)].join('')
      }
    }
  },
  data: {...
`
3e76ba 119.20s Just Enough Items;
386AA7  37.87s Just Enough Items (Plugins);
a651a8  26.36s IndustrialCraft 2;
7c813e  23.87s Thaumcraft;
9e2174   2.16s Tinkers' Construct;
8E1E68  19.84s Tinkers' Construct (Oredict Melting);
219e2a  17.34s BuildCraft Lib;
8f3087  15.45s Forge Mod Loader;
8f304e  13.39s Astral Sorcery;
516fa8  11.49s Ender IO;
6e3a17  11.10s Quark;
216364  10.87s Thermal Expansion;
3e76ba  10.07s Railcraft;
5162a8   8.17s Applied Energistics 2;
213664   7.58s Forestry;
8c2ccd   7.02s Immersive Engineering;
3eb2ba   5.41s Botania;
3e8160   4.40s The Twilight Forest;
8f8630   4.27s GenDustry;
a86e51   4.03s Extra Utilities 2;
3eb6ba   3.71s Chisels & Bits;
649e21   2.99s OpenBlocks;
444444  45.30s 26 Other mods;
333333  47.75s 115 'Fast' mods (load 1.0s - 0.1s);
222222   2.57s 69 'Instant' mods (load %3C 0.1s)
`
    .split(';').reduce((a, l) => {
      l.match(/(\w{6}) *(\d*\.\d*)s (.*)/)
      .slice(1).map((a, i) => [[String.fromCharCode(35),a].join(''), parseFloat(a), a][i])
      .forEach((s, i) => 
        [a.datasets[0].backgroundColor, a.datasets[0].data, a.labels][i].push(s)
      );
      return a
    }, {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 1
      }]
    })
  }
}"/>
</p>

<br>

# Top Mods Details (except JEI, FML and Forge)
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=450&c={
  options: {
    scales: {
      xAxes: [{stacked: true}],
      yAxes: [{stacked: true}],
    },
    plugins: {
      datalabels: {
        anchor: 'end',
        align: 'top',
        color: 'white',
        backgroundColor: 'rgba(46, 140, 171, 0.6)',
        borderColor: 'rgba(41, 168, 194, 1.0)',
        borderWidth: 0.5,
        borderRadius: 3,
        padding: 0,
        font: {size:10},
        formatter: (v,ctx) => 
          ctx.datasetIndex!=ctx.chart.data.datasets.length-1 ? null
            : [((ctx.chart.data.datasets.reduce((a,b)=>a- -b.data[ctx.dataIndex],0)*10)|0)/10,'s'].join('')
      },
      colorschemes: {
        scheme: 'office.Damask6'
      }
    }
  },
  type: 'bar',
  data: {...(() => {
    let a = { labels: [], datasets: [] };
`
1: Construction;
2: Loading Resources;
3: PreInitialization;
4: Initialization;
5: InterModComms$IMC;
6: PostInitialization;
7: LoadComplete;
8: ModIdMapping
`
    .split(';')
      .map(l => l.match(/\d: (.*)/).slice(1))
      .forEach(([name]) => a.datasets.push({ label: name, data: [] }));
`
                          1      2      3      4      5      6      7      8  ;
IndustrialCraft 2     |  1.61|  0.02| 22.35|  1.20|  0.00|  1.18|  0.00|  0.00;
Thaumcraft            |  0.73|  0.01|  0.45|  1.13|  0.01| 21.54|  0.00|  0.00;
Tinkers' Construct    |  1.15|  0.01|  0.24|  0.04|  0.00| 20.55|  0.00|  0.00;
BuildCraft Lib        |  0.13|  0.02|  1.03|  0.11|  0.00| 16.06|  0.00|  0.00;
Astral Sorcery        |  0.33|  0.01| 11.00|  1.38|  0.00|  0.67|  0.00|  0.00;
Ender IO              |  2.25|  0.02|  2.79|  0.98|  5.15|  0.29|  0.00|  0.00;
Quark                 |  0.05|  0.01| 10.47|  0.13|  0.00|  0.43|  0.00|  0.00;
Thermal Expansion     |  0.10|  0.01|  1.19|  0.22|  0.13|  9.11|  0.02|  0.10;
Railcraft             |  0.30|  0.01|  7.00|  2.24|  0.00|  0.52|  0.00|  0.00;
Applied Energistics 2 |  0.34|  0.02|  5.49|  0.48|  0.18|  1.66|  0.00|  0.00;
Forestry              |  0.97|  0.02|  5.31|  1.02|  0.02|  0.25|  0.00|  0.00;
Immersive Engineering |  1.52|  0.01|  1.80|  1.72|  0.00|  1.97|  0.00|  0.00
`
    .split(';').slice(1)
      .map(l => l.split('|').map(s => s.trim()))
      .forEach(([name, ...arr], i) => {
        a.labels.push(name);
        arr.forEach((v, j) => a.datasets[j].data[i] = v)
      }); return a
  })()}
}"/>
</p>

<br>

# TOP JEI Registered Plugis
<p align="center">
<img src="https://quickchart.io/chart?w=700&c={
  options: {
    elements: { rectangle: { borderWidth: 1 } },
    legend: false
  },
  type: 'horizontalBar',
    data: {...(() => {
      let a = {
        labels: [], datasets: [{
          backgroundColor: 'rgba(0, 99, 132, 0.5)',
          borderColor: 'rgb(0, 99, 132)',
          data: []
        }]
      };
`
  9.61: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  4.83: binnie.extratrees.integration.jei.ExtraTreesJeiPlugin;
  4.57: jeresources.jei.JEIConfig;
  4.50: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  2.78: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  1.76: ic2.jeiIntegration.SubModule;
  1.42: mezz.jei.plugins.vanilla.VanillaPlugin;
  1.38: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.08: forestry.factory.recipes.jei.FactoryJeiPlugin;
  1.06: blusunrize.immersiveengineering.common.util.compat.jei.JEIHelper;
  0.86: binnie.genetics.integration.jei.GeneticsJeiPlugin;
  0.75: com.buuz135.industrial.jei.JEICustomPlugin;
  0.72: net.bdew.jeibees.BeesJEIPlugin;
  0.36: com.chocohead.AdvMachines.JEICompat;
  0.24: crazypants.enderio.base.integration.jei.JeiPlugin;
  1.97: Other 67 Plugins
`
        .split(';')
        .map(l => l.split(':'))
        .forEach(([time, name]) => {
          a.labels.push(name);
          a.datasets[0].data.push(time)
        })
        ; return a
    })()
  }
}"/>
</p>

<br>

# FML Stuff
<p align="center">
<img src="https://quickchart.io/chart?w=500&h=400&c={
  options: {
    rotation: Math.PI,
    cutoutPercentage: 55,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v)=>v.labels
      },
      doughnutlabel: {
        labels: [
          {
            text: 'FML stuff:',
            color: 'rgba(128, 128, 128, 0.5)',
            font: {size: 18}
          },
          {
            text: [257.03,'s'].join(''),
            color: 'rgba(128, 128, 128, 1)',
            font: {size: 22}
          }
        ]
      },
    }
  },
  type: 'outlabeledPie',
  data: {...(() => {
    let a = {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 2
      }]
    };
`
993A00   2.90s Loading sounds;
994400   2.98s Loading Resource - SoundHandler;
994F00  30.60s ModelLoader: blocks;
995900   6.56s ModelLoader: items;
996300  19.68s ModelLoader: baking;
996D00  89.17s Indexing ingredients;
444444 105.14s Other
`
    .split(';')
      .map(l => l.match(/(\w{6}) *(\d*\.\d*)s (.*)/))
      .forEach(([, col, time, name]) => {
        a.labels.push([name, ' ', time, 's'].join(''));
        a.datasets[0].data.push(parseFloat(time));
        a.datasets[0].backgroundColor.push([String.fromCharCode(35), col].join(''))
      })
      ; return a
  })()}
}"/>
</p>

<br>
