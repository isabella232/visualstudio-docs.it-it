---
title: Collegare elementi di modello ed elementi di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 603438fda4c2f883376292b68896309a4e669be5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531067"
---
# <a name="link-model-elements-and-work-items"></a>Collegare elementi di modello ed elementi di lavoro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [collegare elementi di modello ed elementi di lavoro](https://docs.microsoft.com/visualstudio/modeling/link-model-elements-and-work-items).  
  
È possibile tenere traccia di attività, test case, bug, requisiti, problemi e altre operazioni correlate al modello collegando gli elementi del modello in Visual Studio e gli elementi di lavoro in Team Foundation Server o Visual Studio Online. È possibile inoltre associare documenti agli elementi di lavoro per associarli agli elementi del modello.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  È necessario usare Team Explorer per creare e aprire i collegamenti. Assicurarsi che il progetto di modello e i diagrammi vengano archiviati nel controllo della versione in modo che altri utenti siano in grado di aprire eventuali diagrammi collegati.  
  
 È possibile ad esempio eseguire le attività indicate di seguito.  
  
-   Collegare un elemento di lavoro di una storia utente con un diagramma attività per mostrare il modo in cui la storia viene interpretata come una sequenza di operazioni.  
  
-   Collegare un diagramma caso di utilizzo agli elementi di lavoro del test case per garantire che il caso di utilizzo sia implementato in modo corretto.  
  
-   Collegare un attributo in una classe di un diagramma classi UML a un elemento di lavoro bug per mostrare un errore nell'implementazione dell'attributo.  
  
-   Collegare un componente in un diagramma componente a un elemento di lavoro di attività per tenere traccia dello sviluppo del componente. Tale attività è generalmente suddivisa in attività minori  
  
 È possibile collegare elementi di lavoro a qualsiasi elemento che è possibile selezionare nei diagrammi di modellazione oppure in Esplora modelli UML.  
  
-   Tutti gli elementi nei modelli UML, ad esempio classi UML, linee di vita, casi di utilizzo, sottosistemi, attività, nodi oggetto, componenti, interfacce.  
  
-   Tutte le relazioni nei modelli UML, ad esempio associazioni, generalizzazioni, dipendenze, flussi, messaggi.  
  
-   Parti di elementi, quali gli attributi e le operazioni di classi, le occorrenze dell'esecuzione di linee di vita, il pin di input e di output delle attività e le parti e le porte di componenti.  
  
-   Livelli e dipendenze del livello.  
  
-   Commenti e collegamenti al commento.  
  
-   Diagrammi. Per selezionare un diagramma, scegliere una parte vuota del diagramma.  
  
> [!WARNING]
>  Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
-   [Connettersi a un progetto team](#ConnectTFS)  
  
-   [Collegare un elemento del modello a un nuovo elemento di lavoro](#LinkNew)  
  
-   [Collegare un elemento del modello a un elemento di lavoro esistente](#LinkExisting)  
  
-   [Visualizza elementi di lavoro collegato a un elemento del modello](#OpenWorkItem)  
  
-   [Visualizzare elementi del modello collegati a un elemento di lavoro](#ViewLinkedModels)  
  
-   [Eliminare collegamenti tra elementi del modello ed elementi di lavoro](#RemoveLinks)  
  
-   [Risoluzione dei problemi](#Troubleshooting)  
  
##  <a name="ConnectTFS"></a> Connettersi a un progetto team  
 Per creare, visualizzare o rimuove collegamenti, è necessario innanzitutto connettersi al progetto team.  
  
1.  Nel menu **Team** scegliere **Gestione connessioni** per visualizzare la finestra Team Explorer.  
  
2.  Se non viene visualizzato il progetto corretto, in Team Explorer scegliere **Gestione connessioni** e quindi scegliere **Connessione al progetto team**. Scegliere i progetti corretti o il server se necessario.  
  
3.  In **Team Explorer**scegliere il progetto in cui si desidera creare, collegare o visualizzare elementi di lavoro.  
  
##  <a name="LinkNew"></a> Collegare un elemento del modello a un nuovo elemento di lavoro  
  
1.  Verificare che si è connessi all'istanza di TFS che si desidera utilizzare.  
  
2.  Nel diagramma di modellazione o in **Esplora modelli UML**aprire il menu di scelta rapida per l'elemento del modello.  
  
3.  Scegliere **Crea elemento di lavoro** e il tipo di elemento di lavoro da creare.  
  
4.  Nel modulo relativo all'elemento di lavoro compilare i campi. Scegliere **Salva elemento di lavoro**.  
  
     In Visual Studio l'elemento del modello viene collegato all'elemento di lavoro. Verrà visualizzata un'icona sull'elemento del modello o nelle sue vicinanze.  
  
> [!WARNING]
>  Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
##  <a name="LinkExisting"></a> Collegare un elemento del modello a un elemento di lavoro esistente  
 Quando si collegano elementi del modello a elementi di lavoro, partire dall'elemento del modello e non dall'elemento di lavoro.  
  
1.  Verificare che si è connessi all'istanza di TFS che si desidera utilizzare.  
  
2.  Nel diagramma di modellazione o in **Esplora modelli UML**aprire il menu di scelta rapida per l'elemento del modello. Scegliere **Collega a elemento di lavoro**. Selezionare il progetto nel campo **Progetto** .  
  
3.  Scegliere uno o più elementi di lavoro da collegare all'elemento del modello con una delle operazioni seguenti:  
  
    -   Scegliere una query in **Query salvata**.  
  
    -   Digitare l'ID di uno o più elementi di lavoro separati da spazi in **ID**.  
  
    -   Digitare una parola o una frase in **Il titolo contiene**.  
  
4.  Scegliere **Trova**.  
  
5.  Nell'elenco di elementi di lavoro selezionare l'elemento o gli elementi di lavoro da collegare.  
  
     A termine, la proprietà **Elementi di lavoro** dell'elemento del modello è associata a un numero maggiore del precedente. Verrà visualizzata anche un'icona accanto o sull'elemento del modello.  
  
> [!WARNING]
>  Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
##  <a name="OpenWorkItem"></a> Visualizza elementi di lavoro collegato a un elemento del modello  
  
1.  In **Team Explorer**verificare di essere connessi al progetto team in cui gli elementi di lavoro sono collegati all'elemento del modello.  
  
2.  Nel diagramma di modellazione o in **Esplora modelli UML**aprire il menu di scelta rapida per l'elemento del modello. Scegliere **Visualizza elementi di lavoro** per visualizzare l'elenco di elementi di lavoro collegati.  
  
    > [!NOTE]
    >  Vengono visualizzati solo gli elementi di lavoro del server attualmente connesso. Se non viene visualizzato alcun elemento di lavoro, verificare di essere connessi al server corretto in **Team Explorer**.  
  
##  <a name="ViewLinkedModels"></a> Visualizzare elementi del modello collegati a un elemento di lavoro  
 È possibile visualizzare elementi e diagrammi di modellazione collegati a un elemento di lavoro in Visual Studio Online e in Team Foundation Server 2012 o versioni successive. Un elemento di lavoro potrebbe essere collegato ad esempio a modelli di classe che mostrano la progettazione di nuove classi da implementare.  
  
1.  In **Team Explorer**verificare di essere connessi al progetto team in cui gli elementi del modello sono collegati all'elemento di lavoro.  
  
    > [!NOTE]
    >  Per visualizzare gli elementi del modello collegati, è possibile usare solo Team Explorer, non Team Web Access. Verificare che l'area di lavoro venga mappata al progetto di modello contenente gli elementi o i diagrammi di modellazione. Se non si dispone di un'area di lavoro, è necessario crearla. Visualizzare [risoluzione dei problemi](#Troubleshooting) e [creare e usare aree di lavoro](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).  
  
2.  Aprire l'elemento di lavoro e scegliere **Collegamenti**. In **Collegamento modello**aprire il menu di scelta rapida per l'elemento del modello collegato. Scegliere **Apri elemento collegato**.  
  
     ![Elemento del modello collegato aperto da un elemento di lavoro](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")  
  
##  <a name="RemoveLinks"></a> Eliminare collegamenti tra elementi del modello ed elementi di lavoro  
 Eliminare un elemento di lavoro collegato a partire dall'elemento del modello. In questo modo viene rimosso il collegamento reciproco all'elemento del modello dall'elemento di lavoro. In caso contrario, se si inizia con l'elemento di lavoro, il collegamento reciproco dall'elemento del modello all'elemento di lavoro non verrà eliminato.  
  
1.  Nel diagramma di modellazione o in **Esplora modelli UML**aprire il menu di scelta rapida per l'elemento del modello.  
  
2.  Scegliere **Rimuovi elementi di lavoro**.  
  
     \- oppure -  
  
    1.  Scegliere **Proprietà**, quindi **Elementi di lavoro** in cui viene visualizzato il numero di elementi di lavoro collegati.  
  
    2.  Nella proprietà **Elementi di lavoro** scegliere il pulsante con i puntini di sospensione **[…]**.  
  
        > [!NOTE]
        >  Vengono visualizzati solo gli elementi di lavoro sul server corrente. Se l'elenco è vuoto, ma il numero di elementi di lavoro è diverso da zero, assicurarsi di essere connessi al server corretto in **Team Explorer**.  
  
3.  In **Rimuovi collegamenti a elementi di lavoro**rimuovere gli elementi selezionati da scollegare. Scegliere **OK**.  
  
##  <a name="Troubleshooting"></a> Risoluzione dei problemi  
  
|**Problema**|**Possibile causa**|**Risoluzione**|  
|---------------|------------------------|--------------------|  
|Impossibile trovare l'elemento del modello da collegare.|L'elemento potrebbe essere in un diagramma di un progetto di modello archiviato nel [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Potrebbe non essere presente un'area di lavoro mappata al diagramma.|Eseguire il mapping dell'area di lavoro al progetto di modello e al diagramma. Se non è presente un'area di lavoro, è necessario crearla.<br /><br /> Il messaggio di errore visualizzato per questo problema contiene il percorso che è possibile usare per eseguire il mapping dell'area di lavoro.<br /><br /> Visualizzare [creare e usare aree di lavoro](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|  
|Impossibile trovare l'elemento del modello collegato.|L'elemento collegato potrebbe essere in un diagramma che è stato spostato, rinominato o eliminato.|1.  Nell'elemento di lavoro, eliminare il collegamento all'elemento del modello.<br />2.  Creare un nuovo collegamento dall'elemento di lavoro all'elemento del modello.|  
|All'elemento di lavoro non sono associati gli elementi del modello collegato previsti.|Un elemento di lavoro mostra un elemento livello collegato solo se il collegamento è stato creato dall'elemento di lavoro. Se il team non usa il [!INCLUDE[esprscc](../includes/esprscc-md.md)], per creare i collegamenti verrà usato il percorso locale dei diagrammi. Se il progetto di modello e i relativi diagrammi sono nel [!INCLUDE[esprscc](../includes/esprscc-md.md)], tutti i membri del team che possono accedere al progetto potranno visualizzare gli elementi collegati negli elementi di lavoro.|Provare ad aggiornare l'elemento di lavoro.|  
|L'eliminazione di un collegamento a un elemento del modello da un elemento di lavoro non elimina il collegamento dall'elemento del modello all'elemento di lavoro.||Eliminare il collegamento all'elemento di lavoro a partire dall'elemento del modello.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)



