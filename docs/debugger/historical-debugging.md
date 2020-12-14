---
title: Debug cronologico | Microsoft Docs
description: Risolvere i problemi relativi a un'app controllando lo stato mentre si sposta indietro e avanti attraverso l'esecuzione. IntelliTrace raccoglie le informazioni per questa funzionalità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38166f777153206ad4b862ac473226aecdff4147
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398545"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Debug cronologico (C#, Visual Basic, C++)

Il debug cronologico è una modalità di debug che dipende dalle informazioni raccolte da IntelliTrace. Consente di tornare indietro e avanti l'esecuzione dell'applicazione e controllare lo stato.

 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="why-use-historical-debugging"></a>Perché usare il debug cronologico?

 Impostazione di punti di interruzione per individuare i bug può essere una questione piuttosto hit-or-miss. È possibile impostare un punto di interruzione simile al punto nel codice in cui si ritiene che il bug sia quindi eseguire l'applicazione nel debugger e spero che il punto di interruzione ottiene accesso e il luogo in cui l'esecuzione si interrompe è in grado di rivelare l'origine del bug. In caso contrario, sarà necessario provare a impostare un punto di interruzione in un'altra posizione nel codice ed eseguire nuovamente il debugger, eseguire i passi del test più volte fino a individuare il problema.

 ![impostazione di un punto di interruzione](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 È possibile usare IntelliTrace e il debug cronologico portati in giro nell'applicazione e controllare lo stato (stack di chiamate e le variabili locali) senza dover impostare punti di interruzione, riavviare il debug e ripetere i passi del test. Ciò consente di risparmiare molto tempo, soprattutto quando il bug si trova approfondita in uno scenario di test che richiede molto tempo per eseguire.

## <a name="how-do-i-start-using-historical-debugging"></a>Come iniziare a usare il debug cronologico?

IntelliTrace è attivato per impostazione predefinita. È sufficiente decidere quali eventi e chiamate di funzione sono di interesse e se si desidera visualizzare gli snapshot dello stato completo dell'applicazione. Per ulteriori informazioni sulla definizione di ciò che si desidera cercare, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md). Il supporto della funzionalità varia in base al tipo di linguaggio e app.

- Per visualizzare gli snapshot con il debug cronologico, vedere [esaminare gli Stati delle app precedenti con IntelliTrace](../debugger/view-historical-application-state.md)
- Per informazioni su come esaminare le variabili e spostarsi nel codice, vedere [esaminare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)
- Per altre informazioni sul debug con eventi di IntelliTrace, vedere [procedura dettagliata: Uso di IntelliTrace](../debugger/walkthrough-using-intellitrace.md).