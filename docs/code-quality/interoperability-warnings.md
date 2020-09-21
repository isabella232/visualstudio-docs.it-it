---
title: Avvisi di portabilità e interoperabilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808600"
---
# <a name="portability-and-interoperability-rules"></a>Regole di portabilità e interoperabilità

Le regole di portabilità supportano la portabilità tra piattaforme diverse. Le regole di interoperabilità supportano l'interazione con i client COM.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
| - | - |
| [CA1401: i P/Invoke non devono essere visibili](../code-quality/ca1401.md) | Un metodo pubblico o protetto in un tipo pubblico dispone dell'attributo System.Runtime.InteropServices.DllImportAttribute (implementato anche dalla parola chiave Declare in Visual Basic). Questi metodi non devono essere esposti. |
| [CA1416: Convalida compatibilità della piattaforma](../code-quality/ca1416.md) | L'uso di API dipendenti dalla piattaforma su un componente rende il codice non più funzionante in tutte le piattaforme. |
| [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](../code-quality/ca1417.md) | I parametri stringa passati per valore con `OutAttribute` possono destabilizzare il runtime se la stringa è una stringa interna. |
