---
title: Debug cronologico | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a622fcb91ad40e7d0777f37ce87e9a2cb950695
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542403"
---
# <a name="historical-debugging"></a>Debug cronologico
Il debug cronologico è una modalità di debug che dipende dalle informazioni raccolte da IntelliTrace. Consente di tornare indietro e avanti l'esecuzione dell'applicazione e controllare lo stato.  
  
 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).  
  
## <a name="why-use-historical-debugging"></a>Perché usare il debug cronologico?  
 Impostazione di punti di interruzione per individuare i bug può essere una questione piuttosto hit-or-miss. È possibile impostare un punto di interruzione simile al punto nel codice in cui si ritiene che il bug sia quindi eseguire l'applicazione nel debugger e spero che il punto di interruzione ottiene accesso e il luogo in cui l'esecuzione si interrompe è in grado di rivelare l'origine del bug. In caso contrario, è possibile provare a impostare un punto di interruzione in un'altra posizione nel codice ed eseguire di nuovo il debugger, eseguire i passi del test più volte fino a individuare il problema.  
  
 ![impostare un punto di interruzione](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 È possibile utilizzare IntelliTrace e il debug cronologico per spostarsi all'interno dell'applicazione e controllare lo stato (stack di chiamate e variabili locali) senza dover impostare punti di interruzione, riavviare il debug e ripetere i passi del test. Ciò consente di risparmiare molto tempo, soprattutto quando il bug si trova approfondita in uno scenario di test che richiede molto tempo per eseguire.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Come si inizia il debug cronologico?  
 IntelliTrace è attivato per impostazione predefinita. Sufficiente è decidere quali eventi e chiamate di funzione sono di interesse e se si desidera visualizzare gli snapshot dello stato dell'applicazione completo. Per altre informazioni sulla definizione di ciò che si desidera cercare, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md).  

 - Per visualizzare gli snapshot con il debug cronologico, vedere [ispezionare stati precedenti di app con IntelliTrace](../debugger/view-historical-application-state.md)
 - Per informazioni su come controllare le variabili ed esplorare il codice, vedere [analizzare un'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)
 - Per altre informazioni sul debug con eventi di IntelliTrace, vedere [procedura dettagliata: utilizzo di IntelliTrace](../debugger/walkthrough-using-intellitrace.md).