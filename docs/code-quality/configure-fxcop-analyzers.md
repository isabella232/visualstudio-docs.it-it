---
title: Configurare gli analizzatori di qualità del codice .NET con EditorConfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800736"
---
# <a name="configure-net-code-quality-analyzers"></a>Configurare gli analizzatori di qualità del codice .NET

Per determinati analizzatori di qualità del codice .NET (quelli i cui ID di regola iniziano con `CA` ), è possibile ridefinire le parti della codebase a cui applicare le [Opzioni configurabili](fxcop-analyzer-options.md). Ogni opzione viene specificata aggiungendo una coppia chiave-valore a un file [EditorConfig](https://editorconfig.org) . Un file di configurazione può essere specifico per un file, un progetto, una soluzione o l'intero repository.

> [!TIP]
> Per aggiungere un file con estensione EditorConfig al progetto, fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra **Aggiungi nuovo elemento** immettere **EditorConfig** nella casella di ricerca. Selezionare il modello **file EditorConfig (impostazione predefinita)** e scegliere **Aggiungi**.
>
> ![Aggiungere il file EditorConfig al progetto in Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Per informazioni sulla configurazione della gravità di una regola, ad esempio se si tratta di un errore o di un avviso, vedere [impostare la gravità della regola in un file EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). In alternativa, è possibile scegliere uno dei [file EditorConfig o dei set](analyzer-rule-sets.md) di regole predefiniti per abilitare o disabilitare rapidamente una categoria di regole.

::: moniker-end

Nella parte restante di questo articolo viene illustrata la sintassi generale per le [opzioni che ridefiniscono](fxcop-analyzer-options.md) l'applicazione degli analizzatori di qualità del codice .NET.

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

## <a name="enabling-editorconfig-based-configuration"></a>Abilitazione della configurazione basata su EditorConfig

È possibile abilitare la configurazione dell'analizzatore basato su EditorConfig per gli ambiti seguenti:

- Documenti specifici
- Cartelle specifiche
- Progetto/i specifici
- Soluzioni specifiche
- Intero repository

Per abilitare la configurazione, aggiungere un file con *estensione EditorConfig* con le opzioni nella directory corrispondente. Questo file può contenere anche voci di configurazione della gravità diagnostica basata su EditorConfig. Per altri dettagli, vedere [qui](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>Vedere anche

- [Opzioni dell'ambito delle regole per gli analizzatori di qualità del codice .NET](fxcop-analyzer-options.md)
- [Configurazione analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenzioni di codifica .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
