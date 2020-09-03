---
title: Inventario degli ambienti di pre-produzione | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: Informazioni sulla responsabilità degli amministratori di eseguire gli inventari di pre-produzione
ms.openlocfilehash: dc307d9d2f83666c6648a35b3e28a81da2de5c38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80232767"
---
# <a name="inventory-of-pre-production-environment"></a>Inventario dell'ambiente di preproduzione
Le sottoscrizioni di Visual Studio semplificano la gestione degli asset basandosi sul conteggio degli utenti piuttosto che dei dispositivi.

Gli amministratori di Visual Studio devono assegnare le sottoscrizioni di Visual Studio a **utenti specifici e nominati**. **Non sono consentite** le convenzioni di denominazione come Dev1, Dev2 o l'uso di nomi di team come "FeatureTeam".

Ecco alcuni modi per semplificare la creazione dell'inventario dell'ambiente di preproduzione:
- Verificare le assegnazioni degli utenti. Microsoft offre un sito Web denominato [portale di amministrazione di Visual Studio](https://manage.visualstudio.com/) per tenere traccia delle assegnazioni delle sottoscrizioni di Visual Studio.
- Usare il servizio Active Directory locale o basato sul cloud per elencare gli utenti. Se si usa Active Directory per gestire l'accesso degli utenti, si potrebbe riuscire a identificare gli utenti che si occupano di sviluppo e test in base all'appartenenza alla directory.
- Usare strumenti automatizzati per gestire gli inventari dei sistemi. Potrebbe anche essere necessario usare uno strumento di inventario software per facilitare la gestione degli asset software e distinguere gli ambienti di preproduzione da quelli di produzione. Molti clienti che usano Microsoft System Center creano convenzioni di denominazione per automatizzare questa parte del processo di inventario.
- Richiedere aiuto per la riconciliazione manuale. Coinvolgere il personale per semplificare le associazioni tra gli utenti di sviluppo e test e l'ambiente di sviluppo e test.

## <a name="resources"></a>Risorse
- [White paper sulle licenze per Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Condizioni per contratti multilicenza](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle responsabilità degli amministratori:
- [Responsabilità degli amministratori](admin-responsibilities.md)
- [Gestire team di grandi dimensioni e collaboratori esterni](manage-teams.md)
- [Tenere traccia delle assegnazioni degli utenti ed elaborare gli ordini](assignments-orders.md)
- Usare [Utilizzo massimo](maximum-usage.md) per tenere traccia degli impegni di acquisto



