## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
579.14 sec
<br>
<sup><sub>(
9:39 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [368.12]},
      {label: 'FML stuff:', data: [211.02]}
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
3e76ba  26.28s Just Enough Items;
386AA7  24.91s Just Enough Items (Plugins);
386AA7  11.76s Just Enough Items (Ingredient Filter);
a651a8  29.23s IndustrialCraft 2;
9e2174   3.22s Tinkers' Construct;
8E1E68  19.29s Tinkers' Construct (Oredict Melting);
219e2a  20.36s BuildCraft Lib;
3e76ba  14.72s Railcraft;
8f304e  13.78s Astral Sorcery;
516fa8  11.71s Ender IO;
6e3a17  10.68s Quark;
213664  10.04s Forestry;
8c2ccd   9.70s Immersive Engineering;
8f3087   9.40s Forge Mod Loader;
216364   7.19s Thermal Expansion;
8f8630   5.87s GenDustry;
3e8160   5.70s The Twilight Forest;
a86e51   5.00s Extra Utilities 2;
3ebab8   4.58s CoFH World;
3eb2ba   4.54s Botania;
649e21   4.14s OpenBlocks;
814a3e   4.11s RFTools;
cdad2c   3.87s Steve's Carts 2;
444444  57.66s 32 Other mods;
333333  47.84s 109 'Fast' mods (load 1.0s - 0.1s);
222222   2.56s 61 'Instant' mods (load %3C 0.1s)
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
IndustrialCraft 2     |  1.53|  0.03| 25.50|  1.08|  0.00|  1.09|  0.00|  0.00;
Tinkers' Construct    |  1.54|  0.03|  0.40|  0.06|  0.00| 20.48|  0.00|  0.00;
BuildCraft Lib        |  0.06|  0.02|  1.45|  0.15|  0.00| 18.68|  0.00|  0.00;
Railcraft             |  0.33|  0.02| 11.87|  1.86|  0.00|  0.65|  0.00|  0.00;
Astral Sorcery        |  0.44|  0.03| 10.60|  1.82|  0.00|  0.89|  0.00|  0.00;
Ender IO              |  2.79|  0.02|  4.53|  0.66|  3.49|  0.22|  0.00|  0.00;
Quark                 |  0.04|  0.01|  9.68|  0.16|  0.00|  0.79|  0.00|  0.00;
Forestry              |  0.67|  0.02|  7.10|  1.21|  0.01|  1.03|  0.00|  0.00;
Immersive Engineering |  2.09|  0.02|  2.95|  1.24|  0.00|  3.40|  0.00|  0.00;
Thermal Expansion     |  0.14|  0.01|  1.57|  0.14|  0.12|  5.17|  0.01|  0.04;
GenDustry             |  0.05|  0.01|  4.54|  0.13|  0.00|  1.14|  0.00|  0.00;
The Twilight Forest   |  1.71|  0.02|  1.99|  1.94|  0.01|  0.02|  0.00|  0.00
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
  5.69: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  3.99: jeresources.jei.JEIConfig;
  2.76: binnie.extratrees.integration.jei.ExtraTreesJeiPlugin;
  1.98: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  1.57: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  1.57: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.36: mezz.jei.plugins.vanilla.VanillaPlugin;
  1.17: forestry.factory.recipes.jei.FactoryJeiPlugin;
  0.63: ic2.jeiIntegration.SubModule;
  0.62: com.buuz135.industrial.jei.JEICustomPlugin;
  0.60: net.bdew.jeibees.BeesJEIPlugin;
  0.43: com.chocohead.advsolar.gui.JEICompat;
  0.25: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.22: slimeknights.tconstruct.plugin.jei.JEIPlugin;
  0.19: mods.railcraft.common.plugins.jei.RailcraftJEIPlugin;
  1.89: Other 61 Plugins
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
            text: [211.02,'s'].join(''),
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
993A00   4.10s Loading sounds;
994400   4.23s Loading Resource - SoundHandler;
994F00  20.64s ModelLoader: blocks;
995900   5.93s ModelLoader: items;
996300  15.69s ModelLoader: baking;
996D00  11.63s Indexing ingredients;
444444 148.81s Other
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
