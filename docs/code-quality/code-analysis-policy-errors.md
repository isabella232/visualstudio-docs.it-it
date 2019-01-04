---
title: Errori dei criteri per l'analisi del codice
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3edd9b341d2ccead65fee8f97f32ec54f7857dea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987810"
---
# <a name="code-analysis-policy-errors"></a>Errori dei criteri per l'analisi del codice

Se non sono stato soddisfatto i criteri di analisi codice per l'archiviazione, si verificano gli errori seguenti:

**Le impostazioni di analisi del codice per uno o più progetti non sono compatibili con i criteri di analisi del codice.**

I requisiti di analisi codice check-in controllo del codice sorgente il progetto non è stata soddisfatta per uno o più progetti di codice. Questo errore può essere causato da una o più delle condizioni seguenti:

- Analisi del codice non è abilitato in fase di compilazione per tutti i progetti nella soluzione.

- La regola locale impostata per il progetto in Visual Studio ha meno restrittivo **azione** impostazione di set di regole il progetto, ad esempio, una regola che è impostata su **azione**=**errore** nel server è relativo **azione** impostata su **avviso** oppure **Nessuno** nella regola impostata viene eseguita in Visual Studio).

- Il set specificata in Visual Studio di regole non contiene tutte le regole che vengono specificate nella regola di impostare i criteri di archiviazione al posto dell'analisi del codice per il progetto specificata.

**I criteri di analisi codice non è riuscita. Sono presenti errori nel progetto {0} o la compilazione non è aggiornata.**

La compilazione contiene errori o sono stati corretti gli errori, ma l'analisi del codice non è stata eseguita dopo la correzione.

**Check-in non è riuscita. I criteri di analisi codice richiedono che l'archiviazione Visual Studio con una soluzione aperta.**

I criteri di analisi codice richiedono che devono essere eseguita la verifica tutti i file nella soluzione attualmente aperta. Per correggere questo errore, aprire la soluzione che contiene il file da archiviare.

**Non tutti i file nel controllo aggiuntivo in sospeso sono all'interno della soluzione attualmente aperta.**

I criteri di analisi codice richiedono che devono essere eseguita la verifica tutti i file nella soluzione attualmente aperta. Questo errore viene generato quando vi è una soluzione aperta, ma alcuni file nella vista "archiviazione in sospeso" non fanno parte della soluzione attualmente aperta. Per correggere questo errore, aprire la soluzione che contiene il file da archiviare.

**La versione di '{0}' non è corretto. È il nome sicuro specificato nei criteri '{1}'.**

Questo errore si applica ai progetti .NET. Esiste una regola. dll richiesto dai criteri di analisi del codice nel computer locale, ma la chiave pubblica/versione non corrisponde. Per correggere questo errore, l'autore dei criteri deve aggiornare il file con estensione dll in *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  directory nel proprio computer.

**'{0}' assembly specificati nei criteri non esiste.**

Questo errore si applica ai progetti .NET. Una regola necessaria per i criteri di analisi codice non dispone della corrispondente dll installata nel computer client. Per correggere questo errore, l'autore dei criteri deve aggiornare la dll nella *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  directory nel proprio computer.

**Progetto {0} impostazioni delle regole non sono in conformità con criteri di analisi codice.**

Questo errore si applica ai progetti .NET. Le impostazioni delle regole di codice gestito non sono più rigoroso quanto richiesto dai criteri. Per correggere questo errore, l'impostazione del client deve essere uguale o più restrittiva rispetto al requisito dei criteri nel server.

**Analisi del codice non è abilitata nella configurazione attiva. Passare alla configurazione {0} e Compila progetto {1} prima dell'archiviazione.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configurazione attiva non è attivata l'analisi codice, ma non esiste almeno un'analisi del codice abilitate.

**È necessario abilitare l'analisi del codice per i file binari gestiti nel progetto {0} compilazione prima dell'archiviazione e le proprietà.**

Questo errore si applica a [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] applicazioni .NET. I criteri richiedono l'analisi del codice gestito deve essere eseguita, ma non è abilitato nel progetto corrente sul client.

**È necessario abilitare l'analisi del codice nel progetto {0} compilazione prima dell'archiviazione e le proprietà.**

Questo errore si applica a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti e i progetti web. I criteri richiedono l'analisi del codice gestito deve essere eseguita, ma non è abilitato nel progetto corrente sul client.

**È necessario abilitare analisi del codice C/C++ nel progetto {0} compilazione prima dell'archiviazione e le proprietà.**

Questo errore si applica ai progetti non gestiti. I criteri di analisi del codice richiedono l'analisi del codice per C/C++, ma non è abilitato nel progetto corrente sul client.

## <a name="see-also"></a>Vedere anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)