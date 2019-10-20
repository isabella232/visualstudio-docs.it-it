---
title: Collegare un caso di utilizzo a documenti e diagrammi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657646"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Collegare un caso di utilizzo a documenti e diagrammi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile collegare un caso di utilizzo in un diagramma caso di utilizzo a un altro diagramma o documento. Ad esempio, è possibile collegare il caso di utilizzo ai seguenti diagrammi e documenti:

- Un diagramma di sequenza che mostra come raggiungere gli obiettivi del caso di utilizzo usando le interazioni tra gli utenti e il sistema o i relativi componenti principali.

- Un diagramma di attività che mostra le azioni dettagliate eseguite dagli utenti e dal sistema o dai relativi componenti principali durante l'esecuzione del caso di utilizzo.

- Una pagina o un paragrafo OneNote che descrive dettagliatamente il caso di utilizzo.

- Un documento di Word o una presentazione di PowerPoint che descrive dettagliatamente il caso di utilizzo. È possibile tenere questi documenti nella soluzione o in una posizione accessibile al team, ad esempio un sito SharePoint.

  Per collegare un caso di utilizzo a un documento, creare un elemento nel diagramma caso di utilizzo e connettere quest'ultimo all'elemento. Nelle proprietà dell'elemento, impostare il percorso del file dell'altro diagramma o documento. Quando si fa doppio clic sull'elemento, si apre l'altro diagramma o documento.

  Non ci sono limitazioni al numero di elementi che è possibile connettere a un caso di utilizzo. È anche possibile collegare elementi ad altri tipi di elemento in un diagramma caso di utilizzo.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Per aprire un documento associato a un elemento

- Nel diagramma caso di utilizzo, fare doppio clic sulla forma dell'elemento.

     Il documento associato si apre.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Per collegare un caso di utilizzo a un diagramma o a un file nella stessa soluzione

1. Disegnare un diagramma, ad esempio un diagramma di sequenza o di attività, per illustrare uno scenario del caso di utilizzo.

2. Tornare al diagramma caso di utilizzo.

3. Trascinare il diagramma o il file da Esplora soluzioni in una parte vuota del diagramma caso di utilizzo.

4. Connettersi dall'artefatto al caso di utilizzo usando una **dipendenza**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Per eseguire il collegamento a un file di soluzione, ad esempio un documento di Word o una presentazione di PowerPoint

1. Aggiungere il documento alla soluzione.

    1. Spostare il documento di Word nella stessa cartella di Windows della soluzione.

    2. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi**, quindi fare clic su **elemento esistente**.

    3. Passare al documento di Word e fare clic su **Aggiungi**.

         Il documento di Word viene visualizzato in una cartella della soluzione in Esplora soluzioni.

2. Trascinare il documento di Word da Esplora soluzioni in una parte vuota del diagramma caso di utilizzo.

     Viene visualizzato un nuovo elemento.

3. Connettersi dall'artefatto al caso di utilizzo usando una **dipendenza**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Per eseguire il collegamento a un documento condiviso, un elemento OneNote o una pagina Web

1. Ottenere l'URL dell'elemento condiviso. Questo può essere, ad esempio, un percorso di file di rete che inizia con ' \\ \\' o una pagina Web o un URL di SharePoint che inizia con ' http://' o un collegamento a una sezione, pagina o paragrafo di OneNote con inizio ' OneNote:'.

2. Nella casella degli strumenti fare clic su **artefatto** , quindi fare clic nel diagramma caso di utilizzo.

3. Con il nuovo elemento selezionato, digitare o incollare l'URL nella proprietà **collegamento ipertestuale** .

    > [!NOTE]
    > Se si desidera fornire un percorso di file, è consigliabile scegliere un file in un'area di lavoro comune (a partire da' \\ \\') o un file all'interno della soluzione di Visual Studio. In questo modo, il percorso file resterà valido nel computer di un altro membro del team oppure in caso la soluzione venga spostata. Per aggiungere un documento, ad esempio un documento di Word, alla soluzione, fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni, scegliere **Aggiungi** , quindi fare clic su **elemento esistente**.

## <a name="see-also"></a>Vedere anche
 [Diagrammi caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md) [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md) [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md) [creare modelli per l'app](../modeling/create-models-for-your-app.md)
