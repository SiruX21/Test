## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
504.41 sec
<br>
<sup><sub>(
8:24 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [309.81]},
      {label: 'FML stuff:', data: [194.59]}
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
3e76ba  22.94s Just Enough Items;
386AA7  30.94s Just Enough Items (Plugins);
386AA7  26.08s Just Enough Items (Ingredient Filter);
a651a8  23.14s IndustrialCraft 2;
9e2174   2.09s Tinkers' Construct;
8E1E68  18.76s Tinkers' Construct (Oredict Melting);
219e2a  20.00s BuildCraft Lib;
8f304e  12.74s Astral Sorcery;
8f3087  10.86s Forge Mod Loader;
3e76ba  10.13s Railcraft;
6e3a17   9.24s Quark;
516fa8   8.83s Ender IO;
213664   6.82s Forestry;
8c2ccd   6.70s Immersive Engineering;
216364   6.02s Thermal Expansion;
8f8630   3.76s GenDustry;
3e8160   3.24s The Twilight Forest;
a86e51   3.18s Extra Utilities 2;
3eb2ba   3.12s Botania;
649e21   2.56s OpenBlocks;
5161a8   1.43s CraftTweaker2;
495797   1.01s CraftTweaker2 (Script Loading);
814a3e   2.17s RFTools;
575a2c   2.16s BuildCraft Silicon;
444444  24.40s 16 Other mods;
333333  44.54s 110 'Fast' mods (load 1.0s - 0.1s);
222222   2.93s 78 'Instant' mods (load %3C 0.1s)
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
IndustrialCraft 2     |  1.03|  0.02| 20.04|  0.82|  0.00|  1.24|  0.00|  0.00;
Tinkers' Construct    |  0.97|  0.01|  0.21|  0.04|  0.00| 19.63|  0.00|  0.00;
BuildCraft Lib        |  0.05|  0.01|  0.84|  0.12|  0.00| 18.98|  0.00|  0.00;
Astral Sorcery        |  0.32|  0.01| 10.14|  1.36|  0.00|  0.90|  0.00|  0.00;
Railcraft             |  0.23|  0.01|  7.29|  1.92|  0.00|  0.68|  0.00|  0.00;
Quark                 |  0.03|  0.01|  8.68|  0.12|  0.00|  0.40|  0.00|  0.00;
Ender IO              |  1.94|  0.02|  2.55|  0.49|  3.65|  0.18|  0.00|  0.00;
Forestry              |  0.45|  0.02|  4.70|  0.91|  0.01|  0.73|  0.00|  0.00;
Immersive Engineering |  1.42|  0.01|  1.73|  1.16|  0.00|  2.38|  0.00|  0.00;
Thermal Expansion     |  0.09|  0.00|  1.00|  0.10|  0.07|  4.70|  0.01|  0.05;
GenDustry             |  0.04|  0.00|  2.50|  0.13|  0.00|  1.08|  0.00|  0.00;
The Twilight Forest   |  0.88|  0.02|  1.10|  1.20|  0.04|  0.01|  0.00|  0.00
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
  6.35: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  5.62: jeresources.jei.JEIConfig;
  3.28: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  2.82: binnie.extratrees.integration.jei.ExtraTreesJeiPlugin;
  2.12: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  2.09: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  1.47: mezz.jei.plugins.vanilla.VanillaPlugin;
  1.13: forestry.factory.recipes.jei.FactoryJeiPlugin;
  0.91: ic2.jeiIntegration.SubModule;
  0.87: net.bdew.jeibees.BeesJEIPlugin;
  0.65: com.buuz135.industrial.jei.JEICustomPlugin;
  0.55: slimeknights.tconstruct.plugin.jei.JEIPlugin;
  0.49: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.36: com.chocohead.AdvMachines.JEICompat;
  0.21: buildcraft.compat.module.jei.BCPluginJEI;
  2.05: Other 61 Plugins
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
            text: [194.59,'s'].join(''),
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
993A00   2.73s Loading sounds;
994400   2.78s Loading Resource - SoundHandler;
994F00  24.10s ModelLoader: blocks;
995900   5.78s ModelLoader: items;
996300  20.18s ModelLoader: baking;
996D00  25.86s Indexing ingredients;
444444 113.16s Other
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
