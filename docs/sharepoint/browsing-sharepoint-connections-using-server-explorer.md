---
title: Esplorazione SharePoint connessioni tramite Esplora server | Microsoft Docs
description: Esplorare SharePoint connessioni tramite Esplora server. Informazioni sui Esplora server e i comandi del menu di scelta rapida dei nodi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 15b47ac8286edda99ed6115f3c6eca1aa36edcbe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060271"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Esplorare SharePoint connessioni tramite Esplora server
  È ora possibile esplorare le connessioni SharePoint locali in **Esplora server**. Utilizzando questa tecnica, è possibile navigare attraverso i componenti di un sito di SharePoint nel sistema. SharePoint componenti del sito, ad esempio definizioni di elenco e tipi di contenuto, vengono visualizzati in un nodo denominato **SharePoint Connections** nella visualizzazione albero **di Esplora server**. Per visualizzare **Esplora server**, sulla barra dei menu scegliere  >  **Visualizza Esplora server**. Oltre a visualizzare i componenti del sito di SharePoint, è possibile rimuovere gli elementi, visualizzare le relative proprietà o aggiornare la visualizzazione albero usando i comandi del menu di scelta rapida.

> [!IMPORTANT]
> Per esplorare un sito di SharePoint, è necessario essere un amministratore della raccolta siti di SharePoint ed eseguire Visual Studio come amministratore del computer locale. In caso contrario, il sito viene **visualizzato Esplora server**, ma non è possibile espanderne il nodo. Per verificare se si è un amministratore della raccolta siti, aprire il sito in un Web browser, aprire il menu Azioni  sito, scegliere  Autorizzazioni sito **e** quindi nella pagina  **Autorizzazioni: Sito del team** scegliere il comando Amministratori raccolta siti dal gruppo Gestisci sulla barra multifunzione. Il nome verrà visualizzato nella casella di testo se si è un amministratore della raccolta siti. Se il **comando** Amministratori raccolta siti non viene visualizzato nel gruppo Gestisci sulla barra multifunzione, non si è un amministratore della raccolta siti ed è necessario ottenere le autorizzazioni appropriate dall'amministratore del sito.

## <a name="server-explorer-nodes"></a>Esplora server nodi
 Ogni componente di un SharePoint sito è rappresentato da un nodo nella visualizzazione Esplora server **albero** in **SharePoint Connessioni**. Ad esempio, i SharePoint predefiniti includono un tipo di contenuto denominato Discussione,  che rappresenta un tipo di discussione visualizzato nella pagina Discussioni del SharePoint sito. Il tipo di contenuto Discussione contiene diversi campi. Per visualizzare questi campi in **Esplora server**, espandere il **nodo ContentTypes** e quindi il **nodo Discussione.** Al suo interno sono presenti diversi nodi di campo, ad esempio Corpo, Oggetto discussione e Titolo.

## <a name="node-shortcut-menu-commands"></a>Comandi del menu di scelta rapida del nodo
 Ogni nodo ha un menu di scelta rapida a cui si accede facendo clic con il pulsante destro del mouse sul nodo o scegliendolo e quindi premendo + **MAIUSC+F10.** I comandi del nodo possono includere quanto segue:

|Nome comando|Descrizione|
|------------------|-----------------|
|Aggiorna|Aggiorna la visualizzazione albero in modo da riflettere tutte le modifiche che potrebbero essere state apportate dopo l'ultima visualizzazione del nodo.|
|Elimina|Rimuove il nodo selezionato dalla visualizzazione albero. **Nota:**  Questo comando è abilitato solo nelle connessioni SharePoint elencate nel nodo SharePoint **connessioni.**|
|Proprietà|Visualizza le proprietà disponibili per il nodo selezionato nella **finestra** Proprietà. Le proprietà sono tutte di sola lettura e non a ogni nodo sono associate proprietà.|
|Aggiungi connessione|Consente di specificare un SharePoint da esplorare. Disponibile nel nodo **SharePoint connessioni** e nei nodi del sito secondario.|
|Visualizza nel browser|Visualizza l'elenco selezionato nel Web browser. Questo comando è disponibile in alcuni elenchi nel **nodo Elenchi** contenuto in Elenchi **e librerie**.|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Aggiungere o rimuovere SharePoint connessioni](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Vengono descritti i passaggi necessari per l'aggiunta di un nuovo SharePoint al nodo SharePoint **Connections** in **Esplora server**.|

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
