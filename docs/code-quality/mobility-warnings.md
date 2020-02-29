---
title: Mobility Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6061b614442d7bcb2f3465b1c40f35d583626c45
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167585"
---
# <a name="mobility-warnings"></a>Mobility Warnings
Gli avvisi di mobilità supportano un utilizzo efficiente dell'energia elettrica.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1600: Non impostare la priorità del processo su Inattivo](../code-quality/ca1600.md)|Non impostare la priorità del processo su Inattivo. I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|
|[CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza](../code-quality/ca1601.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.|
