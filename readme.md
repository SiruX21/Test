## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
874.50 sec
<br>
<sup><sub>(
14:34 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [712.78]},
      {label: 'FML stuff:', data: [161.72]}
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
214d9e 134.75s Minecraft Forge;
3e76ba  89.96s Just Enough Items;
386AA7  21.73s Just Enough Items (Plugins);
5161a8  72.97s CraftTweaker2;
495797   1.84s CraftTweaker2 (Script Loading);
9e2174   5.13s Tinkers' Construct;
8E1E68  44.37s Tinkers' Construct (Oredict Melting);
7c813e  29.91s Thaumcraft;
219e2a  22.88s BuildCraft Lib;
649e21  18.08s OpenBlocks;
8f3087  17.68s Forge Mod Loader;
516fa8  15.93s Ender IO;
8c2ccd  15.57s Immersive Engineering;
3eb6ba  12.77s Chisels & Bits;
5162a8  11.51s Applied Energistics 2;
814a3e   9.18s RFTools;
2c365a   9.12s Chance Cubes;
436e17   8.01s Integrated Dynamics;
ba3eb8   6.95s Cyclic;
3eb2ba   6.94s Botania;
a86e51   6.58s Extra Utilities 2;
ba3e93   5.34s Tesla Core Lib;
216364   4.92s Thermal Expansion;
444444  89.98s 49 Other mods;
333333  47.43s 120 'Fast' mods (load 1.0s - 0.1s);
222222   3.26s 68 'Instant' mods (load %3C 0.1s)
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
CraftTweaker2         |  1.34|  0.01|  2.81|  0.00|  0.00|  0.97| 69.68|  0.00;
Tinkers' Construct    |  2.55|  0.03|  0.45|  0.05|  0.00| 46.42|  0.00|  0.01;
Thaumcraft            |  1.22|  0.02|  0.72|  0.68|  0.01| 27.25|  0.00|  0.00;
BuildCraft Lib        |  0.35|  0.04|  2.14|  0.17|  0.00| 20.19|  0.00|  0.00;
OpenBlocks            |  0.61|  0.04| 17.17|  0.11|  0.00|  0.15|  0.00|  0.00;
Ender IO              |  4.41|  0.03|  4.99|  1.04|  4.92|  0.54|  0.00|  0.00;
Immersive Engineering |  2.90|  0.03|  4.18|  1.23|  0.00|  7.21|  0.00|  0.01;
Chisels & Bits        |  0.13|  0.00|  0.48|  0.08|  0.05|  0.09|  0.00| 11.94;
Applied Energistics 2 |  0.52|  0.04|  8.73|  0.36|  0.18|  1.69|  0.00|  0.00;
RFTools               |  0.08|  0.01|  3.78|  5.26|  0.01|  0.03|  0.00|  0.00;
Chance Cubes          |  0.09|  0.00|  4.43|  0.01|  0.00|  4.59|  0.00|  0.00;
Integrated Dynamics   |  0.48|  0.06|  7.35|  0.12|  0.00|  0.00|  0.00|  0.00
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
  4.96: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  3.27: com.buuz135.industrial.jei.JEICustomPlugin;
  2.19: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  2.13: jeresources.jei.JEIConfig;
  1.99: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.97: mezz.jei.plugins.vanilla.VanillaPlugin;
  1.37: com.buuz135.thaumicjei.ThaumcraftJEIPlugin;
  0.50: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  0.47: codechicken.microblock.jei.MicroblockJEIPlugin;
  0.28: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.24: slimeknights.tconstruct.plugin.jei.JEIPlugin;
  0.21: exnihilocreatio.compatibility.jei.CompatJEI;
  0.19: blusunrize.immersiveengineering.common.util.compat.jei.JEIHelper;
  0.16: com.brandon3055.draconicevolution.integration.jei.DEJEIPlugin;
  0.15: com.gendeathrow.hatchery.core.jei.JEIPllugin;
  1.67: Other 63 Plugins
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
            text: [161.72,'s'].join(''),
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
993A00   4.47s Loading sounds;
994400   4.58s Loading Resource - SoundHandler;
994F00  36.01s ModelLoader: blocks;
995900   8.28s ModelLoader: items;
996300  28.13s ModelLoader: baking;
996D00  63.78s Indexing ingredients;
444444  16.46s Other
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
