---
title: Generare la metrica del codice dall'IDE o della riga di comando
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232749"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedura: Generare dati di metrica codice

È possibile generare dati di metrica codice in tre modi:

- Installando [analizzatori FxCop](#fxcop-analyzers-code-metrics-rules) e abilitare le regole di codice di quattro metriche (manutenibilità) contiene.

- Scegliendo il [ **Analyze** > **Calcola metrica codice** ](#calculate-code-metrics-menu-command) comando di menu all'interno di Visual Studio.

- Dal [riga di comando](#command-line-code-metrics) per C# e i progetti Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Regole metriche di codice gli analizzatori FxCop

Il [pacchetto FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) include diverse metriche di codice [analizzatore](roslyn-analyzers-overview.md) regole:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Queste regole sono disabilitate per impostazione predefinita, ma è possibile abilitarle dal [ **Esplora soluzioni** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) o in un [set di regole](using-rule-sets-to-group-code-analysis-rules.md) file. Per abilitare la regola CA1502 come un avviso, ad esempio, il file con estensione ruleset conterrà la voce seguente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configurazione

È possibile configurare le soglie in corrispondenza del quale le regole metriche del codice negli analizzatori FxCop pacchetto incendi.

1. Creare un file di testo. Ad esempio, è possibile denominarlo *CodeMetricsConfig.txt*.

2. Aggiungere le soglie desiderate al file di testo nel formato seguente:

   ```txt
   CA1502: 10
   ```

   In questo esempio di regola [CA1502](ca1502-avoid-excessive-complexity.md) è configurato per essere generato quando la complessità ciclomatica di un metodo è maggiore di 10.

3. Nel **delle proprietà** finestra di Visual Studio o nel file di progetto, contrassegnare l'azione di compilazione del file di configurazione come [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Ad esempio:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calcolare il comando di menu della metrica del codice

Generare la metrica del codice per uno o tutti i progetti aperti nell'IDE usando il **Analyze** > **Calcola metrica codice** menu.

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

::: moniker range="vs-2017"

> [!NOTE]
> Il **Calcola metrica codice** comando non funziona per i progetti .NET Core e .NET Standard. Per calcolare la metrica del codice per un progetto .NET Core o .NET Standard, è possibile:
>
> - Calcola metrica codice dal [riga di comando](#command-line-code-metrics) invece
>
> - Eseguire l'aggiornamento a [2019 di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metrica del codice della riga di comando

È possibile generare dati di metrica codice dalla riga di comando per C# e i progetti di Visual Basic per le app .NET Framework, .NET Core e .NET Standard. Per eseguire la metrica del codice dalla riga di comando, installare il [Microsoft.CodeAnalysis.Metrics mobileengagement](#microsoftcodeanalysismetrics-nuget-package) o compilare il [Metrics.exe](#metricsexe) eseguibile se stessi.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacchetto Microsoft.CodeAnalysis.Metrics NuGet

Il modo più semplice per generare dati di metrica codice dalla riga di comando consiste nell'installazione di [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) pacchetto NuGet. Dopo aver installato il pacchetto, eseguire `msbuild /t:Metrics` dalla directory che contiene il file di progetto. Ad esempio:

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

È possibile sostituire il nome del file di output specificando `/p:MetricsOutputFile=<filename>`. È anche possibile ottenere [stile legacy](#previous-versions) dei dati di metrica di codice specificando `/p:LEGACY_CODE_METRICS_MODE=true`. Ad esempio:

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

### <a name="code-metrics-output"></a>Output di metrica codice

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

### <a name="metricsexe"></a>Metrics.exe

Se non si desidera installare il pacchetto NuGet, è possibile generare e usare la *Metrics.exe* eseguibile direttamente. Per generare il *Metrics.exe* eseguibile:

1. Clona il [dotnet/roslyn-analizzatori](https://github.com/dotnet/roslyn-analyzers) repository.
2. Come amministratore, aprire il prompt dei comandi per gli sviluppatori per Visual Studio.
3. Dalla radice del **analizzatori di roslyn** repo, eseguire il comando seguente: `Restore.cmd`
4. Passare alla directory *src\Tools*.
5. Eseguire il comando seguente per compilare il **Metrics.csproj** progetto:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un eseguibile denominato *Metrics.exe* viene generato nel *artifacts\bin* directory sotto la radice del repository.

#### <a name="metricsexe-usage"></a>Utilizzo di Metrics.exe

Per eseguire *Metrics.exe*, fornire un progetto o file di soluzione e un output XML come argomenti. Ad esempio:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modalità legacy

È possibile scegliere di compilare *Metrics.exe* nelle *modalità legacy*. La versione in modalità legacy dello strumento genera i valori delle metriche che più si avvicinano a quelle [le versioni precedenti dello strumento generato](#previous-versions). Inoltre, in modalità legacy *Metrics.exe* genera la metrica del codice per lo stesso set di metodo che le versioni precedenti della metrica del codice generato dallo strumento per i tipi. Ad esempio, non genera dati di metrica codice per gli inizializzatori di campo e proprietà. Modalità legacy è utile per le versioni precedenti compatibilità o se si dispone di controlli check-in di codice basato su metrica del codice numeri. Il comando per compilare *Metrics.exe* in modalità legacy è:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Per altre informazioni, vedere [abilita la generazione di metrica del codice in modalità legacy](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versioni precedenti

Visual Studio 2015 include uno strumento di metriche di codice della riga di comando che è stato chiamato anche *Metrics.exe*. Questa versione precedente dello strumento ha eseguito un'analisi binaria, vale a dire, un'analisi basata su assembly. Il nuovo *Metrics.exe* strumento analizza il codice sorgente invece. Poiché il nuovo *Metrics.exe* lo strumento è la metrica del codice basata su codice, della riga di comando di origine i risultati sono diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*.

Il nuovo strumento di metriche di codice della riga di comando Calcola metriche anche in presenza di errori del codice sorgente, purché la soluzione e progetto può essere caricati.

#### <a name="metric-value-differences"></a>Differenze di valore della metrica

Il `LinesOfCode` metrica è più accurate e affidabili nel nuovo strumento di metriche di codice della riga di comando. È indipendente da eventuali differenze codegen e non cambia quando il runtime o un set di strumenti di modifica. Il nuovo strumento conta le righe effettive di codice, inclusi i commenti e le righe vuote.

Altre metriche, ad esempio `CyclomaticComplexity` e `MaintainabilityIndex` utilizzare le stesse formule come le versioni precedenti di *Metrics.exe*, ma il nuovo strumento conta il numero di `IOperations` (istruzioni di origine logica) anziché intermedio istruzioni in linguaggio (IL). I numeri sarà leggermente diversi rispetto a quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*.

## <a name="see-also"></a>Vedere anche

- [Utilizzare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)
- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
