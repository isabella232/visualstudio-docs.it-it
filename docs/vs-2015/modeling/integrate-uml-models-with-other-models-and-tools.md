---
title: Integrare modelli UML con altri modelli e strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f511a96f94ab98a93144938529a05d07bb6ed26
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669576"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrare modelli UML con altri modelli e strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I modelli UML possono essere integrati con altri modelli e linguaggi specifici di dominio.

 Mediante la scrittura di codice di estensione per eseguire una serie di funzioni, è possibile integrare modelli nei modi seguenti:

 Associare i riferimenti da qualsiasi elemento ad altri elementi, ad esempio a file o elementi di altri modelli.
In un elemento UML è possibile archiviare i collegamenti ad altri elementi, file o altri oggetti UML codificando le identità come stringhe.

 Ad esempio, è possibile scrivere un'estensione che può collegare qualsiasi azione UML (vale a dire, un elemento in un diagramma di attività) a un altro diagramma di attività. Quando l'utente fa doppio clic sull'azione, viene aperto un altro diagramma. Consente all'utente di fornire una visualizzazione più dettagliata dell'azione.

 Esistono due modi in cui è possibile archiviare stringhe e altri dati di qualsiasi elemento:

- **Proprietà degli stereotipi.** È possibile definire un profilo UML, in cui viene definito uno stereotipo che aggiunge proprietà a determinati tipi di elemento UML. Ad esempio, è possibile definire un profilo che aggiunge una proprietà denominata **moredetail** a un'azione UML. È possibile scrivere codice di estensione che archivia dati collegamento in un'azione applicando lo stereotipo all'azione e quindi archiviando i dati nella proprietà.

   Lo stereotipo e le relative proprietà sono visibili all'utente nella finestra Proprietà.

   Per distribuire questa estensione, comprimere la definizione del profilo e il codice di estensione in una singola estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).

   Per un progetto di esempio in cui un profilo viene distribuito insieme ai comandi di menu e ai gestori movimenti, vedere [esempio: profili UML](http://go.microsoft.com/fwlink/?LinkID=213811).

- **Riferimenti.** È possibile associare un insieme di stringhe a qualsiasi elemento UML. È possibile scrivere codice che archivia le informazioni, ad esempio un nome di file o il GUID di un altro elemento. Questa operazione può essere eseguita senza fornire definizioni aggiuntive. I riferimenti non sono direttamente visibili all'utente.

   Per altre informazioni, vedere [aggiungere stringhe di riferimento agli elementi del modello UML](../modeling/attach-reference-strings-to-uml-model-elements.md). Per un esempio, vedere [collegare elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).

  Esistono due modi per codificare i riferimenti agli elementi del modello:

- **GUID e filename** dell'elemento del modello di destinazione e del modello che lo contiene o un particolare diagramma che lo Visualizza.

   Per un esempio, vedere [collegare elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).

- **Riferimenti ModelBus.** ModelBus è un framework per la creazione e la risoluzione dei riferimenti tra modelli. Include il selettore ModelBus che consente all'utente di selezionare un elemento in un modello. Consente anche all'utente di risolvere i riferimenti persi a causa delle modifiche nel modello di destinazione.

   Per altre informazioni, vedere [integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propagare le modifiche da un modello a un altro.
  Ad esempio, è possibile sincronizzare il nome di un elemento con il nome del diagramma collegato, in modo che se l'utente ne modifica uno, anche l'altro viene modificato. Sono disponibili due meccanismi per eseguire questa operazione:

1. È possibile utilizzare **le regole VMSDK** per propagare le modifiche all'interno dello stesso modello.

    Per un esempio, vedere [collegare elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813).

2. **Gli eventi VMSDK** possono essere utilizzati per propagare le modifiche all'esterno del modello, ad esempio per modificare il nome del file di un documento collegato o per modificare un elemento in un altro modello.

   Per informazioni su entrambi i meccanismi, vedere [procedura: rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Trascinare gli elementi per copiarli da un modello a un altro. è possibile consentire all'utente di creare elementi trascinando gli elementi in un diagramma UML. Non è necessario che l'elemento creato sia una copia dell'originale. Ad esempio, è possibile consentire all'utente di trascinare un diagramma di attività da Esplora soluzioni in un altro diagramma di attività per creare una nuova azione.

   Per altre informazioni, vedere [definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) e [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="samples"></a>Esempi
 Vedere l'esempio di codice [collegare elementi UML a diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813). L'esempio consente agli utenti di trascinare un file su qualsiasi elemento UML e aprirlo successivamente facendo doppio clic sull'elemento. Ad esempio, è possibile collegare un diagramma di attività a un elemento del caso di utilizzo. Un'icona mostra gli elementi che contengono collegamenti.

 Nell'esempio di codice seguente vengono illustrate le tecniche seguenti:

- [Allegare stringhe di riferimento agli elementi del modello UML](../modeling/attach-reference-strings-to-uml-model-elements.md)

   Il codice di esempio archivia i percorsi di file e i GUID degli elementi nelle stringhe di riferimento associate all'elemento.

- Come aggiungere elementi Decorator a elementi UML. Per informazioni generali sugli elementi Decorator, vedere [personalizzazione dei campi testo e immagine](../modeling/customizing-text-and-image-fields.md).

   Nell'esempio viene aggiunto un elemento Decorator dell'immagine a forme UML.

- [Procedura: Rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)

   Nell'esempio viene illustrato come definire una regola che risponde alle nuove forme visualizzate in un diagramma.

- [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Definire un gestore modelli in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

   Nell'esempio viene illustrato come gestire gli elementi trascinati da Esplora risorse (o Esplora File), Esplora soluzioni e altri elementi UML.

  Per un esempio in cui un modello UML viene letto da un linguaggio DSL, vedere [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Vedere anche
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md) [procedura: rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md) [esempio: profili UML](http://go.microsoft.com/fwlink/?LinkID=213811) [collegare elementi UML a Diagrammi o altri file](http://go.microsoft.com/fwlink/?LinkId=213813)
