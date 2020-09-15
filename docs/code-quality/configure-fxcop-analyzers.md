---
title: Configurare gli analizzatori di qualità del codice .NET con EditorConfig
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4016699e6329bf6b1755b49cae0986770699fabe
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560762"
---
# <a name="configure-net-code-quality-analyzers-with-editorconfig"></a>Configurare gli analizzatori di qualità del codice .NET con EditorConfig

A partire da .NET 5,0, gli analizzatori di qualità del codice ([ `CAxxxx` regole](code-analysis-for-managed-code-warnings.md)) sono inclusi in [.NET SDK](/dotnet/fundamentals/productivity/code-analysis.md/#code-quality-analysis). Ogni analizzatore della qualità del codice può essere ridefinito per essere applicato alle parti della codebase tramite opzioni configurabili. Ogni opzione viene specificata aggiungendo una coppia chiave-valore a un file [EditorConfig](https://editorconfig.org) . Un file di configurazione può essere specifico per un file, un progetto, una soluzione o l'intero repository.

> [!TIP]
> Per aggiungere un file con estensione EditorConfig al progetto, fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra **Aggiungi nuovo elemento** immettere **EditorConfig** nella casella di ricerca. Selezionare il modello **file EditorConfig (impostazione predefinita)** e scegliere **Aggiungi**.
>
> ![Aggiungere il file EditorConfig al progetto in Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Per informazioni sulla configurazione della gravità di una regola, ad esempio se si tratta di un errore o di un avviso, vedere [impostare la gravità della regola in un file EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). In alternativa, è possibile scegliere uno dei [file EditorConfig o dei set](analyzer-rule-sets.md) di regole predefiniti per abilitare o disabilitare rapidamente una categoria di regole.

::: moniker-end

Nella parte restante di questo articolo viene illustrata la sintassi generale per le opzioni che ridefiniscono l'applicazione degli analizzatori di qualità del codice .NET.

## <a name="option-scopes"></a>Ambiti delle opzioni

Ogni opzione di ridefinizione può essere configurata per tutte le regole, per una categoria di regole (ad esempio, sicurezza o progettazione) o per una regola specifica.

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

## <a name="options-for-net-code-quality-analyzers"></a>Opzioni per gli analizzatori di qualità del codice .NET

È possibile specificare le opzioni in un [file EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project). Ad esempio, è possibile specificare le opzioni seguenti.

> [!TIP]
> Per visualizzare l'elenco completo delle opzioni disponibili, vedere il [file Configuration.MD dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Di seguito è riportato un esempio di come è documentata un'opzione nel file *Configuration.MD dell'analizzatore* :
>
> Nome dell'opzione: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valori delle opzioni: valori integrali \
> Valore predefinito: specifico per ogni regola configurabile (' 100000' per impostazione predefinita per la maggior parte delle regole) \
> Esempio: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

### <a name="api_surface"></a>api_surface

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Parte della superficie dell'API da analizzare | `public`<br/>`internal` o `friend`<br/>`private`<br/>`all`<br/><br/>Separa più valori con una virgola (,) | `public` | [CA1000](ca1000.md) [Ca1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) , [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801 CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se ignorare i metodi asincroni che non restituiscono un valore | `true`<br/>`false` | `false` | [Ca2007](ca2007.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `skip_async_void_methods` .

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se escludere i [parametri di tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) carattere singolo dalla regola, ad esempio `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `allow_single_letter_type_parameters` .

### <a name="output_kind"></a>output_kind

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Specifica che il codice in un progetto che genera questo tipo di assembly deve essere analizzato | Uno o più campi dell' <xref:Microsoft.CodeAnalysis.OutputKind> enumerazione<br/><br/>Separa più valori con una virgola (,) | Tutti i tipi di output | [Ca2007](ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Specifica i modificatori obbligatori per le API da analizzare | Uno o più valori della tabella dei modificatori consentiti seguente<br/><br/>Separa più valori con una virgola (,) | Dipende da ogni regola | [CA1802](ca1802.md) |

| Modificatore consentito | Riepilogo |
| --- | --- |
| `none` | Nessun requisito modificatore |
| `static` o `Shared` | Deve essere dichiarato come "static" ("Shared" in Visual Basic) |
| `const` | Deve essere dichiarato come ' const ' |
| `readonly` | Deve essere dichiarato come ' ReadOnly ' |
| `abstract` | Deve essere dichiarato come ' abstract ' |
| `virtual` | Deve essere dichiarato come ' Virtual ' |
| `override` | Deve essere dichiarato come ' override ' |
| `sealed` | Deve essere dichiarato come ' sealed ' |
| `extern` | Deve essere dichiarato come ' extern ' |
| `async` | Deve essere dichiarato come ' async ' |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se ignorare l'analisi per il `this` parametro dei metodi di estensione | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| I nomi dei metodi di convalida del controllo null che convalidano gli argomenti passati al metodo sono non null | Formati dei nomi di metodo consentiti (separati da `|` ):<br/> -Solo nome metodo (include tutti i metodi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `M:` prefisso facoltativo | nessuno | [CA1062](ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei metodi di formattazione delle stringhe aggiuntivi | Formati dei nomi di metodo consentiti (separati da `|` ):<br/> -Solo nome metodo (include tutti i metodi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `M:` prefisso facoltativo | nessuno | [CA2241](ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei tipi, in modo che il tipo e tutti i relativi tipi derivati siano esclusi per l'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome del tipo (include tutti i tipi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `T:` prefisso facoltativo | nessuno | [CA1303](ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei simboli esclusi per l'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome simbolo (include tutti i simboli con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel [formato ID documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo. Ogni nome di simbolo richiede un prefisso di tipo simbolo, ad esempio il prefisso "M:" per i metodi, il prefisso "T:" per i tipi, il prefisso "N:" per gli spazi dei nomi e così via.<br/> - `.ctor` per costruttori e `.cctor` per costruttori statici | nessuno | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) CA, [caCA2302](ca2302.md) [CA2301](ca2301.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [ca3003](ca3003.md) [ca3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi di simboli non consentiti nel contesto dell'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome simbolo (include tutti i simboli con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel [formato ID documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo. Ogni nome di simbolo richiede un prefisso di tipo simbolo, ad esempio il prefisso "M:" per i metodi, il prefisso "T:" per i tipi, il prefisso "N:" per gli spazi dei nomi e così via.<br/> - `.ctor` per costruttori e `.cctor` per costruttori statici | nessuno | [CA1031](ca1031.md) |

## <a name="enable-a-category-of-rules"></a>Abilitare una categoria di regole

I pacchetti dell'analizzatore possono includere file di [set di regole](using-rule-sets-to-group-code-analysis-rules.md) e/o [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) predefiniti che consentono di abilitare in modo semplice e rapido una categoria di regole, ad esempio regole di sicurezza o di progettazione. Il pacchetto [Microsoft. CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet Analyzer include sia i file EditorConfig che i set di regole. Abilitando una categoria specifica di regole, è possibile identificare i problemi di destinazione e le condizioni specifiche.

> [!NOTE]
> L'abilitazione delle regole dell'analizzatore e l'impostazione della loro gravità usando un file EditorConfig sono supportate a partire da Visual Studio 2019 versione 16,3.

Il pacchetto NuGet NetAnalyzers include i set di regole e i file EditorConfig predefiniti per le categorie di regole seguenti:

- Tutte le regole
- Flusso di dati
- Progettazione
- Documentazione
- Globalizzazione
- Interoperabilità
- Facilità di gestione
- Denominazione
- Prestazioni
- Portata da FxCop
- Affidabilità
- Sicurezza
- Utilizzo

Ognuna di queste categorie di regole ha un file EditorConfig o set di regole per:

- Abilitare tutte le regole nella categoria (e disabilitare tutte le altre regole)
- Usa la gravità predefinita di ogni regola e abilitata per impostazione predefinita (e Disabilita tutte le altre regole)

> [!TIP]
> La categoria "tutte le regole" include un file EditorConfig o set di regole aggiuntivo per disabilitare tutte le regole. Utilizzare questo file per eliminare rapidamente eventuali avvisi o errori dell'analizzatore in un progetto.

> [!TIP]
> Se si esegue la migrazione da un'analisi "FxCop" legacy a un'analisi del codice basata su .NET Compiler Platform, i file EditorConfig e set di regole consentono di continuare a usare configurazioni di regole simili a [quelle usate in precedenza](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>File EditorConfig predefiniti

I file EditorConfig predefiniti per il pacchetto Microsoft. CodeAnalysis. NetAnalyzers Analyzer si trovano nella directory *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* . Ad esempio, il file EditorConfig per abilitare tutte le regole di sicurezza si trova in *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copiare il file con estensione EditorConfig scelto nella directory radice del progetto.

## <a name="predefined-rule-sets"></a>Set di regole predefiniti

I file del set di regole predefiniti per il pacchetto Microsoft. CodeAnalysis. NetAnalyzers Analyzer si trovano nella directory *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* . Ad esempio, il file del set di regole per abilitare tutte le regole di sicurezza si trova in *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.RuleSet*.

Copiare uno o più set di regole e incollarli nella directory che contiene il progetto di Visual Studio o direttamente in **Esplora soluzioni**.

È anche possibile [personalizzare un set di regole predefinito](how-to-create-a-custom-rule-set.md) per le proprie preferenze. Ad esempio, è possibile modificare la gravità di una o più regole in modo che le violazioni vengano visualizzate come errori o avvisi nell' **Elenco errori**.


## <a name="see-also"></a>Vedere anche

- [Configurazione analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenzioni di codifica .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
