---
title: Informazioni sull'interfaccia utente degli strumenti di linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a814e3d07c2e51a8f946ae9a7b6eff03ea3c2e01
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859237"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Informazioni sull'interfaccia utente degli strumenti di linguaggio specifico di dominio
Quando si apre una soluzione Domain-Specific Language Tools (strumenti DSL) in Visual Studio, l'interfaccia utente sarà simile all'immagine seguente.

 ![Progettazione DSL](../modeling/media/dsl_designer.png)

 Nella tabella seguente viene illustrato come vengono usate le parti dell'interfaccia utente.

|**Elemento**|**Definizione**|
|-----------------|--------------------|
|Diagramma|Il diagramma mostra il modello di dominio.<br /><br /> Il diagramma presenta due lati. Lato "uno" definisce i tipi degli elementi nei modelli. L'altro lato definisce come i modelli verranno visualizzato sullo schermo.|
|Casella degli strumenti|Trascinare gli strumenti dalla casella degli strumenti per aggiungere classi di dominio e definire i tipi al diagramma. Per aggiungere mappe delle forme, connettori e relazioni, fare clic sullo strumento, quindi fare clic sul nodo di origine nel diagramma, quindi il nodo di destinazione.|
|Esplora DSL|**Esplora DSL** viene visualizzato quando una definizione DSL è la finestra attiva. Viene illustrato il linguaggio DSL come una struttura ad albero. DSL Explorer consente di modificare le funzionalità del modello che non vengono visualizzate nel diagramma. Ad esempio, è possibile aggiungere gli elementi della casella degli strumenti e attivare il processo di convalida usando il **DSL Explorer**.|
|Finestra Dettagli DSL|Il **dettagli DSL** finestra Mostra le proprietà del dominio gli elementi del modello che consentono di controllare come vengono visualizzati gli elementi e come gli elementi vengono copiati ed eliminati.<br /><br /> -Per impostazione predefinita, il **dettagli DSL** accanto a verrà visualizzata la finestra di **elenco errori** e **Output** windows.|

## <a name="the-domain-model-diagram"></a>Il diagramma del modello di dominio
 Il diagramma del modello di dominio è suddivisa in due parti. Un lato del diagramma illustra gli elementi e relazioni nel modello. Viene illustrato l'altro lato come il modello deve essere visualizzato e include le forme che consentono di visualizzare gli elementi e le proprietà del diagramma del modello. Nell'immagine seguente mostra gli elementi del diagramma.

 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png)

 Nella tabella seguente illustra alcuni degli elementi del diagramma del modello di dominio.

|**Termine**|**Definizione**|
|--------------|--------------------|
|Classe di dominio|Classi di dominio sono i tipi di elementi nei modelli.<br /><br /> Una classe di dominio può contenere più di una volta in un diagramma, se si tratta della destinazione di più di una relazione.<br /><br /> Per aggiungere una classe di dominio, trascinare lo strumento di classe di dominio dal **casella degli strumenti** per il **Classes and Relationships** lato del diagramma.|
|Relazione di dominio|Relazioni di dominio sono i tipi di collegamenti tra elementi nei modelli.<br /><br /> Un' *relazione di incorporamento* indica che l'elemento di destinazione è di proprietà o contenuto nell'elemento di origine e viene visualizzato come una linea continua. Ogni elemento in un modello deve essere la destinazione di una relazione di incorporamento, in modo che il modello costituisce una struttura ad albero. Oggetto *fanno riferimento a relazione* indica un collegamento tra elementi del modello generale e viene visualizzato come una linea tratteggiata. Qualsiasi elemento può avere qualsiasi numero di collegamenti di riferimento.<br /><br /> Creare una relazione facendo clic sullo strumento il **casella degli strumenti**, scegliendo la classe di dominio di origine e quindi scegliendo la classe di destinazione.|
|Forme e connettori|Forme specificano come gli elementi del modello devono essere visualizzati in un diagramma DSL., connettori di specificare le righe in un diagramma DSL che può essere utilizzato per visualizzare le relazioni.<br /><br /> Per creare una forma o connettore, trascinare lo strumento per la **Diagram Elements** lato del diagramma.|
|Mappe delle forme|Una mappa della forma viene visualizzata come una riga nel diagramma del modello di dominio, una forma di collegamento alla classe di dominio che viene visualizzato, o un connettore per la relazione di dominio che viene visualizzato.|

## <a name="see-also"></a>Vedere anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
- [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)