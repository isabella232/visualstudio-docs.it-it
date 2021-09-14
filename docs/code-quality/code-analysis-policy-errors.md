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
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 9ca28097058c0f9c7722aacd806f00af3ef263a1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632081"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors

Se i criteri di analisi del codice non vengono soddisfatti al momento dell'archiviazione, si verificano gli errori seguenti:

**Le Code Analysis per uno o più progetti non sono compatibili con Code Analysis criteri.**

I requisiti di analisi del codice per l'archiviazione nel controllo del codice sorgente del progetto non sono stati soddisfatti per uno o più progetti di codice. Questo errore può essere causato da una o più delle condizioni seguenti:

- Code Analysis non è abilitato in fase di compilazione per tutti i progetti nella soluzione.

- Il set di regole locali per il progetto  in Visual Studio ha un'impostazione azione meno restrittiva rispetto al set di regole del progetto, ad esempio una regola impostata su Errore azione nel server ha l'azione impostata su Avviso o Nessuna nel set di regole in esecuzione  =  nel Visual Studio).   

- Il set di regole specificato in Visual Studio non contiene tutte le regole specificate nel set di regole specificato nei criteri di archiviazione Code Analysis per il progetto.

**Il criterio Code Analysis non è riuscito. Si sono verificati errori nel {0} progetto o la compilazione non è aggiornata.**

La compilazione contiene errori o gli errori sono stati corretti, ma l'analisi del codice non è stata eseguita dopo la correzione.

**L'archiviazione non è riuscita. Per Code Analysis criteri è necessario eseguire l'archiviazione tramite Visual Studio con una soluzione aperta.**

I criteri di analisi del codice richiedono che tutti i file archiviati siano nella soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**Non tutti i file nell'archiviazione in sospeso si trova all'interno della soluzione attualmente aperta.**

I criteri di analisi del codice richiedono che tutti i file archiviati siano nella soluzione attualmente aperta. Questo errore viene generato quando è presente una soluzione aperta, ma alcuni file nella visualizzazione "Archiviazione in sospeso" non fanno parte della soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

**La versione di ' {0} ' non è corretta. Il nome sicuro specificato nei criteri è ' {1} '.**

Questo errore si applica ai progetti .NET. Una regola .dll richiesta dai criteri di analisi del codice esiste nel computer locale, ma la versione/chiave pubblica non corrisponde. Per correggere l'errore, l'autore dei criteri deve aggiornare i file DLL nella directory *C:\Programmi\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules \\* nel computer.

**{0}L'assembly ' specificato nei criteri non esiste.**

Questo errore si applica ai progetti .NET. Una regola richiesta dai criteri di analisi del codice non dispone della DLL corrispondente installata nel computer client. Per correggere l'errore, l'autore dei criteri deve aggiornare la DLL nella directory *C:\Programmi\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules \\* nel computer.

**{0}Project Le impostazioni delle regole non sono conformi ai Code Analysis criteri.**

Questo errore si applica ai progetti .NET. Le impostazioni delle regole del codice gestito non sono restrittive come richiesto dal criterio. Per correggere l'errore, l'impostazione del client deve essere uguale o più restrittiva rispetto ai requisiti dei criteri nel server.

**Code Analysis non è abilitato nella configurazione attiva. Passare alla configurazione {0} e compilare il progetto {1} prima dell'archiviazione.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la configurazione attiva non ha l'analisi del codice abilitata, ma è abilitata almeno un'analisi del codice.

**È necessario abilitare Code Analysis per i file binari gestiti nelle proprietà del progetto {0} e compilare prima di archiviare.**

Questo errore si applica alle [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] applicazioni .NET. I criteri richiedono l'esecuzione dell'analisi del codice gestito, ma non sono abilitati nel progetto corrente nel client.

**È necessario abilitare Code Analysis nelle proprietà del {0} progetto e compilare prima di archiviare.**

Questo errore si è applicato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a progetti e progetti Web. I criteri richiedono l'esecuzione dell'analisi del codice gestito, ma non sono abilitati nel progetto corrente nel client.

**È necessario abilitare C/C++ Code Analysis nelle proprietà del progetto {0} e compilare prima di archiviare.**

Questo errore si applica ai progetti non gestiti. I criteri di analisi del codice Code Analysis per C/C++, ma non sono abilitati nel progetto corrente nel client.

## <a name="see-also"></a>Vedi anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)
