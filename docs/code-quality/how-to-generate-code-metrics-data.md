---
title: Generare metriche di codice dall'IDE o dalla riga di comando
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f9904c95be45c7f293355340c814faafb5de2b
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568846"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedura: generare dati di metrica del codice

È possibile generare dati di metrica del codice in tre modi:

- Installando gli [analizzatori FxCop](#fxcop-analyzers-code-metrics-rules) e abilitando le quattro regole della metrica del codice (gestibilità) in esso contenute.

- Scegliendo il comando di menu [ **analizza** > **Calcola metriche del codice** ](#calculate-code-metrics-menu-command) in Visual Studio.

- Dalla [riga di comando](#command-line-code-metrics) per C# i progetti e Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Regole metrica del codice degli analizzatori FxCop

Il [pacchetto NuGet FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) include diverse regole dell' [analizzatore](roslyn-analyzers-overview.md) della metrica del codice:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506.md)

Queste regole sono disabilitate per impostazione predefinita, ma è possibile abilitarle da [**Esplora soluzioni**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) o in un file del [set di regole](using-rule-sets-to-group-code-analysis-rules.md) . Ad esempio, per abilitare la regola CA1502 come avviso, il file con estensione ruleset conterrà la voce seguente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configurazione

È possibile configurare le soglie in base alle quali vengono attivate le regole di metrica del codice nel pacchetto degli analizzatori FxCop.

1. Creare un file di testo. Ad esempio, è possibile denominarlo *CodeMetricsConfig. txt*.

2. Aggiungere le soglie desiderate al file di testo nel formato seguente:

   ```txt
   CA1502: 10
   ```

   In questo esempio la regola [CA1502](ca1502.md) è configurata in modo da essere attivata quando la complessità ciclomatica di un metodo è maggiore di 10.

3. Nella finestra **Proprietà** di Visual Studio o nel file di progetto contrassegnare l'azione di compilazione del file di configurazione come [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Ad esempio:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Comando di menu Calcola metrica codice

Generare la metrica del codice per uno o tutti i progetti aperti nell'IDE usando il menu **analizza** > **Calcola metrica del codice** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generare risultati della metrica del codice per un'intera soluzione

È possibile generare risultati della metrica del codice per un'intera soluzione in uno dei modi seguenti:

- Dalla barra dei menu scegliere **analizza** > **Calcola metriche del codice** > **per la soluzione**.

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Calcola metrica codice**.

- Nella finestra **Risultati metrica codice** scegliere il pulsante **Calcola metrica codice per la soluzione** .

I risultati vengono generati e viene visualizzata la finestra **Risultati metrica codice** . Per visualizzare i dettagli dei risultati, espandere l'albero nella colonna **gerarchia** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generare risultati della metrica del codice per uno o più progetti

1. In **Esplora soluzioni**selezionare uno o più progetti.

1. Dalla barra dei menu scegliere **analizza** > **calcolare le metriche del codice** > **per i progetti selezionati**.

I risultati vengono generati e viene visualizzata la finestra **Risultati metrica codice** . Per visualizzare i dettagli dei risultati, espandere l'albero nella **gerarchia**.

::: moniker range="vs-2017"

> [!NOTE]
> Il comando **Calculate Code Metrics** non funziona per i progetti .NET Core e .NET standard. Per calcolare la metrica del codice per un progetto .NET Core o .NET Standard, è possibile:
>
> - Calcolare la metrica del codice dalla [riga di comando](#command-line-code-metrics)
>
> - Eseguire l'aggiornamento a [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metriche del codice della riga di comando

È possibile generare dati di metrica del codice dalla riga di comando C# per i progetti di e Visual Basic per le app .NET Framework, .NET Core e .NET standard. Per eseguire la metrica del codice dalla riga di comando, installare il [pacchetto NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) oppure compilare manualmente il file eseguibile [metrics. exe](#metricsexe) .

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacchetto NuGet Microsoft. CodeAnalysis. Metrics

Il modo più semplice per generare dati di metrica del codice dalla riga di comando consiste nell'installare il pacchetto NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . Dopo aver installato il pacchetto, eseguire `msbuild /t:Metrics` dalla directory che contiene il file di progetto. Ad esempio:

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

È possibile eseguire l'override del nome del file di output specificando `/p:MetricsOutputFile=<filename>`. È anche possibile ottenere dati di metrica del codice di [tipo legacy](#previous-versions) specificando `/p:LEGACY_CODE_METRICS_MODE=true`. Ad esempio:

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

### <a name="code-metrics-output"></a>Output metrica codice

L'output XML generato assume il formato seguente:

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

### <a name="metricsexe"></a>Metrica. exe

Se non si vuole installare il pacchetto NuGet, è possibile generare e usare direttamente il file eseguibile *metrics. exe* . Per generare il file eseguibile *metrica. exe* :

1. Clonare il repository [DotNet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) .
2. Aprire Prompt dei comandi per gli sviluppatori per Visual Studio come amministratore.
3. Dalla radice del repository **Roslyn-Analyzers** , eseguire il comando seguente: `Restore.cmd`
4. Passare alla directory *src\Tools*.
5. Eseguire il comando seguente per compilare il progetto **metrics. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un eseguibile denominato *metrics. exe* viene generato nella directory *artifacts\bin* nella radice del repository.

#### <a name="metricsexe-usage"></a>Utilizzo di Metrics. exe

Per eseguire *metrics. exe*, fornire un progetto o una soluzione e un file XML di output come argomenti. Ad esempio:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modalità legacy

È possibile scegliere di compilare *metrics. exe* in *modalità legacy*. La versione in modalità legacy dello strumento genera valori di metrica che si avvicinano alle [versioni precedenti dello strumento generate](#previous-versions). Inoltre, in modalità legacy, *metrics. exe* genera la metrica del codice per lo stesso set di tipi di metodo per cui le versioni precedenti dello strumento generavano la metrica del codice. Ad esempio, non genera dati di metrica del codice per gli inizializzatori di campo e di proprietà. La modalità legacy è utile per la compatibilità con le versioni precedenti o se sono presenti controlli di archiviazione del codice basati sui numeri di metrica del codice. Il comando per compilare *metrics. exe* in modalità legacy è:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Per altre informazioni, vedere [abilitare la generazione di metriche del codice in modalità legacy](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versioni precedenti

Visual Studio 2015 include uno strumento per la metrica del codice della riga di comando, denominato anche *metrics. exe*. Questa versione precedente dello strumento eseguiva un'analisi binaria, ovvero un'analisi basata su assembly. Il nuovo strumento *metrics. exe* analizza invece il codice sorgente. Poiché il nuovo strumento *metrics. exe* è basato sul codice sorgente, i risultati della metrica del codice della riga di comando sono diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *metrics. exe*.

Il nuovo strumento per la metrica del codice della riga di comando Calcola le metriche anche in presenza di errori del codice sorgente, purché sia possibile caricare la soluzione e il progetto.

#### <a name="metric-value-differences"></a>Differenze valore metrica

Il `LinesOfCode` metrica è più accurato e affidabile nel nuovo strumento per la metrica del codice della riga di comando. È indipendente dalle differenze di codegen e non cambia in caso di modifica del set di strumenti o del runtime. Il nuovo strumento conta le righe di codice effettive, incluse le righe vuote e i commenti.

Altre metriche, ad esempio `CyclomaticComplexity` e `MaintainabilityIndex` utilizzano le stesse formule delle versioni precedenti di *metrics. exe*, ma il nuovo strumento conta il numero di `IOperations` (istruzioni per le origini logiche) anziché le istruzioni del linguaggio intermedio (il). I numeri saranno leggermente diversi rispetto a quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *metrics. exe*.

## <a name="see-also"></a>Vedere anche

- [Usare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)
- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
