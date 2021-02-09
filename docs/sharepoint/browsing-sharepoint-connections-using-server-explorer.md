---
title: Esplorazione delle connessioni di SharePoint tramite Esplora server | Microsoft Docs
description: Esplorazione delle connessioni di SharePoint tramite Esplora server. Informazioni sui nodi Esplora server e sui comandi del menu di scelta rapida del nodo.
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
ms.workload:
- office
ms.openlocfilehash: b188d95e6478e488fc896b0622fb8d145ef2a741
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851608"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Esplorazione delle connessioni di SharePoint tramite Esplora server
  È ora possibile esplorare le connessioni locali di SharePoint in **Esplora server**. Utilizzando questa tecnica, è possibile navigare attraverso i componenti di un sito di SharePoint nel sistema. I componenti del sito di SharePoint, ad esempio le definizioni di elenco e i tipi di contenuto, vengono visualizzati in un nodo denominato **connessioni di SharePoint** nella visualizzazione albero del **Esplora server**. Per visualizzare **Esplora server**, scegliere **Visualizza** Esplora server sulla barra dei menu  >  . Oltre a visualizzare i componenti del sito di SharePoint, è possibile rimuovere gli elementi, visualizzare le relative proprietà o aggiornare la visualizzazione albero usando i comandi del menu di scelta rapida.

> [!IMPORTANT]
> Per esplorare un sito di SharePoint, è necessario essere un amministratore della raccolta siti di SharePoint ed eseguire Visual Studio come amministratore del computer locale. In caso contrario, il sito viene visualizzato in **Esplora server**, ma non è possibile espanderne il nodo. Per verificare se si è un amministratore della raccolta siti, aprire il sito in un Web browser, aprire il menu **Azioni sito** , scegliere **autorizzazioni sito**, quindi, nella pagina **autorizzazioni: sito del team** , scegliere il comando **Amministratori raccolta siti** dal gruppo **Gestisci** sulla barra multifunzione. Il nome verrà visualizzato nella casella di testo se si è un amministratore della raccolta siti. Se il comando **Amministratori raccolta siti** non viene visualizzato nel gruppo Gestisci sulla barra multifunzione, non si è un amministratore della raccolta siti ed è necessario ottenere le autorizzazioni appropriate dall'amministratore del sito.

## <a name="server-explorer-nodes"></a>Nodi Esplora server
 Ogni componente di un sito di SharePoint è rappresentato da un nodo nella visualizzazione ad albero **Esplora server** in **connessioni a SharePoint**. Ad esempio, i siti di SharePoint predefiniti includono un tipo di contenuto denominato discussion, che rappresenta un tipo di discussione visualizzato nella pagina **discussioni** del sito di SharePoint. Il tipo di contenuto della discussione contiene diversi campi. Per visualizzare questi campi in **Esplora server**, espandere il nodo **ContentTypes** , quindi il nodo **Discussion** . Al suo interno si trovano diversi nodi campo, ad esempio corpo, argomento discussione e titolo.

## <a name="node-shortcut-menu-commands"></a>Comandi del menu di scelta rapida del nodo
 Ogni nodo dispone di un menu di scelta rapida a cui è possibile accedere facendo clic con il pulsante destro del mouse sul nodo oppure scegliendo il tasto **MAIUSC** + **F10** . I comandi del nodo possono includere quanto segue:

|Nome comando|Descrizione|
|------------------|-----------------|
|Aggiorna|Aggiorna la visualizzazione albero in modo da riflettere le modifiche che potrebbero essersi verificate dall'ultima visualizzazione del nodo.|
|Elimina|Rimuove il nodo selezionato dalla visualizzazione albero. **Nota:**  Questo comando è abilitato solo nelle connessioni di SharePoint elencate nel nodo **connessioni di SharePoint** .|
|Proprietà|Consente di visualizzare le proprietà disponibili per il nodo selezionato nella finestra **Proprietà** . Tutte le proprietà sono di sola lettura e non tutte le proprietà sono associate a ogni nodo.|
|Aggiungi connessione|Consente di specificare un sito di SharePoint che si desidera esplorare. Disponibile nel nodo **connessioni di SharePoint** e nei nodi del sito secondario.|
|Visualizza nel browser|Consente di visualizzare l'elenco selezionato nel Web browser. Questo comando è disponibile in alcuni elenchi nel nodo **elenchi** contenuto negli **elenchi e nelle raccolte**.|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: aggiungere o rimuovere connessioni di SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Vengono descritti i passaggi necessari per aggiungere un nuovo sito di SharePoint al nodo **connessioni di SharePoint** in **Esplora server**.|

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
