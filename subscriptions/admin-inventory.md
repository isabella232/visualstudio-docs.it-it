---
title: Inventario degli ambienti di pre-produzione | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Informazioni sulla responsabilità degli amministratori di eseguire gli inventari di pre-produzione
ms.openlocfilehash: 97a7a95354cd4d5d85581830830705bc328f2311
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491706"
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
- [White paper sulle licenze per Visual Studio](https://aka.ms/vslicensing)
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Condizioni dei contratti multilicenza](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle responsabilità degli amministratori:
- [Responsabilità degli amministratori](admin-responsibilities.md)
- [Gestire team di grandi dimensioni e collaboratori esterni](manage-teams.md)
- [Tenere traccia delle assegnazioni degli utenti ed elaborare gli ordini](assignments-orders.md)
- Usare [Utilizzo massimo](maximum-usage.md) per tenere traccia degli impegni di acquisto