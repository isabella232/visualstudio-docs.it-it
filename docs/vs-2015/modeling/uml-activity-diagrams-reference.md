---
title: 'Diagrammi di attività UML: informazioni di riferimento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 960e9469290bca42abd252d497c2ce72e62e41a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531534"
---
# <a name="uml-activity-diagrams-reference"></a>Diagrammi di attività UML: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *diagramma di attività* Mostra un processo aziendale o un processo software come flusso di lavoro tramite una serie di azioni. Queste azioni possono essere eseguite da persone, componenti software o computer.

 È possibile usare un diagramma di attività per descrivere diversi tipi di processi, come negli esempi seguenti:

- Processo aziendale o flusso di lavoro tra gli utenti e il sistema. Per altre informazioni, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).

- Passaggi eseguiti in un caso di utilizzo. Per altre informazioni, vedere [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).

- Protocollo software, cioè le sequenze consentite di interazioni tra componenti.

- Algoritmo software.

  Questo argomento illustra gli elementi che è possibile usare nei diagrammi di attività. Per informazioni più dettagliate su come disegnare i diagrammi di attività [, vedere diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md). Per creare un diagramma di attività UML, scegliere **nuovo diagramma livello o UML**dal menu **architettura** . Per altre informazioni su come creare diagrammi di modellazione in generale, vedere [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Lettura dei diagrammi di attività
 Le tabelle nelle sezioni seguenti descrivono gli elementi che è possibile usare nei diagrammi di attività e le relative proprietà principali. Per un elenco completo delle proprietà degli elementi, vedere [proprietà degli elementi nei diagrammi di attività UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Le azioni e gli altri elementi visualizzati in un diagramma di attività costituiscono un'attività. È possibile visualizzare l'attività in Esplora modelli UML. Viene creata quando si aggiunge il primo elemento al diagramma.

 Per leggere un diagramma, si supponga che un token, o thread di controllo, passi i connettori da un'azione alla successiva.

### <a name="simple-control-flows"></a>Flussi di controllo semplici
 È possibile visualizzare una sequenza di azioni con rami e cicli. Per altre informazioni su come usare gli elementi descritti qui, vedere la sezione Descrizione del flusso di controllo nell'argomento [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md).

 ![Flusso di controllo semplice](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

|**Con forme**|**elemento**|**Descrizione e proprietà principali**|
|-|-|-|
|1|**Azione**|Passaggio dell'attività in cui gli utenti o il software esegue un'attività.<br /><br /> L'azione può essere avviata quando un token è arrivato a tutti i relativi flussi in ingresso. Al termine, i token vengono inviati a tutti i flussi in uscita.<br /><br /> -   **Body** : specifica l'azione in dettaglio.<br />-   **Lingua** : linguaggio dell'espressione nel corpo.<br />-   **Postcondizioni locali** : vincoli che devono essere soddisfatti al termine dell'esecuzione. L'obiettivo raggiunto dall'azione.<br />-   **Precondizioni locali** : vincoli che devono essere soddisfatti prima dell'inizio dell'esecuzione.|
|2|**Flusso di controllo**|Connettore che mostra il flusso del controllo tra le azioni. Per interpretare il diagramma, si immagini che un token un token passi da un'azione alla successiva.<br /><br /> Per creare un flusso di controllo, usare lo strumento **connettore** .|
|3|**Nodo iniziale**|Indica la prima azione o le prime azioni nell'attività. Quando l'attività inizia, un token passa dal nodo iniziale.|
|4|**Nodo finale attività**|Fine all'attività. Quando arriva un token, l'attività termina.|
|5|**Nodo decisione**|Ramo condizionale in un flusso. Ha un input e due o più output. Un token in ingresso emerge solo su uno degli output.|
|6|**Guard**|Condizione che specifica se un token può passare lungo un connettore. Usato più frequentemente sui flussi in uscita di un nodo decisione.<br /><br /> Per impostare una protezione, fare clic con il pulsante destro del mouse su un flusso, scegliere **Proprietà** , quindi impostare la proprietà **Guard** .|
|7|**Nodo unione**|Richiesto per unire flussi che sono stati suddivisi con un nodo decisione. Ha  due o più input e un output. Un token su qualsiasi input emerge sull'output.|
|8|**Commento**|Fornisce informazioni aggiuntive sugli elementi ai quali è collegato.|
|9|**Azione chiama comportamento**|Azione definita più dettagliatamente su un altro diagramma di attività.<br /><br /> -   **Sincroni** : Se true, l'azione attende fino al termine dell'attività.<br />-   **Comportamento** : l'attività richiamata.|
|(non mostrato)|**Azione chiama operazione**|Azione che chiama un'operazione su un'istanza di una classe.|
||**Attività**|Flusso di lavoro raffigurato da un diagramma di attività. Per visualizzare le proprietà di un'attività, è necessario selezionarla in **Esplora modelli UML**.<br /><br /> -   **È di sola lettura** : se è true, l'attività non deve modificare lo stato di un oggetto.<br />-   **Esecuzione singola** : se è true, al massimo un'esecuzione di questo diagramma alla volta.|
||**Diagramma attività UML**|Diagramma che visualizza un'attività. Per vedere le proprietà, fare clic su una parte vuota del diagramma. **Nota:**  I nomi del diagramma di attività, il file che contiene il diagramma e l'attività visualizzata dal diagramma possono essere tutti diversi.|

### <a name="concurrent-flows"></a>Flussi simultanei
 È possibile descrivere sequenze di azioni eseguite contemporaneamente. Per altre informazioni, vedere Creazione di flussi simultanei.

 ![Diagramma di attività che mostra un flusso simultaneo](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

|**Con forme**|**elemento**|**Descrizione**|
|-|-|-|
|11|**Nodo fork**|Divide un singolo flusso in flussi simultanei. Ogni token in ingresso produce un token su ogni connettore in uscita.|
|12|**Nodo join**|Combina i flussi simultanei in un singolo flusso. Quando ogni flusso in ingresso ha un token in attesa, viene prodotto un token sull'output.|
|13|**Azione invia segnale**|Azione che invia un messaggio o un segnale a un'altra attività o a un thread simultaneo nella stessa attività. Il tipo e il contenuto del messaggio sono dati dal titolo dell'azione o vengono specificati nei commenti aggiuntivi.<br /><br /> L'azione può inviare dati nel segnale che può essere passato all'azione in un flusso oggetto o un pin di input (16).|
|14|**Azione accetta evento**|Azione che attende un messaggio o un segnale prima di poter continuare. Il tipo del messaggio che può essere ricevuto dall'azione è dato dal titolo dell'azione o specificato nei commenti aggiuntivi.<br /><br /> Se l'azione non ha un flusso di controllo in ingresso, produce un token quando riceve un messaggio.<br /><br /> L'azione può ricevere dati nel segnale che può essere passato su un flusso oggetto o un pin di input (17).<br /><br /> -   **IsUnmarshall** : Se true, possono essere presenti diversi pin di output tipizzati e viene eseguito il marshalling dei dati su di essi. Se false, tutti i dati vengono visualizzati in un unico pin.|

### <a name="data-flows"></a><a name="DataFlow"></a> Flussi di dati
 È possibile descrivere il flusso di dati da un'azione a un altra. Per altre informazioni sugli elementi usati in questa sezione, vedere la sezione relativa alla creazione di flussi di dati dell'argomento Linee guida per la creazione di un diagramma di attività.

 ![Diagramma di attività che mostra un flusso di dati](../modeling/media/uml-actovdata.png "UML_ActOvData")

|**Con forme**|**elemento**|**Descrizione**|
|-|-|-|
|15|**Nodo oggetto**|Rappresenta i dati che passano lungo un flusso.<br /><br /> -   **Ordinamento** -come vengono archiviati più token.<br />-   **Selection** : richiama un processo, che può essere definito in un altro diagramma, che filtra i dati.<br />-   **Limite superiore** -0 indica che i dati devono passare direttamente lungo il flusso; \* indica che i dati possono essere archiviati nel flusso.<br />-   **Type** : tipo di oggetti archiviati e trasmessi.|
|16|**Pin di input**|Rappresenta i dati che può ricevere un'azione quando viene eseguita.<br /><br /> -   **Type** : tipo di oggetti trasmessi.|
|17|**Pin di output**|Rappresenta i dati che un'azione produce quando viene eseguita.<br /><br /> -   **Type** : tipo di oggetti trasmessi.|
|18|**Nodo parametro attività**|Nodo oggetto tramite il quale i dati possono essere ricevuti o prodotti dall'attività.<br /><br /> Usato quando l'attività rappresentata dal diagramma viene chiamata da un'altra attività o quando il diagramma descrive un'operazione o una funzione.<br /><br /> -   **Type** : tipo di oggetti trasmessi.|
|(non mostrato)|**Flusso oggetto**|Connettore che mostra il flusso dei dati tra le azioni e i nodi oggetto.<br /><br /> Per creare un flusso oggetto, usare lo strumento **connettore** per collegare un pin di input o di output o un nodo oggetto a un altro elemento.<br /><br /> -   **Selection** : richiama un processo, che può essere definito in un altro diagramma, che filtra i dati.<br />-   **Transformation** : richiama un processo, che può essere definito in un altro diagramma, che trasforma i dati.<br />-   **Multicast** : indica che potrebbero essere presenti diversi componenti o oggetti destinatario.<br />-   **IsMultiReceive** : indica che è possibile che vengano ricevuti input da diversi oggetti o componenti.|

## <a name="see-also"></a>Vedere anche
 [Modificare modelli e](../modeling/edit-uml-models-and-diagrams.md) DIAGRAMmi UML diagrammi di [attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md)
