---
title: Generare metriche del codice dall'IDE o dalla riga di comando
ms.date: 11/02/2018
description: Informazioni su come generare i dati delle metriche del codice in Visual Studio. Informazioni su come usare Esplora soluzioni, un file del set di regole, la riga di comando o un comando di menu.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 20090419fd73492e60645dc0742505d15da4a21a8fc6811f17611feeb207a565
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392770"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedura: Generare dati delle metriche del codice

È possibile generare i dati delle metriche del codice in tre modi:

- Abilitando [gli analizzatori](#net-code-quality-analyzers-code-metrics-rules) di qualità del codice .NET e abilitando le quattro regole di metrica del codice (manutenibilità) contenute.

- Scegliendo il comando di menu [   >  **Analizza calcola metriche**](#calculate-code-metrics-menu-command) codice all'interno Visual Studio.

- Dalla riga [di comando per](#command-line-code-metrics) C# e Visual Basic progetto.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>Regole delle metriche del codice degli analizzatori di qualità del codice .NET

Gli analizzatori di qualità del codice .NET includono diverse regole [dell'analizzatore delle metriche del](roslyn-analyzers-overview.md) codice:

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

Queste regole sono disabilitate per impostazione predefinita, ma è possibile abilitarle Esplora soluzioni [**in**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) un file [EditorConfig.](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) Ad esempio, per abilitare la regola CA1502 come avviso, il file EditorConfig conterrà la voce seguente:

```cs
dotnet_diagnostic.CA1502.severity = warning
```

### <a name="configuration"></a>Configurazione

È possibile configurare le soglie in base alle quali vengono applicate le regole delle metriche del codice.

1. Creare un file di testo. Ad esempio, è possibile assegnare un nome *CodeMetricsConfig.txt*.

2. Aggiungere le soglie desiderate al file di testo nel formato seguente:

   ```txt
   CA1502: 10
   ```

   In questo esempio la regola [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) è configurata per l'utilizzo quando la complessità di un metodo è maggiore di 10.

3. Nella finestra **Proprietà** di Visual Studio o nel file di progetto contrassegnare l'azione di compilazione del file di configurazione [**come AdditionalFiles**](../ide/build-actions.md#build-action-values). Esempio:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Comando di menu Calcola metriche codice

Generare metriche del codice per uno o tutti i progetti aperti nell'IDE usando il menu **Analizza**  >  **calcola metriche codice.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generare i risultati delle metriche del codice per un'intera soluzione

È possibile generare i risultati delle metriche del codice per un'intera soluzione in uno dei modi seguenti:

- Dalla barra dei menu selezionare **Analizza calcola** metriche  >  **codice per** la  >  **soluzione**.

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione e quindi scegliere **Calcola metriche codice**.

- Nella finestra **Risultati metriche codice** selezionare il pulsante Calcola metriche codice per **la** soluzione.

I risultati vengono generati e viene **visualizzata la** finestra Risultati metriche codice. Per visualizzare i dettagli dei risultati, espandere l'albero nella **colonna Gerarchia** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generare i risultati delle metriche del codice per uno o più progetti

1. In **Esplora soluzioni** selezionare uno o più progetti.

1. Dalla barra dei menu selezionare **Analizza calcola** metriche codice per le Project  >    >  **selezionate.**

I risultati vengono generati e viene **visualizzata la** finestra Risultati metriche codice. Per visualizzare i dettagli dei risultati, espandere l'albero nella **gerarchia**.

::: moniker range="vs-2017"

> [!NOTE]
> Il **comando Calcola metriche codice** non funziona per i progetti .NET Core e .NET Standard codice. Per calcolare le metriche del codice per un progetto .NET Standard .NET Core, è possibile:
>
> - Calcolare invece le metriche del codice [dalla riga di comando](#command-line-code-metrics)
>
> - Eseguire [l'Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metriche del codice della riga di comando

È possibile generare dati sulle metriche del codice dalla riga di comando per i progetti C# e Visual Basic per .NET Framework, .NET Core e .NET Standard applicazioni. Per eseguire metriche del codice dalla riga di comando, installare il pacchetto [microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) o compilare manualmente ilMetrics.exe[file](#metricsexe) eseguibile.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacchetto NuGet Microsoft.CodeAnalysis.Metrics

Il modo più semplice per generare i dati delle metriche del codice dalla riga di comando è installare il pacchetto NuGet [Microsoft.CodeAnalysis.Metrics.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) Dopo aver installato il pacchetto, eseguire `msbuild /t:Metrics` dalla directory che contiene il file di progetto. Esempio:

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

È possibile eseguire l'override del nome del file di output specificando `/p:MetricsOutputFile=<filename>` . È anche possibile ottenere [dati sulle metriche del](#previous-versions) codice di tipo legacy specificando `/p:LEGACY_CODE_METRICS_MODE=true` . Esempio:

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

### <a name="code-metrics-output"></a>Output delle metriche del codice

L'output XML generato ha il formato seguente:

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

Se non si vuole installare il pacchetto NuGet, è possibile  generare e usare direttamente ilMetrics.exeeseguibile. Per generare il file *Metrics.exe* eseguibile:

1. Clonare [il repo dotnet/roslyn-analyzers.](https://github.com/dotnet/roslyn-analyzers)
2. Aprire Prompt dei comandi per gli sviluppatori per Visual Studio come amministratore.
3. Dalla radice del **repo roslyn-analyzers** eseguire il comando seguente: `Restore.cmd`
4. Modificare la directory in *src\Tools\Metrics*.
5. Eseguire il comando seguente per compilare **il progetto Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Nella directory *artifacts\bin* *nella radice delMetrics.exe* viene generato un file eseguibile denominatoMetrics.exe.

#### <a name="metricsexe-usage"></a>Metrics.exe utilizzo

Per eseguire *Metrics.exe*, specificare un progetto o una soluzione e un file XML di output come argomenti. Esempio:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modalità legacy

È possibile scegliere di compilare *Metrics.exe* in *modalità legacy.* La versione in modalità legacy dello strumento genera valori di metrica più vicini a quelli delle [versioni precedenti dello strumento generato.](#previous-versions) Inoltre, in modalità *legacy,* Metrics.exemetriche del codice per lo stesso set di tipi di metodo per cui le versioni precedenti dello strumento generano metriche del codice. Ad esempio, non genera dati delle metriche del codice per gli inizializzatori di campo e proprietà. La modalità legacy è utile per la compatibilità con le versioni precedenti o se si dispone di gate di archiviazione del codice in base ai numeri delle metriche del codice. Il comando per compilare *Metrics.exe* in modalità legacy è:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Per altre informazioni, vedere [Abilitare la generazione di metriche del codice in modalità legacy.](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Versioni precedenti

::: moniker range=">=vs-2019"
Visual Studio 2015 includeva uno strumento di metrica del codice da riga di comando denominato *ancheMetrics.exe*. Questa versione precedente dello strumento ha fatto un'analisi binaria, cio' un'analisi basata su assembly. La versione più recente dello strumento *Metrics.exe* analizza invece il codice sorgente. Poiché lo  strumentoMetrics.exepiù recente è basato sul codice sorgente, i risultati delle metriche del codice della riga di comando possono essere diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*. A partire Visual Studio 2019, l'IDE Visual Studio analizza il codice sorgente come lo strumento da riga di comando e i risultati dovrebbero essere gli stessi.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 includeva uno strumento di metrica del codice da riga di comando denominato *ancheMetrics.exe*. Questa versione precedente dello strumento ha fatto un'analisi binaria, cio' un'analisi basata su assembly. Il nuovo *strumentoMetrics.exe* analizza invece il codice sorgente. Poiché il nuovo *strumentoMetrics.exe* è basato sul codice sorgente, i risultati delle metriche del codice della riga di comando sono diversi da quelli generati dall'IDE di Visual Studio e dalle versioni precedenti di *Metrics.exe*.
::: moniker-end

Il nuovo strumento di metrica del codice della riga di comando calcola le metriche anche in presenza di errori del codice sorgente, purché sia possibile caricare la soluzione e il progetto.

#### <a name="metric-value-differences"></a>Differenze tra i valori delle metriche

::: moniker range=">=vs-2019"
A partire Visual Studio 2019 versione 16.4 e Microsoft.CodeAnalysis.Metics (2.9.5) e sostituire la metrica `SourceLines` `ExecutableLines` `LinesOfCode` precedente. Per le descrizioni delle nuove metriche, vedere [Valori delle metriche del codice.](../code-quality/code-metrics-values.md) La `LinesOfCode` metrica è disponibile in modalità legacy.
::: moniker-end
::: moniker range="vs-2017"
La metrica è più accurata e affidabile nel nuovo strumento di metrica del codice della `LinesOfCode` riga di comando. È indipendente da eventuali differenze di codegen e non cambia quando cambia il set di strumenti o il runtime. Il nuovo strumento conta le righe di codice effettive, incluse righe vuote e commenti.
::: moniker-end

Altre metriche, ad esempio e , usano le stesse formule delle versioni precedenti diMetrics.exe, ma il nuovo strumento conta il numero di istruzioni (istruzioni di origine logica) anziché istruzioni di linguaggio `CyclomaticComplexity` `MaintainabilityIndex` ** `IOperations` intermedio (IL). I numeri saranno leggermente diversi da quelli generati dall'IDE Visual Studio e dalle versioni precedenti *diMetrics.exe*.

## <a name="see-also"></a>Vedi anche

- [Usare la finestra Risultati metriche codice](../code-quality/working-with-code-metrics-data.md)
- [Valori delle metriche del codice](../code-quality/code-metrics-values.md)