---
title: 'Procedura: aggiungere e rimuovere cartelle mappate | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe9868a9909dbb78bf510f18584472520948d6f9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757648"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Procedura: aggiungere e rimuovere cartelle mappate
  Alcune cartelle utilizzate comunemente in SharePoint, ad esempio immagini e layout di annidamento nella gerarchia dei file. È possibile eseguire il mapping di queste cartelle in un progetto di SharePoint per accedervi più facilmente. Cartelle mappate sono cartelle nel progetto di SharePoint che corrispondono al percorso fisico dei file nell'installazione di SharePoint Server.  
  
 Quando si distribuisce un'applicazione di SharePoint, il contenuto della cartella mappata e tutte le relative sottocartelle vengono copiate dal pacchetto della soluzione (con estensione wsp) nel server che esegue SharePoint nel percorso specificato nella struttura di cartelle di SharePoint. Questa posizione è determinata dal **percorso di distribuzione** proprietà che è impostato per la cartella mappata. Tutte le sottocartelle della cartella mappata sono relativi alla **percorso di distribuzione** della cartella mappata. Si noti che il **percorso di distribuzione** determina di proprietà, non il nome della cartella mappata, in cui vengono distribuiti elementi.  
 È possibile aggiungere cartelle mappate a un progetto usando i comandi sulla barra dei menu o nel menu di scelta rapida per il progetto. È possibile usare la **cartella mappata "Immagini" Aggiungi SharePoint** e **aggiungere SharePoint "Layout" cartella** comandi per aggiungere quelli mappati cartelle utilizzate più spesso. È possibile eseguire il mapping presenti altre cartelle SharePoint disponibili nel progetto usando il **Aggiungi cartella mappata di SharePoint** comando nel menu di scelta rapida e quindi specificare le cartelle nel **Aggiungi cartella mappata di SharePoint** finestra di dialogo.  
  
## <a name="add-mapped-folders-to-a-project"></a>Aggiungere cartelle mappate a un progetto  
 La procedura seguente descrive come aggiungere due cartelle mappate a un progetto web part visiva. Per iniziare, si crea un progetto web part visiva.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Per aggiungere cartelle mappate a un progetto  
  
1.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere uno il **Visual Basic** o **Visual c#** nodo, espandere il **Office/SharePoint** nodo e quindi Scegliere il **soluzioni SharePoint** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere il **Web Part visiva di SharePoint 2013** modello.  
  
4.  Nel **Name** casella, immettere **TestProject1**e quindi scegliere il **OK** pulsante.  
  
5.  Nel **Personalizzazione guidata SharePoint**, scegliere il **fine** pulsante per mantenere le impostazioni predefinite.  
  
6.  Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **cartella mappata "Immagini" Aggiungi SharePoint**.  
  
     Una cartella denominata **immagini** è presente nel progetto e contiene una sottocartella denominata TestProject1. Questa cartella mappata conterrà le immagini per il progetto web part visiva.  
  
7.  Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi cartella mappata di SharePoint** per visualizzare il  **Aggiungi cartella mappata di SharePoint** nella finestra di dialogo.  
  
8.  Nella visualizzazione albero delle cartelle che sono disponibili per il mapping, scegliere il **le risorse** cartella, quindi scegliere il **OK** pulsante.  
  
     Una cartella denominata **risorse** viene visualizzata nel progetto. Questa cartella può archiviare gli elementi, ad esempio i file di risorse stringa. Possono essere utile per organizzare il contenuto di una cartella mappata nelle sottocartelle, ma vengono create automaticamente quando si aggiunge una cartella mappata con il **Aggiungi cartella mappata di SharePoint** comando. Per aggiungere una sottocartella, scegliere il **le risorse** cartella, quindi nella barra dei menu, scegliere **Project** > **nuova cartella**.  
  
## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modificare il percorso di distribuzione di una cartella mappata  
 Per impostazione predefinita, vengono aggiunti cartelle mappate a posizioni specifiche relativo al percorso di installazione radice di SharePoint, quale il token \<SharePointRoot > denota. Tuttavia, è possibile modificare questo percorso modificando la **percorso di distribuzione** proprietà della cartella mappata. Ogni cartella mappata con il proprio **percorso di distribuzione** proprietà.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Per modificare il percorso di distribuzione di una cartella mappata  
  
1.  Nel progetto creato in precedenza, scegliere una cartella mappata.  
  
2.  Nel **delle proprietà** finestra, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) pulsante la **distribuzione percorso** proprietà.  
  
3.  Nel **Aggiungi cartella mappata di SharePoint** finestra di dialogo, individuare la cartella in cui si desidera che la cartella mappata in modo che punti.  
  
4.  Scegliere il nodo e quindi scegliere il **OK** pulsante.  
  
## <a name="rename-or-remove-mapped-folders"></a>Rinominare o rimuovere cartelle mappate  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Per rinominare o rimuovere una cartella mappata  
  
1.  Nel progetto creato in precedenza, scegliere una cartella mappata.  
  
2.  Per rinominare la cartella mappata, aprire il menu di scelta rapida, scegliere **Rinomina**, immettere il nuovo nome e quindi premere INVIO.  
  
     In alternativa, è possibile scegliere la cartella mappata che si desidera rinominare, aprire il **delle proprietà** finestra e quindi impostare il valore della **nome della cartella** proprietà per il nuovo nome.  
  
3.  Per rimuovere una cartella mappata dal progetto, aprire il menu di scelta rapida, scegliere **eliminare**, quindi scegliere il **OK** pulsante nella finestra di dialogo per confermare la rimozione.  
  
## <a name="see-also"></a>Vedere anche
 [Lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
