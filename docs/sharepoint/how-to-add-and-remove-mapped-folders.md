---
title: 'Procedura: Aggiungere e rimuovere cartelle mappate | Microsoft Docs'
description: Aggiungere e rimuovere cartelle mappate a un progetto in SharePoint.  Modificare il percorso di distribuzione di una cartella mappata. Rinominare o rimuovere le cartelle mappate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112430"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Procedura: aggiungere e rimuovere cartelle mappate

  Alcune cartelle di uso comune in SharePoint, ad esempio immagini e layout, sono molto incorporate nella gerarchia di file. È possibile eseguire il mapping di queste cartelle in un progetto SharePoint per accedervi più facilmente. Le cartelle mappate sono cartelle nel progetto SharePoint che corrispondono al percorso fisico dei file nell'installazione di SharePoint Server.

 Quando si distribuisce un'applicazione SharePoint, il contenuto della cartella mappata e di tutte le relative sottocartelle viene copiato dal pacchetto della soluzione (con estensione wsp) nel server che esegue SharePoint nel percorso specificato nell'albero di cartelle di SharePoint. Questo percorso è determinato dalla **proprietà Percorso** di distribuzione impostata per la cartella mappata. Tutte le sottocartelle nella cartella mappata sono relative **al percorso di** distribuzione della cartella mappata. Si noti che **la proprietà Percorso distribuzione,** non il nome della cartella mappata, determina dove vengono distribuiti gli elementi.
È possibile aggiungere cartelle mappate a un progetto usando i comandi sulla barra dei menu o il menu di scelta rapida per il progetto. È possibile usare i comandi Aggiungi cartella mappata **"Immagini"** di SharePoint e Aggiungi cartella **"Layout"** di SharePoint per aggiungere le cartelle mappate usate più di frequente. È possibile eseguire il mapping di qualsiasi altra cartella di SharePoint disponibile al progetto usando il comando Aggiungi cartella mappata **SharePoint** del menu di scelta rapida e quindi specificando le cartelle nella finestra di dialogo Aggiungi cartella mappata **SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Aggiungere cartelle mappate a un progetto

 La procedura seguente descrive come aggiungere due cartelle mappate a un progetto web part visivo. Per iniziare, creare un progetto web part visivo.

## <a name="to-add-mapped-folders-to-a-project"></a>Per aggiungere cartelle mappate a un progetto

1. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **progetto**.
::: moniker range="=vs-2017"
2. Nella finestra **di dialogo** Nuovo progetto espandere il nodo **Visual Basic** o **Visual C#,** espandere il **nodo Office/SharePoint** e quindi scegliere il **nodo Soluzioni SharePoint.**

3. Nell'elenco dei modelli di progetto scegliere il modello **Di SharePoint 2013 Visual Web Part.**

4. Nella casella **Nome** immettere **TestProject1** e quindi scegliere **OK.**
::: moniker-end
::: moniker range=">=vs-2019"
2. Nella finestra **di dialogo Crea un nuovo** progetto selezionare la web part Visual *SharePoint** per la versione specifica di SharePoint installata. Ad esempio, se si ha l'installazione di SharePoint 2019, selezionare il modello **Di SharePoint 2019 Visual Web Part.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Nella casella **Nome** immettere **TestProject1**
4. Scegliere quindi il **pulsante** Crea.
::: moniker-end

5. Nella **Personalizzazione guidata SharePoint** scegliere il **pulsante Fine** per mantenere le impostazioni predefinite.

6. In **Esplora soluzioni** scegliere il nodo del progetto e quindi nella barra dei menu scegliere Progetto Aggiungi cartella mappata  >  **"Immagini" di SharePoint.**

     Una cartella denominata **Images** viene visualizzata nel progetto e contiene una sottocartella denominata TestProject1. Questa cartella mappata conterrà le immagini per il progetto web part visivo.

7. In **Esplora soluzioni** scegliere il nodo del progetto e quindi, sulla barra dei menu, scegliere Progetto Aggiungi cartella mappata SharePoint per visualizzare la finestra di dialogo Aggiungi cartella mappata  >   **SharePoint.**

8. Nella visualizzazione albero delle cartelle disponibili per il mapping scegliere la **cartella Risorse** e quindi fare clic sul **pulsante OK.**

     Nel progetto viene visualizzata una cartella denominata **Risorse.** Questa cartella può archiviare elementi come file di risorse di tipo stringa. Le sottocartelle possono essere utili per organizzare il contenuto di una cartella mappata, ma non vengono create automaticamente quando si aggiunge una cartella mappata usando il comando Aggiungi cartella mappata **SharePoint.** Per aggiungere una sottocartella, scegliere la **cartella Risorse** e quindi nella barra dei menu scegliere **Progetto**  >  **nuova cartella**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modificare il percorso di distribuzione di una cartella mappata

 Per impostazione predefinita, le cartelle mappate vengono aggiunte a percorsi specifici relativi al percorso di installazione radice di SharePoint, indicato \<SharePointRoot> dal token. È tuttavia possibile modificare questo percorso modificando la **proprietà Percorso di** distribuzione della cartella mappata. Ogni cartella mappata ha la propria **proprietà Percorso di** distribuzione.

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Per modificare il percorso di distribuzione di una cartella mappata

1. Nel progetto creato in precedenza scegliere una cartella mappata.

2. Nella finestra **Proprietà** scegliere i puntini di sospensione (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) nella proprietà Percorso **distribuzione** .

3. Nella finestra **di dialogo Aggiungi cartella mappata SharePoint** passare alla cartella a cui si vuole puntare la cartella mappata.

4. Scegliere il nodo e quindi fare clic sul **pulsante OK.**

## <a name="rename-or-remove-mapped-folders"></a>Rinominare o rimuovere cartelle mappate

### <a name="to-rename-or-remove-a-mapped-folder"></a>Per rinominare o rimuovere una cartella mappata

1. Nel progetto creato in precedenza scegliere una cartella mappata.

2. Per rinominare la cartella mappata, aprire il menu di scelta rapida, scegliere **Rinomina,** immettere il nuovo nome e quindi premere INVIO.

     In alternativa, è possibile scegliere la cartella mappata che  si vuole rinominare, aprire la finestra Proprietà e quindi impostare il valore della proprietà **Nome** cartella sul nuovo nome.

3. Per rimuovere una cartella mappata dal progetto, aprire il relativo menu di scelta rapida, scegliere Elimina **e** quindi fare clic sul **pulsante OK** nella finestra di dialogo per confermare la rimozione.

## <a name="see-also"></a>Vedi anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
