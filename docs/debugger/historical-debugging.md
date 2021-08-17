---
title: Attività di debug cronologico | Microsoft Docs
description: Risolvere i problemi di un'app controllando il relativo stato mentre si avanza avanti e indietro durante l'esecuzione. Intellitrace raccoglie le informazioni per questa funzionalità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0d3198e5fb784cac999097167ef2499004823781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074150"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Debug cronologico (C#, Visual Basic, C++)

Il debug cronologico è una modalità di debug che dipende dalle informazioni raccolte da IntelliTrace. Consente di tornare indietro e avanti l'esecuzione dell'applicazione e controllare lo stato.

 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="why-use-historical-debugging"></a>Perché usare il debug cronologico?

 Impostazione di punti di interruzione per individuare i bug può essere una questione piuttosto hit-or-miss. È possibile impostare un punto di interruzione simile al punto nel codice in cui si ritiene che il bug sia quindi eseguire l'applicazione nel debugger e spero che il punto di interruzione ottiene accesso e il luogo in cui l'esecuzione si interrompe è in grado di rivelare l'origine del bug. In caso contrario, sarà necessario provare a impostare un punto di interruzione in un'altra posizione nel codice ed eseguire nuovamente il debugger, eseguire i passi del test più volte fino a individuare il problema.

 ![impostazione di un punto di interruzione](../debugger/media/breakpointprocesa.png "Punto di interruzioneProcesa")

 È possibile usare IntelliTrace e il debug cronologico portati in giro nell'applicazione e controllare lo stato (stack di chiamate e le variabili locali) senza dover impostare punti di interruzione, riavviare il debug e ripetere i passi del test. Ciò consente di risparmiare molto tempo, soprattutto quando il bug si trova approfondita in uno scenario di test che richiede molto tempo per eseguire.

## <a name="how-do-i-start-using-historical-debugging"></a>Come iniziare a usare il debug cronologico?

IntelliTrace è attivato per impostazione predefinita. È necessario solo decidere quali eventi e chiamate di funzione sono di interesse per l'utente e se si desidera visualizzare gli snapshot dello stato completo dell'applicazione. Per ulteriori informazioni sulla definizione di ciò che si desidera cercare, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md). Il supporto delle funzionalità varia in base al linguaggio e al tipo di app.

- Per visualizzare gli snapshot con il debug cronologico, vedere [Esaminare gli stati delle app precedenti usando IntelliTrace](../debugger/view-historical-application-state.md)
- Per informazioni su come esaminare le variabili ed esplorare il codice, vedere [Esaminare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)
- Per altre informazioni sul debug con eventi di IntelliTrace, vedere [procedura dettagliata: Uso di IntelliTrace](../debugger/walkthrough-using-intellitrace.md).