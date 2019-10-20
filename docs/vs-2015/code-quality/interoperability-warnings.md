---
title: Avvisi di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd914a65ff23b05130cb0c36162bb96a3d30aa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656496"
---
# <a name="interoperability-warnings"></a>avvisi di interoperabilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli avvisi di interoperabilità supportano l'interazione con i client COM.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Un metodo pubblico o protetto è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria.|
|[CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Un metodo pubblico o protetto in un tipo pubblico ha l'attributo System. Runtime. InteropServices. DllImportAttribute (implementato anche dalla parola chiave Declare in Visual Basic). Questi metodi non devono essere esposti.|
|[CA1402: Evitare gli overload nelle interfacce visibili a COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura (_) e un numero intero che corrisponde all'ordine di dichiarazione dell'overload.|
|[CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un tipo di valore visibile a COM è contrassegnato tramite l'attributo System. Runtime. InteropServices. StructLayoutAttribute impostato su LayoutKind. auto. Il layout di questi tipi può variare tra le versioni del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], in modo da interrompere i client COM che prevedono un layout specifico.|
|[CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Viene eseguita una chiamata al metodo Marshal. GetLastWin32Error o alla funzione [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] GetLastError equivalente e la chiamata immediatamente precedente non è a un metodo di platform invoke.|
|[CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un tipo visibile a COM deriva da un tipo non visibile a COM.|
|[CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 client COM non possono accedere a interi a 64 bit.|
|[CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM non supporta i metodi statici.|
|[CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se l'attributo ClassInterfaceAttribute non è specificato, viene utilizzata un'interfaccia di solo invio.|
|[CA1409: I tipi visibili a COM devono essere creabili](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un tipo di riferimento contrassegnato specificatamente come visibile a COM contiene un costruttore con parametri pubblico, ma non contiene un costruttore predefinito pubblico senza parametri. Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM.|
|[CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Un tipo dichiara un metodo contrassegnato tramite l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, ma non dichiara un metodo contrassegnato tramite l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> o viceversa...|
|[CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Un metodo contrassegnato tramite l'attributo System. Runtime. InteropServices. ComRegisterFunctionAttribute o l'attributo System. Runtime. InteropServices. ComUnregisterFunctionAttribute è visibile esternamente.|
|[CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un tipo è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComSourceInterfacesAttribute e almeno una delle interfacce specificate non è contrassegnata utilizzando l'attributo System.Runtime.InteropServices.InterfaceTypeAttribute impostato su ComInterfaceType.InterfaceIsIDispatch.|
|[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto dei campi alla ricerca di informazioni che non devono essere esposte o che avranno un impatto non previsto sulla progettazione o la sicurezza.|
|[CA1414: Contrassegnare argomenti P/Invoke booleani con MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Per il tipo di dati booleano sono disponibili più rappresentazioni nel codice non gestito.|
|[CA1415: Dichiarare correttamente P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Questa regola cerca platform invoke dichiarazioni di metodo che hanno come destinazione [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] le funzioni che hanno un puntatore a un parametro di struttura SOVRAPPOSTa e il parametro gestito corrispondente non è un puntatore a una struttura di <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.|
