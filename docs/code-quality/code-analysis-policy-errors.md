---
title: Code Analysis Policy Errors
ms.date: 11/04/2016
description: Informazioni sugli errori dei criteri di analisi del codice in Visual Studio. Visualizzare le descrizioni degli errori che si verificano se i criteri non vengono soddisfatti quando viene archiviato il codice.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5fdd14b394bca495b38f408be94b46a4b9a68c01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860555"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors

Se i criteri di analisi del codice non sono soddisfatti al momento dell'archiviazione, si verificano gli errori seguenti:

**Le impostazioni di analisi del codice per uno o più progetti non sono compatibili con i criteri di analisi del codice.**

I requisiti di analisi del codice che controllano il controllo del codice sorgente del progetto non sono stati soddisfatti per uno o più progetti di codice. Questo errore può essere causato da una o più delle condizioni seguenti:

- L'analisi del codice non è abilitata durante la compilazione per tutti i progetti nella soluzione.

- Il set di regole locali per il progetto in Visual Studio ha un'impostazione di **azione** meno restrittiva rispetto al set di regole del progetto. ad esempio, una regola impostata su = **errore** azione sul server ha l' **azione** impostata su **avviso** o **Nessuna** nel set di regole in esecuzione in Visual Studio.

- Il set di regole specificato in Visual Studio non contiene tutte le regole specificate nel set di regole specificato nei criteri di archiviazione dell'analisi codice per il progetto.

**Criteri di analisi codice non riusciti. Sono presenti errori nel progetto {0} o la compilazione non è aggiornata.**

La compilazione contiene errori o gli errori sono stati corretti, ma l'analisi del codice non è stata eseguita dopo la correzione.

**Archiviazione non riuscita. Per i criteri di analisi del codice è necessario archiviare Visual Studio con una soluzione aperta.**

Per i criteri di analisi del codice è necessario che tutti i file archiviati debbano trovarsi nella soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**Non tutti i file nell'archiviazione in sospeso si trovano all'interno della soluzione attualmente aperta.**

Per i criteri di analisi del codice è necessario che tutti i file archiviati debbano trovarsi nella soluzione attualmente aperta. Questo errore viene generato quando esiste una soluzione aperta, ma alcuni file nella visualizzazione "archiviazione in sospeso" non fanno parte della soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**La versione di ' {0} ' non è corretta. Il nome sicuro specificato nei criteri è' {1} '.**

Questo errore si applica ai progetti .NET. Una regola. dll richiesta dai criteri di analisi del codice è presente nel computer locale, ma la chiave pubblica o la versione non corrisponde. Per correggere l'errore, l'autore del criterio deve aggiornare le dll in *C:\Programmi\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* directory nel computer.

**{0}l'assembly '' specificato nel criterio non esiste.**

Questo errore si applica ai progetti .NET. Una regola necessaria per i criteri di analisi del codice non dispone della dll corrispondente installata nel computer client. Per correggere l'errore, l'autore del criterio deve aggiornare la dll in *C:\Programmi\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* directory nel computer.

**{0}Le impostazioni delle regole di progetto non sono conformi ai criteri di analisi del codice.**

Questo errore si applica ai progetti .NET. Le impostazioni delle regole del codice gestito non sono rigorose quanto richiesto dai criteri. Per correggere l'errore, l'impostazione client deve essere uguale o più restrittiva del requisito dei criteri nel server.

**L'analisi codice non è abilitata nella configurazione attiva. Passa alla configurazione {0} e compila {1} il progetto prima di archiviare.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , per la configurazione attiva non è abilitata l'analisi del codice, ma è stata abilitata almeno un'analisi del codice.

**È necessario abilitare l'analisi del codice per i binari gestiti nelle proprietà del progetto {0} e compilare prima dell'archiviazione.**

Questo errore si verifica per [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le applicazioni .NET. Il criterio richiede l'esecuzione dell'analisi del codice gestito, ma non è abilitata nel progetto corrente nel client.

**Prima di archiviare, è necessario abilitare l'analisi del codice nelle proprietà del progetto {0} e compilare.**

Questo errore è stato applicato a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti e progetti Web. Il criterio richiede l'esecuzione dell'analisi del codice gestito, ma non è abilitata nel progetto corrente nel client.

**Prima di archiviare, è necessario abilitare l'analisi del codice C/C++ nelle proprietà del progetto {0} e compilare.**

Questo errore si applica ai progetti non gestiti. Il criterio di analisi del codice richiede l'analisi del codice per C/C++, ma non è abilitato nel progetto corrente nel client.

## <a name="see-also"></a>Vedi anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)
