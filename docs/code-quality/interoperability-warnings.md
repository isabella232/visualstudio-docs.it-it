---
title: avvisi di interoperabilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1eb65f52df4b27837c00b7557db0c5e15e6c187
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091756"
---
# <a name="interoperability-warnings"></a>avvisi di interoperabilità

Gli avvisi di interoperabilità supportano l'interazione con i client COM.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
| - | - |
| [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400.md) | Un metodo pubblico o protetto è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria. |
| [CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401.md) | Un metodo pubblico o protetto in un tipo pubblico ha l'attributo System. Runtime. InteropServices. DllImportAttribute (implementato anche dalla parola chiave Declare in Visual Basic). Questi metodi non devono essere esposti. |
| [CA1402: Evitare gli overload nelle interfacce visibili a COM](../code-quality/ca1402.md) | Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura (_) e un numero intero che corrisponde all'ordine di dichiarazione dell'overload. |
| [CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403.md) | Un tipo di valore visibile a COM è contrassegnato tramite l'attributo System. Runtime. InteropServices. StructLayoutAttribute impostato su LayoutKind. auto. Il layout di questi tipi può variare tra le versioni di .NET, in modo da interrompere i client COM che prevedono un layout specifico. |
| [CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404.md) | Viene eseguita una chiamata al metodo Marshal. GetLastWin32Error o alla funzione [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError equivalente e la chiamata immediatamente precedente non è a un metodo di platform invoke. |
| [CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM](../code-quality/ca1405.md) | Un tipo visibile a COM deriva da un tipo non visibile a COM. |
| [CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406.md) | I client COM Visual Basic 6 non è possibile accedere a numeri interi a 64 bit. |
| [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407.md) | COM non supporta i metodi statici. |
| [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408.md) | I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se l'attributo ClassInterfaceAttribute non è specificato, viene utilizzata un'interfaccia di solo invio. |
| [CA1409: I tipi visibili a COM devono essere creabili](../code-quality/ca1409.md) | Un tipo di riferimento contrassegnato specificatamente come visibile a COM contiene un costruttore con parametri pubblico, ma non contiene un costruttore predefinito pubblico senza parametri. Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM. |
| [CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410.md) | Un tipo dichiara un metodo contrassegnato tramite l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, ma non dichiara un metodo contrassegnato tramite l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> o viceversa (). |
| [CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411.md) | Un metodo contrassegnato tramite l'attributo System. Runtime. InteropServices. ComRegisterFunctionAttribute o l'attributo System. Runtime. InteropServices. ComUnregisterFunctionAttribute è visibile esternamente. |
| [CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412.md) | Un tipo è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComSourceInterfacesAttribute e almeno una delle interfacce specificate non è contrassegnata utilizzando l'attributo System.Runtime.InteropServices.InterfaceTypeAttribute impostato su ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413.md) | I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto dei campi alla ricerca di informazioni che non devono essere esposte o che avranno un impatto non previsto sulla progettazione o la sicurezza. |
| [CA1414: Contrassegnare argomenti P/Invoke booleani con MarshalAs](../code-quality/ca1414.md) | Per il tipo di dati booleano sono disponibili più rappresentazioni nel codice non gestito. |
| [CA1415: Dichiarare correttamente P/Invoke](../code-quality/ca1415.md) | Questa regola cerca platform invoke dichiarazioni di metodo che hanno come destinazione [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] le funzioni che hanno un puntatore a un parametro di struttura SOVRAPPOSTa e il parametro gestito corrispondente non è un puntatore a una struttura di <xref:System.Threading.NativeOverlapped?displayProperty=fullName>. |
