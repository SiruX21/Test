## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
537.39 sec
<br>
<sup><sub>(
8:57 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [328.86]},
      {label: 'FML stuff:', data: [208.53]}
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
3e76ba  21.30s Just Enough Items;
386AA7  29.88s Just Enough Items (Plugins);
386AA7  35.62s Just Enough Items (Ingredient Filter);
a651a8  22.38s IndustrialCraft 2;
219e2a  20.11s BuildCraft Lib;
9e2174   2.00s Tinkers' Construct;
8E1E68  17.74s Tinkers' Construct (Oredict Melting);
8f304e  11.91s Astral Sorcery;
8f3087  11.79s Forge Mod Loader;
516fa8  10.47s Ender IO;
3e76ba   9.68s Railcraft;
6e3a17   9.33s Quark;
8c2ccd   6.57s Immersive Engineering;
213664   5.78s Forestry;
216364   5.74s Thermal Expansion;
8f8630   4.98s GenDustry;
a86e51   4.67s Extra Utilities 2;
3e8160   4.09s The Twilight Forest;
649e21   3.70s OpenBlocks;
3eb2ba   3.30s Botania;
5161a8   1.17s CraftTweaker2;
495797   1.43s CraftTweaker2 (Script Loading);
575a2c   2.59s BuildCraft Silicon;
814a3e   2.43s RFTools;
444444  33.65s 21 Other mods;
333333  43.81s 108 'Fast' mods (load 1.0s - 0.1s);
222222   2.76s 73 'Instant' mods (load %3C 0.1s)
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
IndustrialCraft 2     |  1.14|  0.02| 19.13|  1.11|  0.00|  0.98|  0.00|  0.00;
BuildCraft Lib        |  0.06|  0.02|  0.86|  0.19|  0.00| 18.99|  0.00|  0.00;
Tinkers' Construct    |  0.94|  0.02|  0.21|  0.04|  0.00| 18.54|  0.00|  0.00;
Astral Sorcery        |  0.33|  0.01|  9.20|  1.65|  0.00|  0.70|  0.00|  0.00;
Ender IO              |  3.42|  0.01|  2.57|  0.64|  3.72|  0.12|  0.00|  0.00;
Railcraft             |  0.20|  0.01|  7.07|  1.81|  0.00|  0.59|  0.00|  0.00;
Quark                 |  0.03|  0.01|  8.78|  0.12|  0.00|  0.38|  0.00|  0.00;
Immersive Engineering |  1.36|  0.01|  1.56|  1.11|  0.00|  2.54|  0.00|  0.00;
Forestry              |  0.44|  0.02|  3.99|  1.10|  0.02|  0.22|  0.00|  0.00;
Thermal Expansion     |  0.11|  0.00|  1.04|  0.14|  0.10|  4.30|  0.01|  0.04;
GenDustry             |  0.03|  0.00|  3.77|  0.15|  0.00|  1.04|  0.00|  0.00;
Extra Utilities 2     |  0.11|  0.01|  4.33|  0.05|  0.00|  0.17|  0.00|  0.00
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
  6.54: com.valkyrieofnight.et.m_plugins.jei.PJEI;
  3.75: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  3.35: jeresources.jei.JEIConfig;
  3.12: binnie.extratrees.integration.jei.ExtraTreesJeiPlugin;
  2.05: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  1.97: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.49: mezz.jei.plugins.vanilla.VanillaPlugin;
  1.47: ic2.jeiIntegration.SubModule;
  1.19: forestry.factory.recipes.jei.FactoryJeiPlugin;
  0.80: com.buuz135.industrial.jei.JEICustomPlugin;
  0.78: net.bdew.jeibees.BeesJEIPlugin;
  0.69: blusunrize.immersiveengineering.common.util.compat.jei.JEIHelper;
  0.36: com.chocohead.advsolar.gui.JEICompat;
  0.29: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.22: slimeknights.tconstruct.plugin.jei.JEIPlugin;
  1.83: Other 61 Plugins
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
            text: [208.53,'s'].join(''),
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
993A00   2.87s Loading sounds;
994400   2.93s Loading Resource - SoundHandler;
994F00  28.21s ModelLoader: blocks;
995900   5.27s ModelLoader: items;
996300  22.53s ModelLoader: baking;
996D00  35.55s Indexing ingredients;
444444 111.16s Other
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
