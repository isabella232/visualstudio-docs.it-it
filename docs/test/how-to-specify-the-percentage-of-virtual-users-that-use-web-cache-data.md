---
title: 'Test di carico: impostare la percentuale utente virtuale usando i dati della cache Web'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a31ea50cdedbeb825d03de38a89200b6e8e5200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287402"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Procedura: Specificare la percentuale di utenti virtuali che usano i dati della cache Web

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test. Per un elenco completo delle proprietà dello scenario del test di carico e delle relative descrizioni, vedere [proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La proprietà **percentuale di nuovi utenti** viene impostata nella finestra **Proprietà** . Le proprietà degli scenari dei test di carico vengono modificate nell'**Editor test di carico**.

La proprietà **percentuale di nuovi utenti** influiscono sul modo in cui il test di carico simula la memorizzazione nella cache che verrebbe eseguita da un Web browser. Per impostazione predefinita, la proprietà **Percentuale di nuovi utenti** è impostata su 0%. Se il valore della proprietà **Percentuale di nuovi utenti** è impostato su 100%, ogni esecuzione dei test prestazioni web in un test di carico viene considerata come un nuovo utente del sito web, che non dispone nella cache del browser di alcun contenuto del sito Web ottenuto con visite precedenti. Vengono pertanto scaricate tutte le richieste del test web, comprese tutte le richieste dipendenti come le immagini.

> [!NOTE]
> Quando la stessa risorsa memorizzabile nella cache viene richiesta più volte in un test Web, le richieste non vengono scaricate.

Se si esegue il test di carico di un sito web caratterizzato da un numero significativo di utenti che tornano a visitarlo e che probabilmente hanno immagini e altro contenuto memorizzati nella cache locale, l'impostazione del 100% per la proprietà **Percentuale di nuovi utenti** genererà più richieste di download rispetto a quelle che potrebbero verificarsi nell'utilizzo reale. In questo caso, è necessario stimare la percentuale di visite effettuate da utenti che visitano per la prima volta il sito web e impostare di conseguenza la proprietà **Percentuale di nuovi utenti**.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Per specificare la percentuale di nuovi utenti per uno scenario

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico, scegliere il nodo dello scenario per cui si vuole modificare la percentuale di nuovi utenti.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4. Impostare il valore per la proprietà **percentuale di nuovi utenti** immettendo un numero per la percentuale di nuovi utenti.

5. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. È quindi possibile eseguire il test di carico usando il nuovo valore **percentuale di nuovi utenti** .

## <a name="see-also"></a>Vedere anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modificare i modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)
