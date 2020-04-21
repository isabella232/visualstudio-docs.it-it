---
title: Generare metriche del codice dall'IDE o dalla riga di comando
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649301"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedura: generare dati sulle metriche del codiceHow to: Generate code metrics data

È possibile generare i dati delle metriche del codice in tre modi:You can generate code metrics data in three ways:

- Installando [analizzatori FxCop](#fxcop-analyzers-code-metrics-rules) e abilitando le quattro regole di metrica del codice (manutenibilità) in esso contenute.

- Scegliendo il comando di menu [ **Analizza** > Calcola metriche codice](#calculate-code-metrics-menu-command) all'interno di Visual Studio.

- Dalla [riga](#command-line-code-metrics) di comando per i progetti in C e Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Regole delle metriche del codice degli analizzatori FxCopFxCop analyzers code metrics rules

Il pacchetto FxCopAnalyzers NuGet include diverse regole [dell'analizzatore](roslyn-analyzers-overview.md) delle metriche del [codice:The FxCopAnalyzers NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) includes several code metrics analyzer rules:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Queste regole sono disabilitate per impostazione predefinita, ma è possibile abilitarle da [**Esplora soluzioni**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) o in un file [del set](using-rule-sets-to-group-code-analysis-rules.md) di regole. Ad esempio, per abilitare la regola CA1502 come avviso, il file .ruleset conterrà la seguente voce:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configurazione

È possibile configurare le soglie in corrispondenza delle quali vengono attivate le regole delle metriche del codice nell'analizzatore FxCop.

1. Creare un file di testo. Ad esempio, è possibile denominarlo *CodeMetricsConfig.txt*.

2. Aggiungere le soglie desiderate al file di testo nel seguente formato:

   ```txt
   CA1502: 10
   ```

   In questo esempio, la regola [CA1502](ca1502.md) è configurata per l'incendio quando la complessità ciclomatica di un metodo è maggiore di 10.

3. Nella finestra **Proprietà** di Visual Studio o nel file di progetto contrassegnare l'azione di compilazione del file di configurazione come [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Ad esempio:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Comando di menu Calcola metrico codice

Generare metriche del codice per uno o tutti i progetti aperti nell'IDE utilizzando il menu **Analizza** > **calcola metriche codice.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generare risultati delle metriche del codice per un'intera soluzione

È possibile generare i risultati delle metriche di codice per un'intera soluzione in uno dei modi seguenti:You can generate code metrics results for an entire solution in any of the following ways:

- Dalla barra dei menu scegliere **Analizza** > **calcola metriche** > codice**per soluzione**.

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione, quindi **scegliere Calcola metriche codice**.

- Nella finestra **Risultati metriche codice** scegliere il **pulsante Calcola metriche codice per soluzione.**

I risultati vengono generati e viene visualizzata la finestra **Risultati metrica codice.** Per visualizzare i dettagli dei risultati, espandere l'albero nella colonna **Gerarchia.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generare risultati delle metriche del codice per uno o più progetti

1. In **Esplora soluzioni**selezionare uno o più progetti.

1. Dalla barra dei menu, scegliere **Analizza** > **calcola metriche** > codice**per progetti selezionati.**

I risultati vengono generati e viene visualizzata la finestra **Risultati metrica codice.** Per visualizzare i dettagli dei risultati, espandere la struttura nella **gerarchia**.

::: moniker range="vs-2017"

> [!NOTE]
> Il comando **Calcola metriche codice** non funziona per i progetti .NET Core e .NET Standard. Per calcolare le metriche di codice per un progetto .NET Core o .NET Standard, è possibile:To calculate code metrics for a .NET Core or .NET Standard project, you can:
>
> - Calcolare invece le metriche del codice dalla riga di [comando](#command-line-code-metrics)
>
> - Eseguire l'aggiornamento a [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metriche del codice della riga di comando

È possibile generare i dati della metrica del codice dalla riga di comando per i progetti di C e Visual Basic per le app .NET Framework, .NET Core e .NET Standard. Per eseguire le metriche del codice dalla riga di comando, installare il [pacchetto Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) o compilare manualmente l'eseguibile [Metrics.exe.](#metricsexe)

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacchetto Microsoft.CodeAnalysis.Metrics NuGet

Il modo più semplice per generare dati di metrica del codice dalla riga di comando consiste nell'installare il pacchetto Microsoft.CodeAnalysis.Metrics NuGet.The easiest way to generate code metrics data from the command line is by installing the [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet package. Dopo aver installato il pacchetto, eseguire `msbuild /t:Metrics` dalla directory che contiene il file di progetto. Ad esempio:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

È possibile sostituire il nome `/p:MetricsOutputFile=<filename>`del file di output specificando . È inoltre possibile ottenere dati sulle metriche del codice [di tipo legacy](#previous-versions) specificando `/p:LEGACY_CODE_METRICS_MODE=true`. Ad esempio:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Output delle metriche di codiceCode metrics output

L'output XML generato assume il seguente formato:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Se non si desidera installare il pacchetto NuGet, è possibile generare e utilizzare direttamente l'eseguibile *Metrics.exe.* Per generare l'eseguibile *Metrics.exe:*

1. Clonare il repository [dotnet/roslyn-analyzers.](https://github.com/dotnet/roslyn-analyzers)
2. Aprire il prompt dei comandi per gli sviluppatori per Visual Studio come amministratore.
3. Dalla radice del repository **roslyn-analyzers,** eseguire il comando seguente:`Restore.cmd`
4. Modificare la directory in *src-Tools*.
5. Eseguire il comando seguente per compilare il progetto **Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un eseguibile denominato *Metrics.exe* viene generato nella directory *artifacts.bin* nella radice del repository.

#### <a name="metricsexe-usage"></a>Utilizzo di Metrics.exe

Per eseguire *Metrics.exe*, fornire un progetto o una soluzione e un file XML di output come argomenti. Ad esempio:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modalità legacy

È possibile scegliere di compilare *Metrics.exe* in *modalità legacy.* La versione in modalità legacy dello strumento genera valori metrici più vicini alle [versioni precedenti dello strumento generate.](#previous-versions) Inoltre, in modalità legacy, *Metrics.exe* genera metriche di codice per lo stesso set di tipi di metodo per cui le versioni precedenti dello strumento generavano metriche di codice. Ad esempio, non genera dati di metrica del codice per gli inizializzatori di campo e di proprietà. La modalità legacy è utile per la compatibilità con le versioni precedenti o se si dispone di gate di archiviazione del codice in base ai numeri delle metriche del codice. Il comando per compilare Metrics.exe in modalità legacy è:The command to build *Metrics.exe* in legacy mode is:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Per ulteriori informazioni, consultate [Abilitare la generazione di metriche del codice in modalità legacy.](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Versioni precedenti

::: moniker range=">=vs-2019"
Visual Studio 2015 includeva uno strumento per metriche del codice della riga di comando denominato anche *Metrics.exe*. Questa versione precedente dello strumento ha eseguito un'analisi binaria, ovvero un'analisi basata su assembly. La versione più recente dello strumento *Metrics.exe* analizza invece il codice sorgente. Poiché lo strumento *Metrics.exe* più recente è basato sul codice sorgente, i risultati delle metriche del codice della riga di comando possono essere diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*. A partire da Visual Studio 2019, l'IDE di Visual Studio analizza il codice sorgente come lo strumento della riga di comando e i risultati devono essere gli stessi.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 includeva uno strumento per metriche del codice della riga di comando denominato anche *Metrics.exe*. Questa versione precedente dello strumento ha eseguito un'analisi binaria, ovvero un'analisi basata su assembly. Il nuovo strumento *Metrics.exe* analizza invece il codice sorgente. Poiché il nuovo strumento *Metrics.exe* è basato sul codice sorgente, i risultati delle metriche del codice della riga di comando sono diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*.
::: moniker-end

Il nuovo strumento di metriche del codice della riga di comando calcola le metriche anche in presenza di errori del codice sorgente, purché la soluzione e il progetto possano essere caricati.

#### <a name="metric-value-differences"></a>Differenze di valore metrico

::: moniker range=">=vs-2019"
A partire da Visual Studio 2019 versione 16.4 e Microsoft.CodeAnalysis.Metics (2.9.5) `SourceLines` e `ExecutableLines` sostituire la metrica precedente. `LinesOfCode` Per una descrizione delle nuove metriche, vedere Valori delle [metriche del codice](../code-quality/code-metrics-values.md). La `LinesOfCode` metrica è disponibile in modalità legacy.
::: moniker-end
::: moniker range="vs-2017"
La `LinesOfCode` metrica è più accurata e affidabile nel nuovo strumento di metriche del codice della riga di comando. È indipendente da eventuali differenze di codegen e non cambia quando il set di strumenti o il runtime viene modificato. Il nuovo strumento conta le righe di codice effettive, incluse le righe vuote e i commenti.
::: moniker-end

Altre `CyclomaticComplexity` metriche, `MaintainabilityIndex` ad esempio e utilizzano le stesse formule delle versioni `IOperations` precedenti di *Metrics.exe*, ma il nuovo strumento conta il numero di (istruzioni di origine logica) anziché istruzioni IL (Intermediate Language). I numeri saranno leggermente diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*.

## <a name="see-also"></a>Vedere anche

- [Utilizzare la finestra Risultati metriche codice](../code-quality/working-with-code-metrics-data.md)
- [Valori delle metriche del codice](../code-quality/code-metrics-values.md)
