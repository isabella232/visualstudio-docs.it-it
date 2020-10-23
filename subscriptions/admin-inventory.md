---
title: Inventario pre-produzione nella sottoscrizione di Visual Studio | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 10/22/2020
ms.topic: conceptual
description: Informazioni sulle responsabilità degli amministratori per condurre gli inventari di pre-produzione
ms.openlocfilehash: b464a7d9cfa8c802cd2367c5c7d0e76141583f3a
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467427"
---
# <a name="inventory-of-pre-production-environment"></a>Inventario dell'ambiente di preproduzione
Le sottoscrizioni di Visual Studio semplificano la gestione degli asset basandosi sul conteggio degli utenti piuttosto che dei dispositivi.

Gli amministratori di Visual Studio devono assegnare le sottoscrizioni di Visual Studio a **utenti specifici, denominati**. **Non sono consentite** le convenzioni di denominazione come Dev1, Dev2 o l'uso di nomi di team come "FeatureTeam".

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
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle responsabilità per gli amministratori:
- [Responsabilità dell'amministratore](admin-responsibilities.md)
- [Gestire team di grandi dimensioni e collaboratori esterni](manage-teams.md)
- [Tenere traccia delle assegnazioni degli utenti ed elaborare gli ordini](assignments-orders.md)
- Usare [Utilizzo massimo](maximum-usage.md) per tenere traccia degli impegni di acquisto