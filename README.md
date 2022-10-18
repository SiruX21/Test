## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
1026.82 sec
<br>
<sup><sub>(
17:6 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [693.43]},
      {label: 'FML stuff:', data: [333.39]}
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
3e76ba 114.89s Just Enough Items;
386AA7  63.35s Just Enough Items (Plugins);
5161a8  88.11s CraftTweaker2;
495797   2.45s CraftTweaker2 (Script Loading);
214d9e  46.65s Minecraft Forge;
7c813e  42.42s Thaumcraft;
9e2174   2.47s Tinkers' Construct;
8E1E68  38.47s Tinkers' Construct (Oredict Melting);
a651a8  27.55s IndustrialCraft 2;
219e2a  23.01s BuildCraft Lib;
3ebab8  19.76s CoFH World;
8f304e  17.57s Astral Sorcery;
8f3087  14.74s Forge Mod Loader;
8c2ccd  13.03s Immersive Engineering;
516fa8  12.00s Ender IO;
3e76ba  10.81s Railcraft;
6e3a17  10.73s Quark;
216364   9.02s Thermal Expansion;
213664   9.01s Forestry;
5162a8   6.01s Applied Energistics 2;
3e8160   5.48s The Twilight Forest;
8f8630   4.75s GenDustry;
649e21   3.99s OpenBlocks;
444444  64.48s 37 Other mods;
333333  39.69s 99 'Fast' mods (load 1.0s - 0.1s);
222222   3.01s 69 'Instant' mods (load %3C 0.1s)
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
CraftTweaker2         |  0.72|  0.00|  1.22|  0.00|  0.00|  0.39| 88.21|  0.00;
Thaumcraft            |  0.59|  0.02|  0.42|  1.80|  0.01| 39.58|  0.00|  0.00;
Tinkers' Construct    |  1.00|  0.02|  0.20|  0.08|  0.00| 39.65|  0.00|  0.00;
IndustrialCraft 2     |  1.20|  0.03| 21.90|  1.46|  0.00|  2.97|  0.00|  0.00;
BuildCraft Lib        |  0.04|  0.02|  1.26|  0.23|  0.00| 21.46|  0.00|  0.00;
CoFH World            |  0.05|  0.00|  0.28|  0.00|  0.00|  0.00| 19.43|  0.00;
Astral Sorcery        |  0.26|  0.01| 13.91|  2.53|  0.00|  0.86|  0.00|  0.00;
Immersive Engineering |  1.57|  0.02|  1.64|  1.35|  0.00|  8.45|  0.00|  0.00;
Ender IO              |  2.55|  0.02|  2.87|  0.89|  5.25|  0.41|  0.00|  0.00;
Railcraft             |  0.28|  0.02|  7.40|  2.19|  0.00|  0.93|  0.00|  0.00;
Quark                 |  0.02|  0.01|  9.84|  0.24|  0.00|  0.61|  0.00|  0.00;
Thermal Expansion     |  0.10|  0.01|  1.41|  0.19|  0.13|  6.98|  0.02|  0.18
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
 15.84: jeresources.jei.JEIConfig;
 10.54: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  8.77: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  6.49: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  5.56: binnie.extratrees.integration.jei.ExtraTreesJeiPlugin;
  3.10: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  2.66: mezz.jei.plugins.vanilla.VanillaPlugin;
  2.07: ic2.jeiIntegration.SubModule;
  1.55: net.bdew.jeibees.BeesJEIPlugin;
  1.49: com.buuz135.industrial.jei.JEICustomPlugin;
  1.32: forestry.factory.recipes.jei.FactoryJeiPlugin;
  0.76: rustic.compat.jei.RusticJEIPlugin;
  0.33: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.32: slimeknights.tconstruct.plugin.jei.JEIPlugin;
  0.25: mods.railcraft.common.plugins.jei.RailcraftJEIPlugin;
  2.30: Other 67 Plugins
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
            text: [333.39,'s'].join(''),
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
993A00   4.58s Loading sounds;
994400   4.68s Loading Resource - SoundHandler;
994F00  35.25s ModelLoader: blocks;
995900   8.13s ModelLoader: items;
996300  40.00s ModelLoader: baking;
996D00  81.29s Indexing ingredients;
444444 159.45s Other
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
