---
title: Esplorazione di connessioni di SharePoint tramite Esplora Server | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9f64e2cebf267e9be1773b37a5827c876961a0d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609527"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Esplorare le connessioni di SharePoint tramite Esplora Server
  È ora possibile esplorare le connessioni di SharePoint locali nel **Esplora Server**. Utilizzando questa tecnica, è possibile navigare attraverso i componenti di un sito di SharePoint nel sistema. Componenti del sito di SharePoint, ad esempio le definizioni elenco e tipi di contenuto, vengono visualizzati in un nodo denominato **connessioni di SharePoint** nella visualizzazione struttura ad albero del **Esplora Server**. Per visualizzare **Esplora Server**, nella barra dei menu, scegliere **View** > **Esplora Server**. Oltre a visualizzare i componenti del sito di SharePoint, è possibile rimuovere gli elementi, visualizzare le relative proprietà o aggiornare la visualizzazione albero usando i comandi del menu di scelta rapida.

> [!IMPORTANT]
>  Per esplorare un sito di SharePoint, è necessario essere un amministratore della raccolta siti di SharePoint ed eseguire Visual Studio come amministratore del computer locale. In caso contrario, il sito verrà visualizzato nella **Esplora Server**, ma non è possibile espandere il nodo. Per verificare se si è un amministratore della raccolta siti, aprire il sito in un web browser, aprire il **Azioni sito** menu, scegliere **autorizzazioni sito**e quindi scegliere il **autorizzazioni: Sito del team** pagina, scegliere il **Site Collection Administrators** comando il **Gestisci** gruppo sulla barra multifunzione. Il nome verrà visualizzato nella casella di testo se sei un amministratore della raccolta siti. Se il **Site Collection Administrators** comando non viene visualizzato nel gruppo di gestione sulla barra multifunzione e non si è un amministratore per la raccolta siti, è necessario ottenere le autorizzazioni appropriate dall'amministratore del sito.

## <a name="server-explorer-nodes"></a>Nodi di Esplora server
 Ogni componente di un sito di SharePoint è rappresentato da un nodo nel **Esplora Server** nella visualizzazione ad albero **connessioni di SharePoint**. Ad esempio, i siti di SharePoint predefinito includono un tipo di contenuto definito discussione che rappresenta un tipo di discussione su cui vengono visualizzati nei **discussioni** pagina del sito di SharePoint. Il tipo di contenuto di discussione contiene diversi campi. Per visualizzare questi campi nei **Esplora Server**, espandere il **ContentTypes** nodo, quindi il **discussione** nodo. Sono in diversi nodi campo, ad esempio corpo, l'oggetto di discussione e Title.

## <a name="node-shortcut-menu-commands"></a>Comandi di menu di scelta rapida nodo
 Ogni nodo dispone di un menu di scelta rapida accessibile facendo clic sul nodo o scegliendolo e quindi scegliere il **Shift**+**F10** chiavi. I comandi di nodo possono includere quanto segue:

|Nome comando|Descrizione|
|------------------|-----------------|
|Aggiorna|Aggiorna la visualizzazione albero per visualizzare eventuali modifiche che possono essersi verificati dall'ultima volta che il nodo è stato visualizzato.|
|Eliminare|Rimuove il nodo selezionato nella visualizzazione albero. **Nota:**  Questo comando è abilitato solo su connessioni di SharePoint elencate sotto la **connessioni di SharePoint** nodo.|
|Proprietà|Visualizza le proprietà disponibili per il nodo selezionato nel **proprietà** finestra. Le proprietà sono di sola lettura e non tutti i nodi dispongono di proprietà associato.|
|Aggiungi connessione|Consente di specificare un sito di SharePoint che si desidera passare. Disponibile nel **connessioni di SharePoint** nodo e nodi dei siti secondari.|
|Visualizza nel browser|Visualizza l'elenco selezionato nel Web browser. Questo comando è disponibile in alcune elenchi sotto il **sono elencati** contenute nel nodo **elenchi e raccolte**.|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Aggiungere o rimuovere connessioni di SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Vengono descritti i passaggi necessari per l'aggiunta di un nuovo sito di SharePoint per il **connessioni di SharePoint** nodo **Esplora Server**.|

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
