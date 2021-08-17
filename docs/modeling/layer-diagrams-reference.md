---
title: Informazioni di riferimento su diagrammi di dipendenza
description: In questo Visual Studio è possibile usare un diagramma delle dipendenze per visualizzare l'architettura logica di alto livello del sistema.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
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
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b08f2814fc20cf97da0e0c081ea2d8a6d49e0129
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055445"
---
# <a name="dependency-diagrams-reference"></a>Diagrammi delle dipendenze: informazioni di riferimento

In Visual Studio è possibile usare *un* diagramma delle dipendenze per visualizzare l'architettura logica di alto livello del sistema. Un diagramma delle dipendenze organizza gli artefatti fisici nel sistema in gruppi logici astratti denominati *livelli*. Questi livelli descrivono le attività principali eseguite dagli elementi o i componenti principali del sistema. Ogni livello può anche contenere livelli annidati che descrivono attività più dettagliate.

Per informazioni su quali edizioni di Visual Studio questa funzionalità, vedere Supporto dell'edizione per gli strumenti di [architettura e modellazione](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> I diagrammi delle dipendenze per i progetti .NET Core sono supportati a partire Visual Studio 2019 versione 16.2.

È possibile specificare le dipendenze desiderate o esistenti tra i livelli. Queste dipendenze, rappresentate come frecce, indicano i livelli che possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Organizzando il sistema in livelli che descrivono ruoli e funzioni distinti, un diagramma delle dipendenze può semplificare la comprensione, il riutilizzo e la gestione del codice.

Usare un diagramma delle dipendenze per eseguire le attività seguenti:

- Comunicare l'architettura logica esistente o desiderata del sistema.

- Individuare i conflitti tra il codice esistente e l'architettura desiderata.

- Visualizzare l'impatto delle modifiche nell'architettura desiderata in caso di refactoring, aggiornamento o evoluzione del sistema.

- Rafforzare l'architettura desiderata durante lo sviluppo e la manutenzione del codice includendo la convalida con le operazioni di archiviazione e compilazione.

Questo argomento descrive gli elementi che è possibile usare in un diagramma delle dipendenze. Per informazioni più dettagliate su come creare e disegnare diagrammi delle dipendenze, vedere [Diagrammi delle dipendenze: Linee guida.](../modeling/layer-diagrams-guidelines.md) Per altre informazioni sui modelli di strating, visitare il sito [patterns & Practices](https://archive.codeplex.com/?p=apparch).

## <a name="reading-dependency-diagrams"></a>Lettura dei diagrammi delle dipendenze

![Elementi nei diagrammi delle dipendenze](../modeling/media/uml_layerrefreading.png)

Nella tabella seguente vengono descritti gli elementi che è possibile usare in un diagramma delle dipendenze.

|**Forma**|**elemento**|**Descrizione**|
|-|-|-|
|1|**Livello**|Gruppo logico di elementi fisici nel sistema. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via.<br /><br /> Per visualizzare gli elementi collegati a un livello, aprire il menu di scelta rapida per il livello e quindi scegliere Visualizza collegamenti **per** aprire **Esplora livelli.**<br /><br /> Per altre informazioni, vedere [Esplora livelli](#Explorer).<br /><br /> -   **Dipendenze dello spazio dei nomi non** consentite: specifica che gli elementi associati a questo livello non possono dipendere dagli spazi dei nomi specificati.<br />-   **Spazi dei nomi non consentiti:** specifica che gli elementi associati a questo livello non devono appartenere agli spazi dei nomi specificati.<br />-   **Spazi dei nomi obbligatori:** specifica che gli elementi associati a questo livello devono appartenere a uno degli spazi dei nomi specificati.|
|2|**Dipendenza**|Indica che un livello può usare la funzionalità di un altro livello, ma non viceversa.<br /><br /> -   **Direzione:** specifica la direzione della dipendenza.|
|3|**Dipendenza bidirezionale**|Indica che un livello può usare la funzionalità di un altro livello e viceversa.<br /><br /> -   **Direzione:** specifica la direzione della dipendenza.|
|4|**Commento**|Usato per aggiungere note generali al diagramma o elementi nel diagramma.|
|5|**Collegamento commento**|Usato per collegare commenti a elementi nel diagramma.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Esplora livelli

È possibile collegare ogni livello a elementi nella soluzione, come progetti, classi, spazi dei nomi, file di progetto e altre parti del software. Il numero specificato su un livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretare il numero di elementi in un livello, ricordare quanto segue:

- Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.

     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.

- Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.

Per altre informazioni sul collegamento di livelli ed elementi, vedere:

- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Esaminare gli elementi collegati

Nel diagramma delle dipendenze aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**.

**Verrà aperto Esplora** livelli e verranno visualizzati gli elementi collegati ai livelli selezionati. **Esplora livelli** include una colonna che mostra ognuna delle proprietà dei collegamenti dell'elemento.

> [!NOTE]
> Se non è possibile visualizzare tutte queste proprietà, espandere la **finestra Esplora** livelli.

|**Colonna in Esplora livello**|**Descrizione**|
|-|-|
|**Categorie**|Tipo di elemento, ad esempio una classe, uno spazio dei nomi, un file di origine e così via|
|**Livello**|Livello collegato all'elemento|
|**Convalida supporti**|Se **True,** il processo di convalida del livello può verificare che il progetto sia conforme alle dipendenze da o verso questo elemento.<br /><br /> Se **False,** il collegamento non partecipa al processo di convalida del livello.<br /><br /> Per altre informazioni, vedere [Diagrammi di dipendenza: Linee guida](../modeling/layer-diagrams-guidelines.md).|
|**Identificatore**|Riferimento all'elemento collegato|

## <a name="see-also"></a>Vedi anche

- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
