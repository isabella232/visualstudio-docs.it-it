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
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857074"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Domande frequenti per il debug di snapshot in Visual Studio

Ecco un elenco di domande che potrebbero sorgere durante il debug di applicazioni di Azure attive con Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual è l'impatto sulle prestazioni della creazione di uno snapshot?

Quando Snapshot Debugger acquisisce uno snapshot dell'app, crea una copia tramite fork del processo dell'app e sospende la copia creata tramite fork. Quando si esegue il debug di uno snapshot, si esegue il debug della la copia creata tramite fork del processo. Questo processo richiede solo 10-20 millisecondi, ma non copia l'heap completo dell'app. Viene invece copiata solo la tabella della pagina e le pagine vengono impostate per la copia su scrittura. Se alcuni degli oggetti dell'app nell'heap cambiano, vengono copiate le pagine corrispondenti. Questo è il motivo per cui ogni snapshot ha un costo ridotto a livello di memoria, nell'ordine di centinaia di kilobyte per la maggior parte delle app.

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Cosa accade in presenza di un servizio app di Azure con scale-out (più istanze dell'app)?

In presenza di più istanze dell'app, a ogni singola istanza vengono applicati punti di acquisizione snapshot. Solo il primo punto di acquisizione snapshot da raggiungere con le condizioni specificate crea uno snapshot. Se esistono più punti di acquisizione snapshot, gli snapshot successivi provengono dalla stessa istanza che ha creato il primo snapshot. I punti di inserimento istruzione di registrazione inviati alla finestra di output visualizzeranno solo i messaggi da un'istanza, mentre i punti di inserimento istruzione di registrazione inviati ai registri applicazioni inviano messaggi da ogni istanza.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>In che modo Snapshot Debugger carica i simboli?

Snapshot Debugger richiede di avere a disposizione i simboli corrispondenti per l'applicazione in locale o distribuiti nel servizio app di Azure. (Non sono attualmente supportati PDB incorporati.) Snapshot Debugger scarica automaticamente i simboli dal servizio app di Azure. A partire da Visual Studio 2017 versione 15.2, la distribuzione nel servizio app di Azure consente di distribuire anche i simboli dell'app.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Snapshot Debugger funziona sulle build di versione dell'applicazione?

Sì, Snapshot Debugger è progettato per funzionare sulle build di versione. Quando si inserisce un punto di acquisizione snapshot in una funzione, la funzione viene ricompilata come versione di debug, rendendo possibile il debug. Con l'arresto di Snapshot Debugger, per le funzioni viene ripristinata la versione della build di versione.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>I punti di inserimento istruzione di registrazione possono avere effetti collaterali nell'applicazione di produzione?

No, eventuali messaggi di log aggiunti all'app vengono valutati in modo virtuale e non determinano effetti collaterali nell'applicazione. Tuttavia, alcune proprietà native potrebbero non essere accessibili con i punti di inserimento istruzione di registrazione.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Se il server è sottoposto a carichi elevati, Snapshot Debugger funziona correttamente?

Sì, il debug di snapshot può funzionare nei server in condizioni di carico elevato. Snapshot Debugger limita il carico di lavoro e non acquisisce snapshot nelle situazioni in cui è presente una quantità scarsa di memoria libera nel server.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Qual è la procedura per disinstallare Snapshot Debugger?

È possibile disinstallare l'estensione del sito Snapshot Debugger nel servizio app seguendo questa procedura:

1. Disattivare il servizio app tramite Cloud Explorer nel portale di Visual Studio o di Azure.
1. Passare al sito di Kudu del servizio app (ovvero, servizioapp.**scm**.azurewebsites.net) e passare a **Estensioni del sito**.
1. Fare clic sulla X per l'estensione del sito Snapshot Debugger per rimuoverla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Per quale motivo vengono aperte delle porte durante una sessione di Snapshot Debugger?

Snapshot Debugger deve aprire un set di porte per eseguire il debug degli snapshot creati in Azure. Si tratta delle stesse porte necessarie per il debug remoto. [È possibile trovare l'elenco delle porte qui](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Eseguire il debug di app ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Eseguire il debug di app ASP.NET attive in macchine virtuali/set di scalabilità di macchine virtuali di Azure con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Eseguire il debug di servizi Azure Kubernetes ASP.NET attivi con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Risoluzione dei problemi e problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md)