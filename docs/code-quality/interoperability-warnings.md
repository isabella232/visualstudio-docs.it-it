---
title: Avvisi di portabilità e interoperabilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f09ccafb79a87dff5c18bb4af11a12e1b1729a4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100500"
---
# <a name="portability-and-interoperability-warnings"></a>Avvisi di portabilità e interoperabilità

Gli avvisi di portabilità supportano la portabilità tra piattaforme diverse. Gli avvisi di interoperabilità supportano l'interazione con i client COM.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
| - | - |
| [CA1401: i P/Invoke non devono essere visibili](../code-quality/ca1401.md) | Un metodo pubblico o protetto in un tipo pubblico dispone dell'attributo System.Runtime.InteropServices.DllImportAttribute (implementato anche dalla parola chiave Declare in Visual Basic). Questi metodi non devono essere esposti. |
| [CA1416: convalida della compatibilità della piattaforma](../code-quality/ca1416.md) | L'uso di API dipendenti dalla piattaforma su un componente rende il codice non più funzionante in tutte le piattaforme. |
| [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](../code-quality/ca1417.md) | I parametri stringa passati per valore con `OutAttribute` possono destabilizzare il runtime se la stringa è una stringa interna. |
