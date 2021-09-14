---
title: Errori nell'applicazione dell'analisi del codice
ms.date: 11/04/2016
description: Informazioni sui messaggi di errore generati nello strumento di analisi del codice gestito in Visual Studio. Visualizzare i codici di errore e le descrizioni corrispondenti.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 62ee5dd35eaa779292f89696f6ab18f6d1dbbeec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632105"
---
# <a name="code-analysis-application-errors"></a>Errori nell'applicazione dell'analisi del codice

Questa sezione è un riferimento ai messaggi di errore generati dallo strumento di analisi del codice gestito.

## <a name="in-this-section"></a>Contenuto della sezione

|Codice|Descrizione|
|-|-|
|[CA0001](ca0001.md)|È stata generata un'eccezione all'interno dello strumento di analisi del codice gestito che non indica una condizione di errore prevista.|
|[CA0051](ca0051.md)|Non è stata selezionata alcuna regola.|
|[CA0052](ca0052.md)|Non è stata selezionata alcuna destinazione da analizzare.|
|[CA0053](ca0053.md)|Non è stato possibile caricare l'assembly della regola.|
|[CA0054](ca0054.md)|Un assembly di regole personalizzate contiene risorse XML non valide.|
|[CA0055](ca0055.md)|Impossibile caricare il file:\<path>|
|[CA0056](ca0056.md)|Una versione dello strumento di analisi di un file di progetto non è corretta.|
|[CA0057](ca0057.md)|Non è possibile eseguire il mapping delle violazioni al set corrente di destinazioni e regole.|
|[CA0058](ca0058.md)|Impossibile caricare gli assembly a cui si fa riferimento.|
|[CA0059](ca0059.md)|Errore dell'opzione della riga di comando.|
|[CA0060](ca0060.md)|Impossibile caricare gli assembly a cui si fa riferimento indirettamente.|
|[CA0061](ca0061.md)|Impossibile trovare la regola '*RuleId*'.|
|[CA0062](ca0062.md)|Impossibile trovare la regola '*RuleId*' a cui si fa riferimento nel set di regole '*RuleSetName*'.|
|[CA0063](ca0063.md)|Impossibile caricare il file del set di regole o uno dei file del set di regole dipendenti.|
|[CA0064](ca0064.md)|Non è stata eseguita alcuna analisi perché il set di regole specificato non contiene regole FxCop.|
|[CA0065](ca0065.md)|Costrutto di metadati non supportato: il tipo '*TypeName*' contiene sia una proprietà che un campo con lo stesso nome '*PropertyFieldName*'|
|[CA0066](ca0066.md)|Il valore '*VersionID*' fornito a **/targetframeworkversion** non è una versione riconosciuta.|
|[CA0067](ca0067.md)|Directory non trovata.|
|[CA0068](ca0068.md)|Impossibile trovare informazioni di debug per l'assembly di *destinazione 'AssemblyName'.*|
|[CA0069](ca0069.md)|Uso della piattaforma alternativa. *Impossibile trovare FrameworkVersion1.* In *alternativa, usare FrameworkVersion2.* Per ottenere risultati di analisi ottimali, assicurarsi che sia installata la versione corretta del framework.|
|[CA0070](ca0070.md)|Impossibile caricare l'assembly o il tipo a causa di autorizzazioni di sicurezza.|
|[CA0501](ca0501.md)|Impossibile leggere il report di output.|
|[CA0502](ca0502.md)|Lingua non supportata.|
|[CA0503](ca0503.md)|La proprietà è deprecata. Usare la proprietà che sostituisce|
|[CA0504](ca0504.md)|La directory della regola è stata ignorata perché non esiste|
|[CA0505](ca0505.md)|La proprietà è deprecata. Usare la proprietà che sostituisce|
|[Errori di FxCopCmd](fxcopcmd-errors.md)|Errori di analisi del codice gestito.|

## <a name="related-sections"></a>Sezioni correlate

- [Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)
- [Analisi della qualità del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)
