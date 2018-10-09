---
title: Gestire modelli e diagrammi nel controllo della versione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1c2cc85b5ae94e95ef5f1e07a6d3ca13663fbb44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532200"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Gestire modelli e diagrammi nel controllo della versione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gestire modelli e diagrammi nel controllo della versione](https://docs.microsoft.com/visualstudio/modeling/manage-models-and-diagrams-under-version-control).  
  
Gestire versioni diverse dei progetti di modellazione e i diagrammi, incluse le mappe codice (file con estensione dgml), usando [Usa il controllo della versione di Team Foundation o Git](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); entrambi con un'istanza locale di Team Foundation Server o nel cloud con Visual Studio Team Services.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
>  Prestare attenzione quando diversi utenti lavorano sullo stesso progetto di modellazione. Scopri come è possibile [organizzare modelli in progetti di medie o grandi dimensioni](../modeling/structure-your-modeling-solution.md).  
  
##  <a name="ModelingProjects"></a> File in un progetto di modellazione  
 Più utenti possono usare un progetto di modellazione contemporaneamente, purché lavorino su file diversi.  
  
 Per evitare o risolvere i conflitti tra le modifiche apportate da utenti diversi, è importante comprendere la modalità di archiviazione del modello nei file.  
  
-   Ogni pacchetto viene archiviato in un file **.uml** distinto, che viene mantenuto nella cartella del progetto **ModelDefinition** . Il modello contiene anche un file **.uml** . Se uno di questi file viene eliminato o danneggiato, il pacchetto o modello corrispondente andrà perso.  
  
-   Ogni diagramma viene archiviato in due file. Ad esempio, un diagramma classi ha:  
  
    -   **DiagramName.classdiagram** - Se questo file viene eliminato o danneggiato, il diagramma andrà perso, ma le classi e le associazioni in esso visualizzate rimangono nel modello e possono essere visualizzate in Esplora modelli UML.  
  
    -   **DiagramName.classdiagram.layout** - Se questo file viene eliminato, le forme verranno comunque visualizzate nel diagramma, ma le loro dimensioni e posizioni andranno perse. Ogni file di layout è affiliato a un file di diagramma. Per visualizzarlo, fare clic su [+] accanto al file di diagramma in Esplora soluzioni.  
  
> [!NOTE]
>  È importante mantenere la coerenza tra i file. Ad esempio, se si usa il controllo del codice sorgente per eseguire il rollback delle modifiche in un file UML, è necessario eseguire contemporaneamente il rollback delle modifiche corrispondenti nei file con estensione *diagram e layout. Gli elementi rappresentati in una. \*file del diagramma verranno perse se non sono inoltre rappresentati in un file con estensione UML.  
  
##  <a name="Shared"></a> Lavorando su progetti di modellazione condivisi  
 Per ridurre al minimo i conflitti tra operazioni simultanee su parti diverse di un progetto:  
  
-   Dividere un progetto di modellazione in pacchetti che rappresentano diverse aree di lavoro. Spostare l'intero modello nei pacchetti, anziché lasciarlo nel modello radice. Per altre informazioni, vedere [definire pacchetti e spazi dei nomi](../modeling/define-packages-and-namespaces.md).  
  
-   Utenti diversi non devono usare lo stesso pacchetto o diagramma contemporaneamente.  
  
-   Se si usano i profili, assicurarsi che tutti abbiano installato gli stessi profili. Visualizzare [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
-   Per garantire che venga modificato solo il pacchetto che si sta usando:  
  
    -   Impostare la proprietà **LinkedPackage** di una classe UML, di un componente o di un caso d'uso di un diagramma.  
  
    -   In Esplora modelli UML trascinare un'attività o interazione nel pacchetto appena creato. Questo elemento verrà visualizzato in Esplora modelli UML quando si crea il primo nodo nel diagramma di sequenza o di attività.  
  
-   Per tenere traccia dei pacchetti, rinominare i file di pacchetto in modo che rispecchino i nomi dei pacchetti effettivi.  
  
-   Nelle [!INCLUDE[esprscc](../includes/esprscc-md.md)], eseguire sempre **Archivia** e **Leggi ultima versione** operazioni nel progetto di modellazione completo, mai sui singoli file.  
  
-   Eseguire sempre un'operazione **Leggi** immediatamente prima di archiviare il progetto di modellazione.  
  
-   Chiudere sempre tutti i diagrammi prima di eseguire un'operazione **Leggi** .  
  
    > [!NOTE]
    >  Se un file viene aperto quando si esegue un'operazione **Leggi**e l'operazione comporta modifiche locali, verrà richiesto di ricaricare il file. In questo caso, fare clic su **No**, quindi ricaricare il progetto completo. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto di modellazione, scegliere **Scarica progetto**e quindi scegliere **Ricarica progetto**.  
  
###  <a name="Exclusive"></a> Modifiche che richiedono l'accesso esclusivo al modello  
 Prima di eseguire i seguenti tipi di modifiche, assicurarsi che sia presente un blocco di estrazione per l'intero progetto.  
  
-   Ridenominazione o eliminazione di elementi a cui si fa riferimento da altri pacchetti.  
  
-   Modifica delle proprietà delle relazioni che superano i limiti del pacchetto.  
  
-   Per altre informazioni sui blocchi di estrazione, vedere [controllare estrarre e modificare i file](http://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Per spostare un file di diagramma all'interno o all'esterno di una cartella di progetto  
  
1.  Avviare **Prompt dei comandi per gli sviluppatori per Visual Studio**.  
  
2.  Usare **tf rename** per spostare il file del diagramma e il relativo file **.layout** :  
  
     `tf rename sourcePath targetPath`  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul file, quindi scegliere **Escludi dal progetto**.  
  
4.  Aggiungere il file alla cartella di destinazione.  
  
     In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella di destinazione o sul progetto, puntare ad **Aggiungi**e quindi fare clic su **Elemento esistente**. Nella finestra di dialogo selezionare il file di diagramma e quindi fare clic su **Aggiungi**. Il file di layout verrà aggiunto automaticamente.  
  
    > [!NOTE]
    >  Non è possibile spostare il file in un progetto diverso.  
  
##  <a name="Merging"></a> Unione delle modifiche nei file di modello e diagrammi  
 Quando più utenti lavorano su un modello contemporaneamente, [!INCLUDE[esprscc](../includes/esprscc-md.md)] richiederà di unire le modifiche nei file di modello. Lavorando su progetti separati come descritto nelle sezioni precedenti è possibile evitare la maggior parte delle unioni. In genere i conflitti rimanenti possono essere uniti automaticamente in modo sicuro. I seguenti tipi di modifiche non dovrebbero comportare alcuna difficoltà:  
  
-   Tipi di linee di vita. Quando si aggiunge una linea di vita a un'interazione (diagramma di sequenza), il relativo tipo viene archiviato nel modello radice, a meno che la linea di vita non sia stata creata da un tipo esistente.  
  
-   Le nuove attività e interazioni vengono inizialmente archiviate nel modello radice.  
  
-   Aggiunta di elementi e relazioni.  
  
-   Ridenominazione o eliminazione di elementi a cui si fa riferimento solo all'interno dei relativi pacchetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)   
 [Condividere modelli ed esportare diagrammi](../modeling/share-models-and-exporting-diagrams.md)


