---
title: Informazioni di riferimento sulle API (estendibilità degli strumenti di SharePoint) | Microsoft Docs
description: Esaminare la documentazione di riferimento per l'API per estendere gli strumenti di SharePoint in Visual Studio. Vedere un elenco di spazi dei nomi correlati, ad esempio Microsoft. VisualStudio. SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec07272ede6c957afb43c29342e8479e67d1dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851721"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Riferimento API (estendibilità degli strumenti di SharePoint)
  Questa sezione contiene la documentazione di riferimento sulle API per l'estensione degli strumenti di SharePoint in Visual Studio.

## <a name="in-this-section"></a>Contenuto della sezione
 <xref:Microsoft.VisualStudio.SharePoint>

 Contiene i tipi utilizzati per estendere il sistema del progetto SharePoint. Ad esempio, è possibile estendere i progetti e gli elementi del progetto SharePoint predefiniti oppure crearne di personalizzati.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contiene i tipi che è possibile utilizzare per creare *comandi* personalizzati di SharePoint. Un comando di SharePoint è un metodo che chiama il modello a oggetti server di SharePoint da un'estensione degli strumenti di SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Contiene i tipi utilizzati per estendere il processo di distribuzione per i progetti SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Contiene i tipi utilizzati per estendere i nodi di SharePoint in **Esplora server** o per definire tipi di nodi personalizzati.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Contiene i tipi che è possibile utilizzare per ottenere informazioni sui nodi **Esplora server** predefiniti che rappresentano singoli componenti in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Contiene i tipi utilizzati per accedere alla definizione di una funzionalità in un progetto SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Contiene i tipi utilizzati per accedere alla definizione del pacchetto in un progetto SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Contiene i tipi utilizzati per l'autenticazione e la comunicazione con le applicazioni per SharePoint distribuite su siti remoti di SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Contiene i tipi utilizzati per creare comandi remoti di SharePoint, utilizzati con le applicazioni per SharePoint distribuite su siti remoti di SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Contiene i tipi utilizzati da Visual Studio come attività di compilazione per creare i pacchetti ed eseguire il debug di progetti SharePoint, applicazioni per Office e applicazioni per SharePoint. Questa API supporta l'infrastruttura Office e SharePoint e non può essere utilizzata direttamente dal codice.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Contiene i tipi utilizzati per personalizzare il comportamento della convalida della funzionalità e del pacchetto per un progetto SharePoint.

## <a name="see-also"></a>Vedi anche
- [Riferimento &#40;estensibilità degli strumenti di SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Chiamare nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
