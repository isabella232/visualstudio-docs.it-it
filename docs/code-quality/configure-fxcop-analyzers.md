---
title: Configurare gli analizzatori FxCop usando EditorConfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 62dd64dfe4e801f91731b1ed569e3a809156d0d1
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172796"
---
# <a name="configure-fxcop-analyzers"></a>Configurare gli analizzatori FxCop

Il [pacchetto degli analizzatori FxCop](install-fxcop-analyzers.md) è costituito dalle regole "FxCop" più importanti dell'analisi legacy convertite in analizzatori di codice basati su .NET Compiler Platform. Per alcune regole FxCop, è possibile ridefinire le parti della codebase a cui devono essere applicate tramite [Opzioni configurabili](fxcop-analyzer-options.md). Ogni opzione viene specificata aggiungendo una coppia chiave-valore a un file [EditorConfig](https://editorconfig.org) . Un file di configurazione può essere [specifico di un progetto](#per-project-configuration) oppure può essere [condiviso](#shared-configuration) tra due o più progetti.

> [!TIP]
> Aggiungere un file con estensione EditorConfig al progetto facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando **Aggiungi** > **nuovo elemento**. Nella finestra **Aggiungi nuovo elemento** immettere **EditorConfig** nella casella di ricerca. Selezionare il modello **file EditorConfig (impostazione predefinita)** e scegliere **Aggiungi**.
>
> ![Aggiungere il file EditorConfig al progetto in Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Per informazioni sulla configurazione della gravità di una regola, ad esempio se si tratta di un errore o di un avviso, vedere [impostare la gravità della regola in un file EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). In alternativa, è possibile scegliere uno dei [file EditorConfig o dei set](analyzer-rule-sets.md) di regole predefiniti per abilitare o disabilitare rapidamente una categoria di regole.

::: moniker-end

Nella parte restante di questo articolo viene illustrata la sintassi generale per le [opzioni che ridefiniscono](fxcop-analyzer-options.md) la posizione in cui vengono applicate le regole FxCop.

> [!NOTE]
> Non è possibile configurare le regole FxCop legacy usando un file EditorConfig. Per informazioni sulle differenze tra analisi legacy e analizzatori FxCop, vedere [domande frequenti sugli analizzatori di FxCop](fxcop-analyzers-faq.md).

## <a name="option-scopes"></a>Ambiti delle opzioni

Ogni opzione di ridefinizione può essere configurata per tutte le regole, per una categoria di regole (ad esempio, denominazione o progettazione) o per una regola specifica.

### <a name="all-rules"></a>Tutte le regole

La sintassi per la configurazione di un'opzione per *tutte* le regole è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria di regole

La sintassi per la configurazione di un'opzione per una *categoria* di regole, ad esempio denominazione, progettazione o prestazioni, è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regola specifica

La sintassi per la configurazione di un'opzione per una regola *specifica* è la seguente:

|Sintassi|Esempio|
|-|-|
| dotnet_code_quality. RuleId. optionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Configurazione per progetto

Per abilitare la configurazione dell'analizzatore basato su EditorConfig per un progetto specifico, aggiungere un file con *estensione EditorConfig* alla directory radice del progetto.

Attualmente non è disponibile alcun supporto gerarchico per i file con estensione EditorConfig che si trovano a livelli di directory diversi, ad esempio il livello di soluzione e di progetto.

## <a name="shared-configuration"></a>Configurazione condivisa

È possibile condividere un file con estensione EditorConfig per la configurazione dell'analizzatore FxCop tra due o più progetti, ma sono necessari alcuni passaggi aggiuntivi.

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
> Il percorso condiviso arbitrario del file EditorConfig descritto di seguito si applica solo alla configurazione dell'ambito di determinate regole dell'analizzatore FxCop. Per altre impostazioni, ad esempio la gravità della regola, le impostazioni generali dell'editor e lo stile del codice, il file EditorConfig deve sempre essere inserito nella cartella del progetto o in una cartella padre.

## <a name="see-also"></a>Vedere anche

- [Opzioni dell'ambito della regola per gli analizzatori FxCop](fxcop-analyzer-options.md)
- [Configurazione analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizzatori FxCop](install-fxcop-analyzers.md)
- [Convenzioni di codifica .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
