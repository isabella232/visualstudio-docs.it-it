---
title: Configurare gli analizzatori FxCop usando EditorConfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0152ae9f76ea1318f717c41a70d3d46351c9021a
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300617"
---
# <a name="configure-fxcop-analyzers"></a>Configurare gli analizzatori FxCop

Gli [analizzatori FxCop](install-fxcop-analyzers.md) sono costituiti dalle regole "FxCop" più importanti dall'analisi statica del codice, convertite in analizzatori Roslyn. È possibile configurare gli analizzatori di codice FxCop in due modi:

- Con un [set di regole](#fxcop-analyzer-rule-sets), che consente di abilitare o disabilitare la regola e impostare la gravità per le singole violazioni delle regole.

- A partire dalla versione 2.6.3 del pacchetto NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) , tramite un [file con estensione EditorConfig](#editorconfig-file). Le [Opzioni](fxcop-analyzer-options.md) configurabili consentono di perfezionare le parti della codebase da analizzare.

> [!TIP]
> Per informazioni sulle differenze tra l'analisi del codice statica FxCop e gli analizzatori FxCop, vedere [domande frequenti](fxcop-analyzers-faq.md)sugli analizzatori di FxCop.

## <a name="fxcop-analyzer-rule-sets"></a>Set di regole dell'analizzatore FxCop

Un modo per configurare gli analizzatori FxCop consiste nell'utilizzare un *set di regole*XML. Un set di regole è un raggruppamento di regole di analisi del codice che identificano i problemi di destinazione e le condizioni specifiche. I set di regole consentono di abilitare o disabilitare la regola e impostare la gravità per le singole violazioni delle regole.

Il pacchetto NuGet dell'analizzatore FxCop include set di regole predefiniti per le categorie di regole seguenti:

- progettazione
- documentazione
- manutenibilità
- denominazione
- prestazioni
- affidabilità
- sicurity
- utilizzo

Per altre informazioni, vedere [set di regole per gli analizzatori Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>File EditorConfig

È possibile configurare le regole dell'analizzatore aggiungendo coppie chiave-valore a un file con [estensione EditorConfig](https://editorconfig.org) . Un file di configurazione può essere [specifico di un progetto](#per-project-configuration) oppure può essere [condiviso](#shared-configuration) tra due o più progetti.

### <a name="per-project-configuration"></a>Configurazione per progetto

Per abilitare la configurazione dell'analizzatore basato su EditorConfig per un progetto specifico, aggiungere un file con *estensione EditorConfig* alla directory radice del progetto.

> [!TIP]
> È possibile aggiungere un file con estensione EditorConfig al progetto facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliendo **Aggiungi** > **nuovo elemento**. Nella finestra **Aggiungi nuovo elemento** immettere **EditorConfig** nella casella di ricerca. Selezionare il modello **file EditorConfig (impostazione predefinita)** e scegliere **Aggiungi**.
>
> ![Aggiungere un elemento EditorConfig al progetto in Visual Studio](media/add-editorconfig-file.png)

Attualmente non è disponibile alcun supporto gerarchico per i file con estensione EditorConfig che si trovano a livelli di directory diversi, ad esempio il livello di soluzione e di progetto.

### <a name="shared-configuration"></a>Configurazione condivisa

È possibile condividere un file con estensione EditorConfig per la configurazione dell'analizzatore tra due o più progetti, ma sono necessari alcuni passaggi aggiuntivi.

1. Salvare il file con *estensione EditorConfig* in un percorso comune.

2. Creare un file con *estensione Props* con il contenuto seguente:

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

3. Aggiungere una riga al file con estensione *csproj* o *VBPROJ* per importare il file con *estensione Props* creato nel passaggio precedente. Questa riga deve essere posizionata prima di tutte le righe che importano i file di FxCop Analyzer *. props* . Ad esempio, se il file. props è denominato *EditorConfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Ricaricare il progetto.

> [!NOTE]
> Non è possibile configurare le regole FxCop legacy (FxCop codice statico) utilizzando un file con estensione EditorConfig.

## <a name="option-scopes"></a>Ambiti delle opzioni

Ogni opzione può essere configurata per tutte le regole, per una categoria di regole (ad esempio, denominazione o progettazione) o per una regola specifica.

### <a name="all-rules"></a>Tutte le regole

La sintassi per la configurazione di un'opzione per tutte le regole è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria di regole

La sintassi per la configurazione di un'opzione per una *categoria* di regole, ad esempio denominazione, progettazione o prestazioni, è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regola specifica

La sintassi per la configurazione di un'opzione per una regola specifica è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. RuleId. optionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Vedere anche

- [Configurazione analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizzatori FxCop](install-fxcop-analyzers.md)
- [Convenzioni di codifica .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
