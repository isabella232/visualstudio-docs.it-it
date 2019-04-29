---
title: Configurare gli analizzatori FxCop tramite editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816917"
---
# <a name="configure-fxcop-analyzers"></a>Configurare gli analizzatori FxCop

Il [analizzatori FxCop](install-fxcop-analyzers.md) costituite da regole di "FxCop" più importanti da analisi statica del codice, convertito in analizzatori di Roslyn. È possibile configurare gli analizzatori di codice FxCop in due modi:

- Con un [set di regole](#fxcop-analyzer-rule-sets), che consente di abilitare o disabilitare la regola e impostare la gravità di violazioni delle regole singole.

- A partire dalla versione 2.6.3 del [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) del pacchetto NuGet, tramite un' [file con estensione editorconfig](#editorconfig-file). Il [opzioni configurabili](fxcop-analyzer-options.md) consentono perfezionare le parti della codebase per l'analisi.

> [!TIP]
> Per informazioni sulle differenze tra l'analisi statica del codice di FxCop e gli analizzatori FxCop, vedere [analizzatori FxCop domande frequenti su](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Set di regole FxCop analyzer

Un modo per configurare gli analizzatori FxCop consiste nell'usare un file XML *set di regole*. Un set di regole è un raggruppamento di regole di analisi del codice che identificano i problemi di destinazione e specifiche condizioni. Set di regole consentono di abilitare o disabilitare la regola e impostare la gravità di violazioni delle regole singole.

Il pacchetto NuGet di analizzatori FxCop include set di regole predefiniti per le categorie di regole seguenti:

- progettazione
- documentazione
- manutenibilità
- denominazione
- prestazioni
- affidabilità
- sicurity
- utilizzo

Per altre informazioni, vedere [set di regole per gli analizzatori di Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>File con estensione EditorConfig

È possibile configurare le regole dell'analizzatore mediante l'aggiunta di coppie chiave-valore da un [editorconfig](https://editorconfig.org) file. Può essere un file di configurazione [specifiche di un progetto](#per-project-configuration) oppure può essere [condiviso](#shared-configuration) tra due o più progetti.

### <a name="per-project-configuration"></a>Configurazione di base al progetto

Per abilitare la configurazione con estensione editorconfig basata analyzer per un progetto specifico, aggiungere un' *editorconfig* file alla directory radice del progetto.

> [!TIP]
> È possibile aggiungere un file con estensione editorconfig al progetto facendo clic sul progetto in **Esplora soluzioni** e selezionando **Add** > **nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra, immettere **editorconfig** nella casella di ricerca. Selezionare il **(impostazione predefinita) di File editorconfig** modello e scegliere **Add**.
>
> ![Aggiungi elemento editorconfig al progetto in Visual Studio](media/add-editorconfig-file.png)

Attualmente non è disponibile alcun supporto gerarchico per "combinando" con estensione editorconfig di file che esistono nei livelli di directory diversi, ad esempio, il livello di soluzione e progetto.

### <a name="shared-configuration"></a>Configurazione condivisa

È possibile condividere un file con estensione editorconfig per la configurazione dell'analizzatore tra due o più progetti, ma richiede alcuni passaggi aggiuntivi.

1. Salvare il *editorconfig* in un percorso comune.

2. Creare un *props* file con il contenuto seguente:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Aggiungere una riga per il *csproj* oppure *vbproj* file da importare il *props* file creato nel passaggio precedente. Questa riga deve essere posizionata prima tutte le righe che importa l'analizzatore di FxCop *props* file. Ad esempio, se il file con estensione props è denominato *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Ricaricare il progetto.

> [!NOTE]
> Non è possibile configurare le regole FxCop legacy (analisi statica del codice FxCop) usando un file con estensione editorconfig.

## <a name="option-scopes"></a>Ambiti di opzione

Ogni opzione può essere configurata per tutte le regole, per una categoria delle regole (ad esempio Naming o progettazione) o per una regola specifica.

### <a name="all-rules"></a>Tutte le regole

La sintassi per la configurazione di un'opzione per tutte le regole è come segue:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria delle regole

La sintassi per la configurazione di un'opzione per un *categoria* delle regole (ad esempio Naming, progettazione o prestazioni) è il seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regola specifica

La sintassi per la configurazione di un'opzione per una regola specifica è come segue:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Vedere anche

- [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizzatori FxCop](install-fxcop-analyzers.md)
