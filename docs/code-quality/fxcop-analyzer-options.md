---
title: Opzioni di configurazione dell'analizzatore FxCop
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78967c93a990aaef0d5863446433c286bdcf46b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649602"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Opzioni dell'ambito della regola per gli analizzatori FxCop

Alcune regole dell'analizzatore FxCop consentono di perfezionare le parti della codebase a cui devono essere applicate. In questa pagina sono elencate le opzioni di configurazione dell'ambito disponibili, i relativi valori consentiti e le regole a cui è possibile applicare. Per usare queste opzioni, specificarle in un [file EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Queste opzioni di configurazione sono disponibili a partire dalla versione 2.6.3 del pacchetto NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Per visualizzare l'elenco completo delle opzioni disponibili per una determinata versione del pacchetto FxCopAnalyzers, esaminare il file *analizzatore Configuration.MD* nella cartella della *documentazione* per il pacchetto. Il file si trova in *% USERPROFILE% \\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version \> \documentation\analyzer Configuration.MD*. Questo file di documentazione di configurazione è incluso in ogni versione del pacchetto, a partire dalla versione 2.6.5. Di seguito è riportato un esempio di come è documentata un'opzione nel file *Configuration.MD dell'analizzatore* :
>
> Nome dell'opzione: `sufficient_IterationCount_for_weak_KDF_algorithm` \
> Valori delle opzioni: valori integrali \
> Valore predefinito: specifico per ogni regola configurabile (' 100000' per impostazione predefinita per la maggior parte delle regole) \
> Esempio: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Parte della superficie dell'API da analizzare | `public`<br/>`internal` o `friend`<br/>`private`<br/>`all`<br/><br/>Separa più valori con una virgola (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se ignorare i metodi asincroni che non restituiscono un valore | `true`<br/>`false` | `false` | [Ca2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Indica se escludere i [parametri di tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) carattere singolo dalla regola, ad esempio `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> Nella versione 2.6.3 e versioni precedenti del pacchetto dell'analizzatore, questa opzione è denominata `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Descrizione | Valori consentiti | Valore predefinito | Regole configurabili |
| - | - | - | - |
| Specifica che il codice in un progetto che genera questo tipo di assembly deve essere analizzato | Uno o più campi dell'enumerazione <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Separa più valori con una virgola (,) | Tutti i tipi di output | [Ca2007](ca2007-do-not-directly-await-task.md) |
