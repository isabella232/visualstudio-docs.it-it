---
title: 'Diagrammi livello: riferimento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 448a74b739bbb339d5f3b3e56c0ba59072994109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850622"
---
# <a name="layer-diagrams-reference"></a>Diagrammi livello: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile usare un *diagramma livello* per visualizzare l'architettura logica di alto livello del sistema. Un diagramma livello organizza gli elementi fisici del sistema in gruppi logici astratti denominati *livelli*. Questi livelli descrivono le attività principali eseguite dagli elementi o i componenti principali del sistema. Ogni livello può anche contenere livelli annidati che descrivono attività più dettagliate.

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 È possibile specificare le dipendenze desiderate o esistenti tra i livelli. Queste dipendenze, rappresentate come frecce, indicano i livelli che possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Organizzando il sistema in livelli che descrivono funzioni e ruoli distinti, un diagramma livello può semplificare la comprensione, il riutilizzo e la manutenzione del codice.

 Usare un diagramma livello per eseguire le attività seguenti:

- Comunicare l'architettura logica esistente o desiderata del sistema.

- Individuare i conflitti tra il codice esistente e l'architettura desiderata.

- Visualizzare l'impatto delle modifiche nell'architettura desiderata in caso di refactoring, aggiornamento o evoluzione del sistema.

- Rafforzare l'architettura desiderata durante lo sviluppo e la manutenzione del codice includendo la convalida con le operazioni di archiviazione e compilazione.

  Questo argomento descrive gli elementi che è possibile usare in un diagramma livello. Per informazioni più dettagliate su come creare e creare diagrammi livello, vedere [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md). Per ulteriori informazioni sui modelli di livello, visitare il [sito modelli & procedure](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home).

## <a name="reading-layer-diagrams"></a>Lettura di diagrammi livello
 ![Elementi dei diagrammi dei livelli](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 La tabella seguente descrive gli elementi che è possibile usare in un diagramma livello.

|**Con forme**|**elemento**|**Descrizione**|
|---------------|-----------------|---------------------|
|1|**Livello**|Gruppo logico di elementi fisici nel sistema. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via.<br /><br /> Per visualizzare gli elementi collegati a un livello, aprire il menu di scelta rapida per il livello, quindi scegliere **Visualizza collegamenti** per aprire **Esplora livello**.<br /><br /> Per altre informazioni, vedere [Esplora livello](#Explorer).<br /><br /> -   **Dipendenze dello spazio dei nomi** non consentiti: specifica che gli artefatti associati a questo livello non possono dipendere dagli spazi dei nomi specificati.<br />-   **Forbidden Namespaces** : specifica che gli artefatti associati a questo livello non devono appartenere agli spazi dei nomi specificati.<br />-   **Spazi dei nomi obbligatori** : specifica che gli elementi associati a questo livello devono appartenere a uno degli spazi dei nomi specificati.|
|2|**Dipendenza**|Indica che un livello può usare la funzionalità di un altro livello, ma non viceversa.<br /><br /> -   **Direction** : specifica la direzione della dipendenza.|
|3|**Dipendenza bidirezionale**|Indica che un livello può usare la funzionalità di un altro livello e viceversa.<br /><br /> -   **Direction** : specifica la direzione della dipendenza.|
|4|**Commento**|Usato per aggiungere note generali al diagramma o elementi nel diagramma.|
|5|**Collegamento commento**|Usato per collegare commenti a elementi nel diagramma.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Esplora livello
 È possibile collegare ogni livello a elementi nella soluzione, come progetti, classi, spazi dei nomi, file di progetto e altre parti del software. Il numero specificato su un livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretare il numero di elementi in un livello, ricordare quanto segue:

- Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.

   Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.

- Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.

  Per altre informazioni sul collegamento di livelli ed elementi, vedere:

- [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)

- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Per esaminare gli elementi collegati

- Nel diagramma livello aprire il menu di scelta rapida per uno o più livelli, quindi scegliere **Visualizza collegamenti**.

     Viene aperto **Esplora livello** che Mostra gli elementi collegati ai livelli selezionati. In **Esplora livello** è presente una colonna che mostra ognuna delle proprietà dei collegamenti agli elementi.

    > [!NOTE]
    > Se non è possibile visualizzare tutte queste proprietà, espandere la finestra **Esplora livello** .

    |**Colonna in Esplora livello**|**Descrizione**|
    |----------------------------------|---------------------|
    |**Categories** (Categorie)|Tipo di elemento, ad esempio una classe, uno spazio dei nomi, un file di origine e così via|
    |**Livello**|Livello collegato all'elemento|
    |**Convalida supporti**|Se **true**, il processo di convalida dei livelli può verificare che il progetto sia conforme alle dipendenze da o verso questo elemento.<br /><br /> Se **false**, il collegamento non partecipa al processo di convalida dei livelli.<br /><br /> Per altre informazioni, vedere [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md).|
    |**Identificatore**|Riferimento all'elemento collegato|

## <a name="see-also"></a>Vedere anche
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
