---
title: Integrare modelli UML con altri modelli e strumenti | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b85ad2e150880042125782349120d271ff2b7d7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290290"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrare modelli UML con altri modelli e strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I modelli UML possono essere integrati con altri modelli e linguaggi specifici di dominio.  
  
 Mediante la scrittura di codice di estensione per eseguire una serie di funzioni, è possibile integrare modelli nei modi seguenti:  
  
 Associare i riferimenti da qualsiasi elemento ad altri elementi, ad esempio a file o elementi di altri modelli.  
 In un elemento UML è possibile archiviare i collegamenti ad altri elementi, file o altri oggetti UML codificando le identità come stringhe.  
  
 Ad esempio, è possibile scrivere un'estensione che può collegare qualsiasi azione UML (vale a dire, un elemento in un diagramma di attività) a un altro diagramma di attività. Quando l'utente fa doppio clic sull'azione, viene aperto un altro diagramma. Consente all'utente di fornire una visualizzazione più dettagliata dell'azione.  
  
 Esistono due modi in cui è possibile archiviare stringhe e altri dati di qualsiasi elemento:  
  
-   **Proprietà di stereotipo.** È possibile definire un profilo UML, in cui viene definito uno stereotipo che aggiunge proprietà a determinati tipi di elemento UML. Ad esempio, è possibile definire un profilo che aggiunge una proprietà denominata **MoreDetail** a un'azione UML. È possibile scrivere codice di estensione che archivia dati collegamento in un'azione applicando lo stereotipo all'azione e quindi archiviando i dati nella proprietà.  
  
     Lo stereotipo e le relative proprietà sono visibili all'utente nella finestra Proprietà.  
  
     Per distribuire questa estensione, comprimere la definizione del profilo e il codice di estensione in una singola estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     Per un progetto di esempio in cui un profilo viene distribuito con comandi di menu e gestori movimenti, vedere [esempio: profili UML](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
-   **Riferimenti.** È possibile associare un insieme di stringhe a qualsiasi elemento UML. È possibile scrivere codice che archivia le informazioni, ad esempio un nome di file o il GUID di un altro elemento. Questa operazione può essere eseguita senza fornire definizioni aggiuntive. I riferimenti non sono direttamente visibili all'utente.  
  
     Per altre informazioni, vedere [stringhe di riferimento Attach UML di elementi del modello](../modeling/attach-reference-strings-to-uml-model-elements.md). Per un esempio, vedere [collegamento di elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
 Esistono due modi per codificare i riferimenti agli elementi del modello:  
  
-   **GUID e il nome file** dell'elemento del modello di destinazione e il modello che lo contiene o un diagramma specifico che viene visualizzato.  
  
     Per un esempio, vedere [collegamento di elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
-   **Riferimenti ModelBus.** ModelBus è un framework per la creazione e la risoluzione dei riferimenti tra modelli. Include il selettore ModelBus che consente all'utente di selezionare un elemento in un modello. Consente anche all'utente di risolvere i riferimenti persi a causa delle modifiche nel modello di destinazione.  
  
     Per altre informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
 Propagare le modifiche da un modello a un altro.  
 Ad esempio, è possibile sincronizzare il nome di un elemento con il nome del diagramma collegato, in modo che se l'utente ne modifica uno, anche l'altro viene modificato. Sono disponibili due meccanismi per eseguire questa operazione:  
  
1.  **Regole VMSDK** può essere usato per propagare le modifiche apportate all'interno dello stesso modello.  
  
     Per un esempio, vedere [collegamento di elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2.  **Eventi VMSDK** può essere usato per propagare le modifiche all'esterno del modello, ad esempio, per modificare il nome del file di un documento collegato o per modificare un elemento in un altro modello.  
  
 Per informazioni su questi due meccanismi, vedere [procedura: rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
 Trascinare gli elementi per copiarli da un modello a un altro  
 È possibile consentire all'utente di creare elementi trascinando gli elementi in un diagramma UML. Non è necessario che l'elemento creato sia una copia dell'originale. Ad esempio, è possibile consentire all'utente di trascinare un diagramma di attività da Esplora soluzioni in un altro diagramma di attività per creare una nuova azione.  
  
 Per altre informazioni, vedere [definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) e [procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Esempi  
 Vedere l'esempio di codice [collegamento di elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813). L'esempio consente agli utenti di trascinare un file su qualsiasi elemento UML e aprirlo successivamente facendo doppio clic sull'elemento. Ad esempio, è possibile collegare un diagramma di attività a un elemento del caso di utilizzo. Un'icona mostra gli elementi che contengono collegamenti.  
  
 Nell'esempio di codice seguente vengono illustrate le tecniche seguenti:  
  
-   [Allegare stringhe di riferimento agli elementi del modello UML](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
     Il codice di esempio archivia i percorsi di file e i GUID degli elementi nelle stringhe di riferimento associate all'elemento.  
  
-   Come aggiungere elementi Decorator a elementi UML. Per informazioni generali sugli elementi Decorator, vedere [personalizzazione dei campi testo e immagine](../modeling/customizing-text-and-image-fields.md).  
  
     Nell'esempio viene aggiunto un elemento Decorator dell'immagine a forme UML.  
  
-   [Procedura: Rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
     Nell'esempio viene illustrato come definire una regola che risponde alle nuove forme visualizzate in un diagramma.  
  
-   [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
-   [Definire un gestore modelli in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
     Nell'esempio viene illustrato come gestire gli elementi trascinati da Esplora risorse (o Esplora File), Esplora soluzioni e altri elementi UML.  
  
 Per un esempio in cui un modello UML è essere letto da un linguaggio DSL, vedere [procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Procedura: rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Esempio: I profili UML](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Collegamento di elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813)



