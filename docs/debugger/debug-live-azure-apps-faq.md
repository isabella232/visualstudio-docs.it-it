---
title: Domande frequenti sul debug di snapshot | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1465d7ee664b1c1d534350be19e4c067a74cb79
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024500"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Domande frequenti per il debug di snapshot in Visual Studio

Ecco un elenco di domande che potrebbero rivelarsi backup durante il debug di applicazioni di Azure in tempo reale tramite il Debugger di Snapshot.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Che cos'è l'impatto sulle prestazioni di esecuzione di uno snapshot?

Quando il Debugger di Snapshot consente di acquisire uno snapshot dell'app, è creato il fork processo dell'app e la sospensione della copia creata tramite fork. Quando si esegue il debug di uno snapshot, si esegue il debug con la copia creata tramite fork del processo. Questo processo richiede solo 10-20 millisecondi ma non vengono copiate nell'heap completo dell'app. Al contrario, viene copiata solo la tabella della pagina e imposta le pagine da copiare durante la scrittura. Se alcuni degli oggetti dell'app sulla modifica dell'heap, relative pagine vengono quindi copiate. Ogni snapshot ha pertanto a basso costo in memoria (nell'ordine di centinaia di KB per la maggior parte delle App). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Cosa accade se si dispone di un servizio App di Azure con scalabilità orizzontale (più istanze dell'app)?

Quando si dispone di più istanze dell'app, i punti di ancoraggio vengano applicate a ogni singola istanza. Solo il primo punto di ancoraggio da colpire con le condizioni specificate crea uno snapshot. Se si dispone di più punti di ancoraggio, gli snapshot successivi provengono dalla stessa istanza che ha creato il primo snapshot. Punti di registrazione inviati nella finestra di output visualizzerà solo i messaggi da un'istanza, mentre i punti di registrazione inviati a log applicazioni di inviare messaggi da ogni istanza. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>In che modo il Debugger di Snapshot caricare i simboli?

Il Debugger di Snapshot è necessario disporre di simboli corrispondenti per l'applicazione locale o distribuito al servizio App di Azure. (I PDB incorporati non sono attualmente supportati.) Il Debugger di Snapshot vengono scaricati automaticamente i simboli dal servizio App di Azure. A partire da Visual Studio 2017 versione 15.2, anche la distribuzione servizio App di Azure distribuisce i simboli dell'app.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Il Debugger di Snapshot funziona con le build di rilascio della mia applicazione?

Sì, il Debugger di Snapshot è progettato per funzionare con le build di rilascio. Quando un punto di ancoraggio viene inserito in una funzione, la funzione viene ricompilata nuovamente a una versione di debug, rendendo possibile effettuare il debug. Quando si arresta il Debugger di Snapshot, le funzioni vengono restituite per le build di rilascio. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Se punti di registrazione possono causare effetti collaterali nell'applicazione di produzione?

No, eventuali messaggi di log che aggiungere all'app vengono valutate praticamente. Essi non determina effetti collaterali nell'applicazione. Tuttavia, alcune proprietà nativa non sia accessibile con punti di registrazione. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Se il server è in condizioni di carico, il Debugger di Snapshot funziona correttamente?

Sì, il debug di snapshot può funzionare per i server in condizioni di carico. Il Debugger di Snapshot limita e non vengono acquisiti gli snapshot in situazioni in cui è presente una quantità insufficiente di memoria libera nel server.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Come disinstallo Snapshot Debugger?

È possibile disinstallare l'estensione del sito Snapshot Debugger nel servizio App con i passaggi seguenti:

1. Disattivare l'App del servizio tramite Cloud Explorer nel portale di Azure o Visual Studio.
1. Passare al sito di Kudu del servizio App (vale a dire yourappservice. **SCM**. azurewebsites.net) e passare al **estensioni del sito**.
1. Fare clic su X che l'estensione del sito Snapshot Debugger per rimuoverlo.

## <a name="see-also"></a>Vedere anche

[Debug in Visual Studio](../debugger/index.md)  
[Il debug in tempo reale delle App ASP.NET usando il Debugger di Snapshot](../debugger/debug-live-azure-applications.md)  
[Risoluzione dei problemi e problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md)
