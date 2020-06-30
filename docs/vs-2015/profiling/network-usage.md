---
title: Utilizzo della rete | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548421"
---
# <a name="network-usage"></a>Utilizzo rete
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lo strumento di diagnostica **Rete** di Visual Studio consente di raccogliere dati sulle operazioni di rete eseguite con l'[API Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). L'analisi dei dati può essere utile nella risoluzione di problemi di accesso e autenticazione, di uso errato della cache, nonché in caso di problemi di prestazioni relativi a visualizzazione e download.  
  
 Lo strumento Rete supporta solo app della piattaforma Windows Universal. Altre piattaforme non sono attualmente supportate.  
  
> [!NOTE]
> Per una descrizione più completa dello strumento Rete, vedere [Introducing Visual Studio's network tool](https://devblogs.microsoft.com/visualstudio/?m=20155) (Introduzione allo strumento Rete di Visual Studio).  
  
## <a name="collecting-network-tool-data"></a>Raccolta dei dati dello strumento di rete  
 È consigliabile eseguire lo strumento **Rete** con un progetto di Visual Studio aperto nel computer di Visual Studio.  
  
1. Aprire il progetto in Visual Studio.  
  
2. Nel menu fare clic su **debug/Profiler prestazioni...**. Scegliere **rete**, quindi scegliere **Avvia**.  
  
3. Lo strumento di rete inizia a raccogliere il traffico di rete HTTP dell'app.  
  
    Quando si esegue l'app, la visualizzazione di riepilogo nel riquadro sinistro visualizza automaticamente un elenco di operazioni HTTP acquisite. Selezionare un elemento nella visualizzazione di riepilogo per visualizzare ulteriori informazioni nel pannello dei dettagli nel riquadro di destra.  
  
4. Scegliere **Arresta** per chiudere l'app.  
  
   La finestra di report dovrebbe essere analoga alla seguente:  
  
   ![Finestra Rete](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analisi dei dati  
 È possibile analizzare il traffico HTTP acquisito mentre l'applicazione è in esecuzione o anche dopo che l'applicazione è stata chiusa, selezionando una delle operazioni di rete visualizzate nella visualizzazione di riepilogo.  
  
 Nella visualizzazione di riepilogo dello strumento **Rete** sono visualizzati i dati relativi alle singole operazioni di rete che si sono verificate durante l'esecuzione dell'app. Scegliere un'intestazione di colonna per ordinare l'elenco oppure scegliere i tipi di contenuto da visualizzare nella visualizzazione del filtro **Tipo di contenuto**.  
  
 Scegliere **Salva come HAR** per creare un file JSON utilizzabile da strumenti di terze parti come Fiddler.  
  
 Nelle visualizzazioni dei dettagli dello strumento **Rete** sono visualizzate maggiori informazioni su un'operazione di rete presente nella visualizzazione di riepilogo.  
  
 ![Riquadro dei dettagli dello strumento di rete](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|Nome|Descrizione|  
|-|-|  
|**Intestazioni**|Informazioni sulle intestazioni della richiesta dell'evento.|  
|**Corpo**|Dati relativi ai payload di richiesta e risposta.|  
|**Parameters**|Nomi e valori dei parametri delle stringhe di query.|  
|**Cookie**|Dati relativi ai cookie di richiesta e risposta.|  
|**Timings**|Grafico delle fasi di acquisizione delle risorse selezionate.|  
  
 La barra di **riepilogo** dello strumento Rete indica il numero di operazioni di rete visualizzate in un determinato momento, la quantità di dati trasferita, il tempo impiegato per il download e il numero di errori (richieste con risposte 4xx o 5xx) visibili.  
  
### <a name="analysis-tips"></a>Suggerimenti sull’analisi   
 Questo strumento evidenzia determinate aree che possono essere utili quando si esegue l’analisi correlata alla rete:  
  
1. Le richieste gestite completamente dalla cache vengono visualizzate come **(dalla cache)** nella colonna **Ricevute**. Ciò consente di determinare se si sta utilizzando la cache in modo efficace per risparmiare la larghezza di banda dell’utente o se si stanno erroneamente memorizzando nella cache risposte fornendo agli utenti finali dell'applicazione dati obsoleti.  
  
2. Le risposte di errore (4xx o 5xx) vengono visualizzate nella colonna **Risultati** con il codice di stato rosso e vengono evidenziate anche nella barra di riepilogo. In tal modo è facile individuare gli errori tra le numerose potenziali richieste nell'applicazione.  
  
3. Il pulsante di stampa della risposta (all'interno della scheda corpo) consente di analizzare i paylod di risposta JSON, XML, HTML, CSS, JavaScript e TypeScript aumentando la leggibilità del contenuto.  
  
## <a name="see-also"></a>Vedere anche  
 [Esegui gli strumenti di profilatura senza debug](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog di Visual Studio: Introduzione al controllo di rete di Visual Studio](https://blogs.msdn.com/b/visualstudio/)   
 [Video di Channel 9: Strumenti di diagnostica di Visual Studio - Nuovo Profiler di rete](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
