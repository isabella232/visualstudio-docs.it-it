---
title: Opzioni di configurazione di .NET Code Quality Analyzer
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0370688b53e87cf6ea1f5079d2e5c706777dd0c7
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706568"
---
# <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Opzioni dell'ambito delle regole per gli analizzatori di qualità del codice .NET

Alcune regole di .NET Code Quality Analyzer consentono di perfezionare le parti della codebase a cui devono essere applicate. In questa pagina sono elencate le opzioni di configurazione dell'ambito disponibili, i relativi valori consentiti e le regole a cui è possibile applicare. Per usare queste opzioni, specificarle in un [file EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

> [!TIP]
> Per visualizzare l'elenco completo delle opzioni disponibili, vedere il [file Configuration.MD dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Di seguito è riportato un esempio di come è documentata un'opzione nel file *Configuration.MD dell'analizzatore* :
>
> Nome dell'opzione: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valori delle opzioni: valori integrali \
> Valore predefinito: specifico per ogni regola configurabile (' 100000' per impostazione predefinita per la maggior parte delle regole) \
> Esempio: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Parte della superficie dell'API da analizzare | `public`<br/>`internal` o `friend`<br/>`private`<br/>`all`<br/><br/>Separa più valori con una virgola (,) | `public` | [CA1000](ca1000.md) [Ca1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) , [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801 CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se ignorare i metodi asincroni che non restituiscono un valore | `true`<br/>`false` | `false` | [Ca2007](ca2007.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se escludere i [parametri di tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) carattere singolo dalla regola, ad esempio `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Specifica che il codice in un progetto che genera questo tipo di assembly deve essere analizzato | Uno o più campi dell' <xref:Microsoft.CodeAnalysis.OutputKind> enumerazione<br/><br/>Separa più valori con una virgola (,) | Tutti i tipi di output | [Ca2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

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

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se ignorare l'analisi per il `this` parametro dei metodi di estensione | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| I nomi dei metodi di convalida del controllo null che convalidano gli argomenti passati al metodo sono non null | Formati dei nomi di metodo consentiti (separati da `|` ):<br/> -Solo nome metodo (include tutti i metodi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `M:` prefisso facoltativo | Nessuno | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei metodi di formattazione delle stringhe aggiuntivi | Formati dei nomi di metodo consentiti (separati da `|` ):<br/> -Solo nome metodo (include tutti i metodi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `M:` prefisso facoltativo | Nessuno | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei tipi, in modo che il tipo e tutti i relativi tipi derivati siano esclusi per l'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome del tipo (include tutti i tipi con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel formato dell'ID di [documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo con `T:` prefisso facoltativo | Nessuno | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi dei simboli esclusi per l'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome simbolo (include tutti i simboli con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel [formato ID documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo. Ogni nome di simbolo richiede un prefisso di tipo simbolo, ad esempio il prefisso "M:" per i metodi, il prefisso "T:" per i tipi, il prefisso "N:" per gli spazi dei nomi e così via.<br/> - `.ctor` per costruttori e `.cctor` per costruttori statici | Nessuno | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) CA, [caCA2302](ca2302.md) [CA2301](ca2301.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [ca3003](ca3003.md) [ca3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Nomi di simboli non consentiti nel contesto dell'analisi | Formati dei nomi di simboli consentiti (separati da `|` ):<br/> -Solo nome simbolo (include tutti i simboli con il nome, indipendentemente dal tipo o dallo spazio dei nomi che lo contiene)<br/> -Nomi completi nel [formato ID documentazione](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del simbolo. Ogni nome di simbolo richiede un prefisso di tipo simbolo, ad esempio il prefisso "M:" per i metodi, il prefisso "T:" per i tipi, il prefisso "N:" per gli spazi dei nomi e così via.<br/> - `.ctor` per costruttori e `.cctor` per costruttori statici | Nessuno | [CA1031](ca1031.md) |
