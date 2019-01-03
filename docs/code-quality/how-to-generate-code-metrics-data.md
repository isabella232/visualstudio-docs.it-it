---
title: Generare la metrica del codice dall'IDE o della riga di comando
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96b74421d638a99823399a0049b712bc6c54c8a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849058"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedura: Generare dati di metrica codice

È possibile generare risultati metrica codice per uno o più progetti o un'intera soluzione. Metrica del codice è disponibile all'interno dell'ambiente di sviluppo interattivo (IDE) di Visual Studio e, per C# e i progetti Visual Basic, nella riga di comando.

Inoltre, è possibile installare un [mobileengagement](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) che include la metrica del codice di quattro [analizzatore](roslyn-analyzers-overview.md) regole: CA1501 CA1502, CA1505 e CA1506. Queste regole sono disabilitate per impostazione predefinita, ma è possibile abilitarle dal **Esplora soluzioni** o in un [set di regole](using-rule-sets-to-group-code-analysis-rules.md) file.

## <a name="visual-studio-ide-code-metrics"></a>Metrica del codice di Visual Studio IDE

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Genera risultati metrica codice per un'intera soluzione

È possibile generare risultati metrica codice per un'intera soluzione in uno dei modi seguenti:

- Dalla barra dei menu, scegliere **Analyze** > **Calcola metrica codice** > **per la soluzione**.

- Nelle **Esplora soluzioni**, fare doppio clic la soluzione e quindi scegliere **Calcola metrica codice**.

- Nel **risultati metrica codice** finestra, scegliere il **calcola metriche codice per la soluzione** pulsante.

I risultati vengono generati e il **risultati metrica codice** viene visualizzata la finestra. Per visualizzare i dettagli dei risultati, espandere l'albero nel **gerarchia** colonna.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Genera risultati metrica codice per uno o più progetti

1. Nelle **Esplora soluzioni**, selezionare uno o più progetti.

1. Dalla barra dei menu, scegliere **Analyze** > **Calcola metrica codice** > **per i progetti selezionati**.

I risultati vengono generati e il **risultati metrica codice** viene visualizzata la finestra. Per visualizzare i dettagli dei risultati, espandere l'albero nel **gerarchia**.

## <a name="command-line-code-metrics"></a>Metrica del codice della riga di comando

È possibile generare dati di metrica codice dalla riga di comando per C# e i progetti di Visual Basic per le app .NET Framework, .NET Core e .NET Standard. Gli strumenti da riga di comando codice metriche viene chiamato *Metrics.exe*.

Per ottenere il *Metrics.exe* eseguibile, è necessario [generarlo manualmente](#generate-the-executable). Nel prossimo futuro, una [versione pubblicata del *Metrics.exe* saranno disponibili](https://github.com/dotnet/roslyn-analyzers/issues/1756) in modo che non è necessario crearlo manualmente.

### <a name="generate-the-executable"></a>Generare il file eseguibile

Per generare il file eseguibile *Metrics.exe*, seguire questa procedura:

1. Clona il [dotnet/roslyn-analizzatori](https://github.com/dotnet/roslyn-analyzers) repository.
2. Come amministratore, aprire il prompt dei comandi per gli sviluppatori per Visual Studio.
3. Dalla radice del **analizzatori di roslyn** repo, eseguire il comando seguente: `Restore.cmd`
4. Passare alla directory *src\Tools*.
5. Eseguire il comando seguente per compilare il **Metrics.csproj** progetto:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un eseguibile denominato *Metrics.exe* viene generato nel *artifacts\bin* directory sotto la radice del repository.

   > [!TIP]
   > Per compilare *Metrics.exe* nelle [modalità legacy](#legacy-mode), eseguire il comando seguente:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Utilizzo

Per eseguire *Metrics.exe*, fornire un progetto o file di soluzione e un output XML come argomenti. Ad esempio:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Output

L'output XML generato viene espresso nel formato seguente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="tool-differences"></a>Differenze dello strumento

Le versioni precedenti di Visual Studio, tra cui Visual Studio 2015, includevano uno strumento di metriche di codice della riga di comando denominato *Metrics.exe*. Questa versione precedente dello strumento ha eseguito un'analisi binaria, vale a dire, un'analisi basata su assembly. Il nuovo strumento analizza il codice sorgente invece. Poiché il nuovo *Metrics.exe* è origine basata su codice, i risultati sono diversi da quello generato dalle versioni precedenti di *Metrics.exe* e IDE di Visual Studio 2017.

Il nuovo *Metrics.exe* strumento può calcolare le metriche anche in presenza di errori del codice sorgente, purché la soluzione e progetto può essere caricati.

#### <a name="metric-value-differences"></a>Differenze di valore della metrica

Il `LinesOfCode` metrica è più accurato e affidabile nelle nuove *Metrics.exe*. È indipendente da eventuali differenze codegen e non cambia quando il runtime o un set di strumenti di modifica. Il nuovo *Metrics.exe* conta le righe effettive di codice, tra cui le righe vuote e i commenti.

Altre metriche, ad esempio `CyclomaticComplexity` e `MaintainabilityIndex` utilizzare le stesse formule come le versioni precedenti di *Metrics.exe*, ma la nuova *Metrics.exe* conta il numero di `IOperations` (logico istruzioni di origine) anziché le istruzioni in linguaggio intermedio (IL). I numeri sarà leggermente diversi rispetto alle versioni precedenti di *Metrics.exe* e dai risultati metrica codice dell'IDE di Visual Studio 2017.

### <a name="legacy-mode"></a>Modalità legacy

È anche possibile scegliere di compilare *Metrics.exe* nelle *modalità legacy*. La versione in modalità legacy dello strumento genera i valori delle metriche per le versioni precedenti dello strumento generato più vicini. Inoltre, in modalità legacy *Metrics.exe* genera la metrica del codice per lo stesso set di metodo che le versioni precedenti della metrica del codice generato dallo strumento per i tipi. Ad esempio, non genera dati di metrica codice per gli inizializzatori di campo e proprietà. Modalità legacy è utile per le versioni precedenti compatibilità o se si dispone di controlli check-in di codice basato su metrica del codice numeri. Il comando per compilare *Metrics.exe* in modalità legacy è:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Per altre informazioni, vedere [abilita la generazione di metrica del codice in modalità legacy](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Vedere anche

- [Utilizzare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)
- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
