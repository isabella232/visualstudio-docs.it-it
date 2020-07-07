---
title: 'Procedura: aggiungere e rimuovere cartelle mappate | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80fbd3e18b8d440eae2873c73013ad7468073640
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014650"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Procedura: aggiungere e rimuovere cartelle mappate
  Alcune cartelle di uso comune in SharePoint, ad esempio immagini e layout, sono profondamente incorporate nella gerarchia dei file. È possibile eseguire il mapping di queste cartelle in un progetto SharePoint per accedervi più facilmente. Le cartelle mappate sono cartelle del progetto SharePoint che corrispondono alla posizione fisica dei file nell'installazione di SharePoint Server.

 Quando si distribuisce un'applicazione SharePoint, il contenuto della cartella mappata e di tutte le relative sottocartelle viene copiato dal pacchetto della soluzione (con estensione wsp) nel server che esegue SharePoint nel percorso specificato nell'albero delle cartelle di SharePoint. Questo percorso è determinato dalla proprietà del **percorso di distribuzione** impostata per la cartella mappata. Tutte le sottocartelle nella cartella mappata sono relative al **percorso di distribuzione** della cartella mappata. Si noti che la proprietà **percorso di distribuzione** , non il nome della cartella mappata, determina la posizione in cui vengono distribuiti gli elementi.
Per aggiungere cartelle mappate a un progetto, è possibile utilizzare i comandi della barra dei menu o il menu di scelta rapida per il progetto. È possibile utilizzare la **cartella mappata "immagini" di SharePoint** e aggiungere i comandi della **cartella "Layouts" di SharePoint** per aggiungere le cartelle mappate utilizzate più spesso. Per eseguire il mapping di qualsiasi altra cartella di SharePoint disponibile al progetto, è possibile utilizzare il comando **Aggiungi cartella mappata di SharePoint** dal menu di scelta rapida e quindi specificare le cartelle nella finestra di dialogo **Aggiungi cartella mappata di SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Aggiungere cartelle mappate a un progetto
 Nella procedura riportata di seguito viene descritto come aggiungere due cartelle mappate a un progetto Web part visiva. Per iniziare, creare un progetto Web part visiva.

#### <a name="to-add-mapped-folders-to-a-project"></a>Per aggiungere cartelle mappate a un progetto

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **Visual Basic** o **Visual C#** , espandere il nodo **Office/SharePoint** , quindi scegliere il nodo soluzioni di **SharePoint** .

3. Nell'elenco dei modelli di progetto scegliere il modello **Web part visiva di SharePoint 2013** .

4. Nella casella **nome** immettere **TestProject1**, quindi scegliere il pulsante **OK** .

5. In **personalizzazione guidata SharePoint**scegliere il pulsante **fine** per mantenere le impostazioni predefinite.

6. In **Esplora soluzioni**scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi cartella mappata di SharePoint "immagini"**.

     Nel progetto viene visualizzata una cartella denominata **Immagini** che contiene una sottocartella denominata TestProject1. Questa cartella mappata conterrà le immagini per il progetto Web part visiva.

7. In **Esplora soluzioni**scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi cartella mappata di SharePoint** per visualizzare la finestra di dialogo **Aggiungi cartella mappata di SharePoint** .

8. Nella visualizzazione albero delle cartelle disponibili per il mapping scegliere la cartella **risorse** , quindi scegliere il pulsante **OK** .

     Nel progetto viene visualizzata una cartella denominata **risorse** . Questa cartella può archiviare elementi, ad esempio file di risorse stringa. Le sottocartelle possono essere utili per organizzare il contenuto di una cartella mappata, ma non vengono create automaticamente quando si aggiunge una cartella mappata tramite il comando **Aggiungi cartella mappata di SharePoint** . Per aggiungere una sottocartella, scegliere la cartella **risorse** , quindi nella barra dei menu scegliere **progetto**  >  **nuova cartella**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modificare il percorso di distribuzione di una cartella mappata
 Per impostazione predefinita, le cartelle mappate vengono aggiunte a percorsi specifici rispetto al percorso di installazione radice di SharePoint, che il token \<SharePointRoot> indica. Tuttavia, è possibile modificare questo percorso modificando la proprietà **percorso di distribuzione** della cartella mappata. Ogni cartella mappata ha una propria proprietà del **percorso di distribuzione** .

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Per modificare il percorso di distribuzione di una cartella mappata

1. Nel progetto creato in precedenza, scegliere una cartella mappata.

2. Nella finestra **Proprietà** scegliere il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) nella proprietà **percorso di distribuzione** .

3. Nella finestra di dialogo **Aggiungi cartella mappata di SharePoint** individuare la cartella a cui si desidera puntare la cartella mappata.

4. Scegliere il nodo, quindi scegliere il pulsante **OK** .

## <a name="rename-or-remove-mapped-folders"></a>Rinominare o rimuovere cartelle mappate

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Per rinominare o rimuovere una cartella mappata

1. Nel progetto creato in precedenza, scegliere una cartella mappata.

2. Per rinominare la cartella mappata, aprire il menu di scelta rapida, scegliere **Rinomina**, immettere il nuovo nome, quindi premere il tasto INVIO.

     In alternativa, è possibile scegliere la cartella mappata che si desidera rinominare, aprire la finestra **Proprietà** , quindi impostare il valore della proprietà **nome cartella** sul nuovo nome.

3. Per rimuovere una cartella mappata dal progetto, aprire il menu di scelta rapida, scegliere **Elimina**, quindi fare clic sul pulsante **OK** nella finestra di dialogo per confermare la rimozione.

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
