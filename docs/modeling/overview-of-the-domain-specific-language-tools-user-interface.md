---
title: Panoramica dell'interfaccia utente Domain-Specific Language Tools
description: Viene fornita una panoramica dell'interfaccia utente di una soluzione di strumenti del linguaggio specifico di dominio in Visual Studio.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 4fe826b373ba2ee468bfe511392eb5564234dc68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390958"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Informazioni sull'interfaccia utente degli strumenti di linguaggio specifico di dominio
Quando si apre per la prima volta una soluzione Domain-Specific Language Tools (strumenti DSL) in Visual Studio, l'interfaccia utente sarà simile all'immagine seguente.

 ![Progettazione DSL](../modeling/media/dsl_designer.png)

 La tabella seguente spiega come vengono usate le diverse parti dell'interfaccia utente.

|**elemento**|**Definition**|
|-|-|
|Diagramma|Il diagramma visualizza il modello di dominio.<br /><br /> Il diagramma presenta due lati. Un lato definisce i tipi degli elementi nei modelli. L'altro lato definisce il modo in cui i modelli verranno visualizzati sullo schermo.|
|Casella degli strumenti|Trascinare gli strumenti dalla casella degli strumenti per aggiungere classi di dominio e tipi di forma al diagramma. Per aggiungere relazioni, connettori e mapping di forme, fare clic sullo strumento, sul nodo di origine sul diagramma e quindi sul nodo di destinazione.|
|Esplora DSL|La **finestra di esplorazione DSL** viene visualizzata quando la finestra attiva corrisponde a una definizione DSL. Il linguaggio DSL viene visualizzato sotto forma di albero. La finestra di esplorazione DSL consente di modificare le caratteristiche del modello non visualizzate nel diagramma. È ad esempio possibile usare la **finestra di esplorazione DSL** per aggiungere elementi della casella degli strumenti e attivare il processo di convalida.|
|Finestra Dettagli DSL|La finestra **Dettagli DSL** visualizza le proprietà degli elementi del modello di dominio che consentono di controllare la modalità di visualizzazione degli elementi, nonché la modalità di copia ed eliminazione di questi.<br /><br /> - Per impostazione predefinita, la finestra **Dettagli DSL** è visualizzata accanto alle finestre **Elenco errori** e **Output**.|

## <a name="the-domain-model-diagram"></a>Diagramma del modello di dominio
 Il diagramma del modello di dominio è diviso in due parti. Un lato del diagramma illustra gli elementi e le relazioni nel modello. L'altro lato, che illustra come deve essere visualizzato il modello, include le forme usate per visualizzare gli elementi e le proprietà del diagramma del modello. L'immagine seguente illustra gli elementi del diagramma.

 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png)

 La tabella seguente spiega alcuni elementi del diagramma del modello di dominio.

|**Termine**|**Definizione**|
|-|-|
|Classe di dominio|Le classi di dominio sono i tipi degli elementi nei modelli.<br /><br /> Una classe di dominio può comparire più volte in un diagramma, se è la destinazione di più relazioni.<br /><br /> Per aggiungere una classe di dominio, trascinare lo strumento Classe di dominio dalla **Casella degli strumenti** al lato **Classi e relazioni** del diagramma.|
|Relazione di dominio|Le relazioni di dominio sono i tipi dei collegamenti tra gli elementi nei modelli.<br /><br /> Una *relazione di incorporamento* indica che l'elemento di destinazione è di proprietà dell'elemento di origine o è contenuto all'interno di esso. Tale relazione viene visualizzata con una linea continua. Ogni elemento in un modello deve essere la destinazione di una relazione di incorporamento, in modo che il modello abbia l'aspetto di un albero. Una *relazione di riferimento* indica un collegamento generale tra elementi del modello generale e viene visualizzata con una linea tratteggiata. Tutti gli elementi possono avere un numero qualsiasi di collegamenti di riferimento.<br /><br /> Creare una relazione facendo clic sullo strumento nella **Casella degli strumenti**, sulla classe di dominio di origine e quindi sulla classe di destinazione.|
|Forme e connettori|Le forme specificano in che modo gli elementi del modello devono essere visualizzati in un diagramma DSL. I connettori specificano le linee che è possibile usare in un diagramma DSL per visualizzare le relazioni.<br /><br /> Per creare una forma o un connettore, trascinare lo strumento sul lato **Elementi diagramma** del diagramma.|
|Mappe delle forme|Un mapping di forme ha l'aspetto di una linea che, nel diagramma del modello di dominio, collega una forma alla classe di dominio che visualizza, o un connettore alla relazione di dominio che visualizza.|

## <a name="see-also"></a>Vedi anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
- [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)