---
title: 'Diagrammi di attività UML: Riferimento | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: bfe4eaad401ce61534e5785ed82b9e33fa2f6610
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518890"
---
# <a name="uml-activity-diagrams-reference"></a>Diagrammi di attività UML: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [diagrammi di attività UML: riferimento](https://docs.microsoft.com/visualstudio/modeling/uml-activity-diagrams-reference).  
  
Un' *diagramma di attività* viene visualizzato un processo di business o un processo software come un flusso di lavoro attraverso una serie di azioni. Queste azioni possono essere eseguite da persone, componenti software o computer.  
  
 È possibile usare un diagramma di attività per descrivere diversi tipi di processi, come negli esempi seguenti:  
  
-   Processo aziendale o flusso di lavoro tra gli utenti e il sistema. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).  
  
-   Passaggi eseguiti in un caso di utilizzo. Per altre informazioni, vedere [diagrammi caso d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).  
  
-   Protocollo software, cioè le sequenze consentite di interazioni tra componenti.  
  
-   Algoritmo software.  
  
 Questo argomento illustra gli elementi che è possibile usare nei diagrammi di attività. Per altre informazioni sulle attività di disegno vedere diagrammi [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md). Per creare un diagramma attività UML, scegliere il **Architecture** menu, fare clic su **nuovo diagramma livello o UML**. Per altre informazioni su come creare diagrammi di modellazione in generale, vedere [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Lettura dei diagrammi di attività  
 Le tabelle nelle sezioni seguenti descrivono gli elementi che è possibile usare nei diagrammi di attività e le relative proprietà principali. Per un elenco completo delle proprietà degli elementi, vedere [delle proprietà degli elementi nei diagrammi di attività UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Le azioni e gli altri elementi visualizzati in un diagramma di attività costituiscono un'attività. È possibile visualizzare l'attività in Esplora modelli UML. Viene creata quando si aggiunge il primo elemento al diagramma.  
  
 Per leggere un diagramma, si supponga che un token, o thread di controllo, passi i connettori da un'azione alla successiva.  
  
### <a name="simple-control-flows"></a>Flussi di controllo semplici  
 È possibile visualizzare una sequenza di azioni con rami e cicli. Per altre informazioni su come usare gli elementi descritti di seguito, vedere la sezione Descrizione del flusso di controllo dell'argomento [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Un flusso di controllo semplice](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Forma**|**Elemento**|**Descrizione e proprietà principali**|  
|1|**Azione**|Passaggio dell'attività in cui gli utenti o il software esegue un'attività.<br /><br /> L'azione può essere avviata quando un token è arrivato a tutti i relativi flussi in ingresso. Al termine, i token vengono inviati a tutti i flussi in uscita.<br /><br /> -   **Corpo** -specifica l'azione in modo dettagliato.<br />-   **Linguaggio** -il linguaggio dell'espressione nel corpo.<br />-   **Local Postconditions** -vincoli che devono essere soddisfatti al termine dell'esecuzione. L'obiettivo raggiunto dall'azione.<br />-   **Local Preconditions** -vincoli che devono essere soddisfatti prima dell'inizio dell'esecuzione.|  
|2|**Flusso di controllo**|Connettore che mostra il flusso del controllo tra le azioni. Per interpretare il diagramma, si immagini che un token un token passi da un'azione alla successiva.<br /><br /> Per creare un flusso di controllo, usare il **connettore** dello strumento.|  
|3|**Nodo iniziale**|Indica la prima azione o le prime azioni nell'attività. Quando l'attività inizia, un token passa dal nodo iniziale.|  
|4|**Nodo finale attività**|Fine all'attività. Quando arriva un token, l'attività termina.|  
|5|**Nodo decisione**|Ramo condizionale in un flusso. Ha un input e due o più output. Un token in ingresso emerge solo su uno degli output.|  
|6|**Guard**|Condizione che specifica se un token può passare lungo un connettore. Usato più frequentemente sui flussi in uscita di un nodo decisione.<br /><br /> Per impostare una protezione, fare clic su un flusso, fare clic su **delle proprietà** e quindi impostare il **Guard** proprietà.|  
|7|**Nodo di tipo merge**|Richiesto per unire flussi che sono stati suddivisi con un nodo decisione. Ha  due o più input e un output. Un token su qualsiasi input emerge sull'output.|  
|8|**Commentoo**|Fornisce informazioni aggiuntive sugli elementi ai quali è collegato.|  
|9|**Azione chiama comportamento**|Azione definita più dettagliatamente su un altro diagramma di attività.<br /><br /> -   **IsSynchronous** : se true, l'azione attende fino al termine dell'attività.<br />-   **Comportamento** -l'attività richiamata.|  
|(non mostrato)|**Azione chiama operazione**|Azione che chiama un'operazione su un'istanza di una classe.|  
||**Attività**|Flusso di lavoro raffigurato da un diagramma di attività. Per visualizzare le proprietà di un'attività, è necessario selezionarla in **Esplora modelli UML**.<br /><br /> -   **È di sola lettura** : se true, l'attività non deve modificare lo stato di qualsiasi oggetto.<br />-   **Is Single Execution** : se true, si verifica al massimo un'esecuzione di questo diagramma alla volta.|  
||**Diagramma attività UML**|Diagramma che visualizza un'attività. Per vedere le proprietà, fare clic su una parte vuota del diagramma. **Nota:** i nomi del diagramma di attività, il file che contiene il diagramma e l'attività visualizzata dal diagramma possa essere tutti diverso.|  
  
### <a name="concurrent-flows"></a>Flussi simultanei  
 È possibile descrivere sequenze di azioni eseguite contemporaneamente. Per altre informazioni, vedere Creazione di flussi simultanei.  
  
 ![Diagramma di attività che mostra un flusso simultaneo](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Forma**|**Elemento**|**Descrizione**|  
|11|**Nodo fork**|Divide un singolo flusso in flussi simultanei. Ogni token in ingresso produce un token su ogni connettore in uscita.|  
|12|**Nodo di join**|Combina i flussi simultanei in un singolo flusso. Quando ogni flusso in ingresso ha un token in attesa, viene prodotto un token sull'output.|  
|13|**Azione invia segnale**|Azione che invia un messaggio o un segnale a un'altra attività o a un thread simultaneo nella stessa attività. Il tipo e il contenuto del messaggio sono dati dal titolo dell'azione o vengono specificati nei commenti aggiuntivi.<br /><br /> L'azione può inviare dati nel segnale che può essere passato all'azione in un flusso oggetto o un pin di input (16).|  
|14|**Azione accetta evento**|Azione che attende un messaggio o un segnale prima di poter continuare. Il tipo del messaggio che può essere ricevuto dall'azione è dato dal titolo dell'azione o specificato nei commenti aggiuntivi.<br /><br /> Se l'azione non ha un flusso di controllo in ingresso, produce un token quando riceve un messaggio.<br /><br /> L'azione può ricevere dati nel segnale che può essere passato su un flusso oggetto o un pin di input (17).<br /><br /> -   **IsUnmarshall** : se true, possono essere presenti diversi pin di output tipizzati e i dati sono unmarshalling. Se false, tutti i dati vengono visualizzati in un unico pin.|  
  
###  <a name="DataFlow"></a> Flussi di dati  
 È possibile descrivere il flusso di dati da un'azione a un altra. Per altre informazioni sugli elementi usati in questa sezione, vedere la sezione relativa alla creazione di flussi di dati dell'argomento Linee guida per la creazione di un diagramma di attività.  
  
 ![Diagramma di attività che mostra un flusso di dati](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Forma**|**Elemento**|**Descrizione**|  
|15|**Nodo oggetto**|Rappresenta i dati che passano lungo un flusso.<br /><br /> -   **Ordinamento** : modalità vengono archiviati più token.<br />-   **Selezione** -richiama un processo, che può essere definito in un altro diagramma, che consente di filtrare i dati.<br />-   **Limite superiore** -0 indica che i dati devono passare direttamente lungo il flusso; \* indica che i dati possono essere archiviati nel flusso.<br />-   **Tipo** -tipo di oggetti archiviati e trasmessi.|  
|16|**Pin di input**|Rappresenta i dati che può ricevere un'azione quando viene eseguita.<br /><br /> -   **Tipo** -tipo di oggetti trasmessi.|  
|17|**Pin di output**|Rappresenta i dati che un'azione produce quando viene eseguita.<br /><br /> -   **Tipo** -tipo di oggetti trasmessi.|  
|18|**Nodo parametro attività**|Nodo oggetto tramite il quale i dati possono essere ricevuti o prodotti dall'attività.<br /><br /> Usato quando l'attività rappresentata dal diagramma viene chiamata da un'altra attività o quando il diagramma descrive un'operazione o una funzione.<br /><br /> -   **Tipo** -tipo di oggetti trasmessi.|  
|(non mostrato)|**Flusso oggetto**|Connettore che mostra il flusso dei dati tra le azioni e i nodi oggetto.<br /><br /> Per creare un flusso oggetto, usare il **connettore** dello strumento per collegare un input, pin di output o un nodo oggetto a un altro elemento.<br /><br /> -   **Selezione** -richiama un processo, che può essere definito in un altro diagramma, che consente di filtrare i dati.<br />-   **Trasformazione** -richiama un processo, che può essere definito in un altro diagramma, che trasforma i dati.<br />-   **IsMulticast** -indica che potrebbero essere presenti diversi componenti o oggetti destinatario.<br />-   **IsMultiReceive** -indica che gli input potrebbero essere ricevuti da diversi componenti o oggetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)



