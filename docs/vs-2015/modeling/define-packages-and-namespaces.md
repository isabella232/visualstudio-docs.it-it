---
title: Definire pacchetti e spazi dei nomi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 58a6c33449162665c10c6fa1d2c96f665c904a98
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915027"
---
# <a name="define-packages-and-namespaces"></a>Definire pacchetti e spazi dei nomi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, un *pacchetto* è un contenitore per le definizioni di elementi UML, ad esempio classi, casi d'uso e i componenti. Un pacchetto può contenere anche altri pacchetti.  
  
 In Esplora modelli UML, tutte le definizioni all'interno di un pacchetto vengono annidate sotto il pacchetto. Il modello UML è un tipo di pacchetto e costituisce la radice dell'albero.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>In questo argomento  
 [Spazi dei nomi](#Namespaces)  
  
 [Creazione e visualizzazione dei pacchetti](#Packages)  
  
 [Creazione di elementi del modello all'interno di pacchetti](#Elements)  
  
 [Lo spostamento di elementi all'interno o all'esterno di un pacchetto](#Moving)  
  
 [Inserimento di elementi in un pacchetto](#Pasting)  
  
 [Importa relazioni tra pacchetti](#Import)  
  
 [Riferimenti da uno Namespace a altro](#References)  
  
 [Proprietà dei pacchetti](#Properties)  
  
##  <a name="Namespaces"></a> Spazi dei nomi  
 I pacchetti sono utili per suddividere il lavoro in aree diverse. Ogni pacchetto definisce uno spazio dei nomi, in modo che i nomi definiti in pacchetti diversi non siano in conflitto tra loro.  
  
 La proprietà del nome completo di ogni elemento è il nome completo del pacchetto a cui appartiene, seguito dal nome dell'elemento stesso. Ad esempio, se il pacchetto si chiama `MyPackage`, una classe nel pacchetto avrà un nome completo come `MyPackage::MyClass`. Poiché ogni elemento è contenuto in un modello, ogni nome completo inizia con il nome del modello.  
  
 Un modello definisce anche uno spazio dei nomi, quindi il nome completo di ogni elemento in un modello inizia con il nome del modello.  
  
 Anche altri elementi del modello definiscono gli spazi dei nomi. Ad esempio, un'operazione appartiene allo spazio dei nomi definito dalla classe padre, quindi il nome completo sarà `MyModel ::MyPackage ::MyClass ::MyOperation`. Allo stesso modo, un'azione appartiene allo spazio dei nomi definito dall'attività padre.  
  
 I pacchetti sono contenitori. Se si sposta o si elimina un pacchetto, vengono spostati o eliminati anche le classi, i pacchetti e gli altri elementi definiti al suo interno. Lo stesso vale per altri elementi che definiscono gli spazi dei nomi.  
  
##  <a name="Packages"></a> Creazione e visualizzazione dei pacchetti  
 È possibile creare un pacchetto in un diagramma classi UML o in Esplora modelli UML.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Per creare un pacchetto in un diagramma classi UML  
  
1.  Aprire un diagramma classi UML o crearne uno nuovo.  
  
2.  Scegliere il **pacchetto** dello strumento.  
  
3.  Fare clic in un punto qualsiasi del diagramma. Verrà visualizzata una nuova forma pacchetto.  
  
     È possibile fare clic all'interno di un pacchetto esistente per annidare un pacchetto in un altro.  
  
4.  Digitare un nuovo nome per il pacchetto.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>Per creare un pacchetto in Esplora modelli UML  
  
1. Aprire **Esplora modelli UML**. Nel **architettura** dal menu **Windows**, quindi fare clic sul **Esplora modelli UML**.  
  
2. Fare clic con il pulsante destro del mouse su un pacchetto o un modello a cui si desidera aggiungere un nuovo pacchetto.  
  
   > [!NOTE]
   >  È possibile annidare un pacchetto all'interno di un altro pacchetto.  
  
3. Puntare **Add** e quindi fare clic su **pacchetto**.  
  
    Nel modello viene visualizzato un nuovo pacchetto.  
  
4. Digitare un nuovo nome per il pacchetto.  
  
   Se è stato creato un pacchetto in Esplora modelli UML, è possibile visualizzarlo in un diagramma classi UML. È inoltre possibile visualizzare un pacchetto in più diagrammi classi UML.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Per visualizzare un pacchetto esistente in un diagramma classi UML  
  
-   Trascinare il pacchetto da Esplora modelli UML al diagramma classi.  
  
    > [!NOTE]
    >  Questo crea una visualizzazione del pacchetto nel diagramma. Non mostrerà necessariamente tutti gli elementi contenuti nel pacchetto. Per assicurarsi che sia visibile tutto il contenuto di un pacchetto, visualizzarlo in Esplora modelli UML.  
  
##  <a name="Elements"></a> Creazione di elementi del modello all'interno di pacchetti  
 È possibile inserire gli elementi del modello all'interno di un pacchetto in quattro modi:  
  
- Aggiungere un nuovo elemento a un pacchetto in Esplora modelli UML.  
  
- Aggiungere classi e altri tipi ai pacchetti in un diagramma classi UML.  
  
- Impostare il **LinkedPackage** proprietà di un diagramma in modo che i nuovi elementi creati nel diagramma vengono posizionati all'interno del pacchetto specificato. I diagrammi classi, i diagrammi dei componenti e i diagrammi caso di utilizzo possono essere collegati a un pacchetto in questo modo.  
  
- Spostare elementi all'interno o all'esterno di un pacchetto in Esplora modelli UML.  
  
  Un elemento in un pacchetto viene visualizzato sotto il pacchetto in Esplora modelli UML e il nome completo inizia con il nome completo del pacchetto. Per visualizzare il nome completo di qualsiasi elemento, fare doppio clic dell'elemento e quindi fare clic su **proprietà**. Il **nome qualificato** proprietà viene visualizzata nella **proprietà** finestra.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Per creare un elemento in un pacchetto in Esplora modelli UML  
  
1.  Aprire **Esplora modelli UML**. Nel **visualizzazione** dal menu **Other Windows**, quindi fare clic su **Esplora modelli UML**.  
  
2.  Fare clic con il pulsante destro del mouse su un pacchetto o un modello a cui si desidera aggiungere un nuovo elemento.  
  
3.  Puntare **Add**, quindi scegliere il tipo di elemento che si desidera aggiungere.  
  
     Il nuovo elemento viene visualizzato sotto il pacchetto.  
  
4.  Digitare il nome del nuovo elemento.  
  
    > [!NOTE]
    >  Il nuovo elemento non appare in alcun diagramma. Per creare una visualizzazione del nuovo elemento, è possibile trascinarlo da Esplora modelli UML a un diagramma. Il diagramma deve essere un tipo che visualizzerà questo genere di elemento.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Per creare un elemento in un pacchetto in un diagramma classi UML  
  
1.  Aprire un diagramma classi in cui viene visualizzato il pacchetto.  
  
    -   Se non è già stato fatto, creare un nuovo pacchetto.  
  
    -   Per visualizzare un pacchetto esistente in un diagramma classi, è possibile trascinare il pacchetto dal **Esplora modelli UML** al diagramma classi.  
  
2.  Fare clic sullo strumento per una classe, un'interfaccia o un'enumerazione oppure un pacchetto.  
  
3.  Fare clic sul pacchetto in cui si desidera inserire il nuovo elemento.  
  
     Il nuovo elemento viene visualizzato all'interno del pacchetto.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Per creare tutti gli elementi di un diagramma in un pacchetto specificato  
  
1.  Se non è già stato fatto, creare il nuovo pacchetto.  
  
2.  Aprire un diagramma dei componenti, un diagramma caso di utilizzo o un diagramma classi UML.  
  
3.  Aprire le proprietà del diagramma. Fare doppio clic su una parte vuota del diagramma e quindi fare clic su **proprietà**.  
  
4.  Nel **pacchetto collegato** proprietà, scegliere il pacchetto che si desidera includere il contenuto del diagramma.  
  
5.  Creare nuovi elementi nel diagramma, che verranno inseriti nel pacchetto.  
  
    -   Il **nome qualificato** di ogni elemento inizierà con il nome del pacchetto completo.  
  
    -   Nelle **Esplora modelli UML**, ogni elemento verrà visualizzato sotto il pacchetto.  
  
##  <a name="Moving"></a> Lo spostamento di elementi da e verso i pacchetti  
 È possibile spostare uno o più elementi all'interno o all'esterno di un pacchetto.  
  
 Se si sposta un pacchetto, si sposta anche il relativo contenuto.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Per spostare un elemento all'interno o all'esterno di un pacchetto  
  
-   In Esplora modelli UML trascinare l'elemento all'interno o all'esterno dell'albero la cui radice è il pacchetto.  
  
     Il nome completo dell'elemento cambierà e indicherà il nuovo pacchetto o modello proprietario.  
  
     \- oppure -  
  
-   In un diagramma classi trascinare l'elemento in una forma pacchetto.  
  
     Il nome completo dell'elemento cambierà e indicherà il nuovo pacchetto proprietario.  
  
    > [!NOTE]
    >  Se si trascina un elemento all'esterno di un pacchetto in una parte vuota del diagramma, il pacchetto proprietario non cambia. In questo modo è possibile creare un diagramma che mostra gli elementi di diversi pacchetti senza dover visualizzare i pacchetti stessi.  
  
##  <a name="Pasting"></a> Inserimento di elementi in un pacchetto  
 È possibile incollare un elemento in un pacchetto. Se si incolla un gruppo di elementi correlati in un pacchetto, verranno incollate anche le relazioni tra di essi.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Per incollare elementi in un pacchetto in un diagramma classi UML  
  
1.  In un diagramma classi UML selezionare tutti gli elementi che si desidera copiare. Fare doppio clic su uno di essi e quindi fare clic su **copia**.  
  
2.  Fare doppio clic su pacchetto e quindi fare clic su **Incolla**.  
  
    > [!NOTE]
    >  Il pacchetto può trovarsi in un diagramma diverso.  
  
##  <a name="Import"></a> Importa relazioni tra pacchetti  
 È possibile definire una relazione di importazione tra pacchetti, usando il **importare** dello strumento.  
  
 Con l'importazione gli elementi definiti nel pacchetto importato, ovvero gli elementi all'estremità freccia della relazione, vengono effettivamente definiti anche nel pacchetto da importare. Tutti gli elementi la cui visibilità viene definito come **pacchetto** saranno visibili anche nel pacchetto di importazione.  
  
 Evitare di creare cicli nelle relazioni di importazione.  
  
##  <a name="References"></a> Riferimenti da uno Namespace a altro  
 Per fare riferimento a un elemento di un pacchetto da un altro, è necessario usare il nome completo dell'elemento.  
  
 Ad esempio, si supponga che il pacchetto `SalesCommon` definisca il tipo `CustomerAddress`. In un altro pacchetto `RestaurantSales`, si vuole definire un tipo `MealOrder`, con un attributo di tipo Customer Address. Sono disponibili due opzioni:  
  
-   Specificare il tipo dell'attributo usando il nome completo `SalesCommon::CustomerAddress`. È consigliabile eseguire questa operazione solo se `CustomerAddress` ha relativi **visibilità** impostata su **pubblica**.  
  
-   Creare una relazione di importazione dal pacchetto `RestaurantSales` al pacchetto `SalesCommon`. Si potrà quindi usare `CustomerAddress` senza usare il nome completo.  
  
##  <a name="Properties"></a> Proprietà dei pacchetti  
 Ogni pacchetto presenta le proprietà seguenti. Per visualizzare le proprietà, fare doppio clic su pacchetto, in un diagramma o in Esplora modelli UML e quindi fare clic su **proprietà**.  
  
|Proprietà|Valore predefinito|Descrizione|  
|--------------|-------------------|-----------------|  
|**Name**|(nuovo nome)|Nome del pacchetto. È possibile modificarlo nel diagramma o nella finestra Proprietà.|  
|**Nome completo**|*Contenitore* :: *nome pacchetto*|Nome completo, preceduto dal nome del pacchetto o del modello contenente questo pacchetto. Per altre informazioni, vedere [Spazi dei nomi](#Namespaces).|  
|**Profili**|(vuoto)|Elenco dei profili collegati a questo pacchetto. Questi profili forniscono gli stereotipi che possono essere applicati agli elementi all'interno del pacchetto. Per altre informazioni, vedere [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Visibilità**|**Public**|Visibilità del pacchetto all'esterno del pacchetto padre.|  
|**Elementi di lavoro**|(vuoto)|Elenco di elementi di lavoro collegati. Per altre informazioni, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|  
|**Percorso definizione**|(un nome)|Nome file in cui sono archiviati i dettagli del pacchetto. I file si trovano all'interno di **ModelDefinition** cartella del progetto. Queste informazioni possono essere utili a scopo di controllo del codice sorgente.|  
|**Descrizione**|(vuoto)|Descrizione del pacchetto.|  
|**Stereotipi**|(vuoto)|Stereotipi applicati al pacchetto. L'elenco di stereotipi disponibili è determinato dai profili scelti per questo pacchetto e dai pacchetti che lo contengono. Per altre informazioni, vedere [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Come vengono archiviati i pacchetti  
 Quando si crea un nuovo pacchetto, un nuovo **UML** file viene creato nel **ModelDefinition** cartella del progetto. Il modello radice, che è anche un pacchetto, verrà anche archiviato in un **UML** file.  
  
 Inoltre, ogni diagramma viene archiviato in due file, uno che rappresenta le forme del diagramma, e un **layout** file che registra le posizioni delle forme.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)   
 [Gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md)



