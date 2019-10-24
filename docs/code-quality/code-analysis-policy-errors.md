---
title: Errori dei criteri per l'analisi del codice
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e6ff6000f0eab60e17642bf2bd8257154e54a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745949"
---
# <a name="code-analysis-policy-errors"></a>Errori dei criteri per l'analisi del codice

Se i criteri di analisi del codice non sono soddisfatti al momento dell'archiviazione, si verificano gli errori seguenti:

**Le impostazioni di analisi del codice per uno o più progetti non sono compatibili con i criteri di analisi del codice.**

I requisiti di analisi del codice che controllano il controllo del codice sorgente del progetto non sono stati soddisfatti per uno o più progetti di codice. Questo errore può essere causato da una o più delle condizioni seguenti:

- L'analisi del codice non è abilitata durante la compilazione per tutti i progetti nella soluzione.

- Il set di regole locali per il progetto in Visual Studio dispone di un'impostazione di **azione** meno restrittiva rispetto al set di regole del progetto, ad esempio, una regola impostata su **azione**=**errore** sul server ha la relativa **azione** impostata su **avviso** o **Nessuno** nel set di regole eseguito in Visual Studio).

- Il set di regole specificato in Visual Studio non contiene tutte le regole specificate nel set di regole specificato nei criteri di archiviazione dell'analisi codice per il progetto.

**Criteri di analisi codice non riusciti. Sono presenti errori nel progetto {0} oppure la compilazione non è aggiornata.**

La compilazione contiene errori o gli errori sono stati corretti, ma l'analisi del codice non è stata eseguita dopo la correzione.

**Archiviazione non riuscita. Per i criteri di analisi del codice è necessario archiviare Visual Studio con una soluzione aperta.**

Per i criteri di analisi del codice è necessario che tutti i file archiviati debbano trovarsi nella soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**Non tutti i file nell'archiviazione in sospeso si trovano all'interno della soluzione attualmente aperta.**

Per i criteri di analisi del codice è necessario che tutti i file archiviati debbano trovarsi nella soluzione attualmente aperta. Questo errore viene generato quando esiste una soluzione aperta, ma alcuni file nella visualizzazione "archiviazione in sospeso" non fanno parte della soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**La versione di ' {0}' non è corretta. Il nome sicuro specificato nei criteri è "{1}".**

Questo errore si applica ai progetti .NET. Una regola. dll richiesta dai criteri di analisi del codice è presente nel computer locale, ma la chiave pubblica o la versione non corrisponde. Per correggere l'errore, l'autore del criterio deve aggiornare le dll in *C:\Programmi\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* directory nel computer.

**l'assembly ' {0}' specificato nel criterio non esiste.**

Questo errore si applica ai progetti .NET. Una regola necessaria per i criteri di analisi del codice non dispone della dll corrispondente installata nel computer client. Per correggere l'errore, l'autore del criterio deve aggiornare la dll in *C:\Programmi\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* directory nel computer.

**Le impostazioni delle regole di Project {0} non sono conformi ai criteri di analisi del codice.**

Questo errore si applica ai progetti .NET. Le impostazioni delle regole del codice gestito non sono rigorose quanto richiesto dai criteri. Per correggere l'errore, l'impostazione client deve essere uguale o più restrittiva del requisito dei criteri nel server.

**L'analisi codice non è abilitata nella configurazione attiva. Passare alla configurazione {0} e compilare il progetto {1} prima di eseguire l'archiviazione.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], per la configurazione attiva non è abilitata l'analisi del codice, ma è stata abilitata almeno un'analisi del codice.

**È necessario abilitare l'analisi del codice per i binari gestiti nelle proprietà di Project {0} e compilare prima di archiviare.**

Questo errore si applica alle applicazioni .NET [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Il criterio richiede l'esecuzione dell'analisi del codice gestito, ma non è abilitata nel progetto corrente nel client.

**È necessario abilitare l'analisi del codice nelle proprietà di Project {0} e compilare prima di archiviare.**

Questo errore è stato applicato ai progetti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e ai progetti Web. Il criterio richiede l'esecuzione dell'analisi del codice gestito, ma non è abilitata nel progetto corrente nel client.

**Prima di archiviare, èC++ necessario abilitare l'analisi del codice C/codice nelle proprietà di Project {0} e compilare.**

Questo errore si applica ai progetti non gestiti. Il criterio di analisi del codice richiede l'analisi delC++codice per C/, ma non è abilitato nel progetto corrente nel client.

## <a name="see-also"></a>Vedere anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)
