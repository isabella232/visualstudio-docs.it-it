---
title: Inventario pre-produzione in Visual Studio sottoscrizione | Visual Studio Mercato
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/19/2021
ms.topic: conceptual
description: Informazioni sulla responsabilità degli amministratori di eseguire gli inventari di pre-produzione
ms.openlocfilehash: f312098642d280b9b784a31fec960e2c7c45f3e0
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430485"
---
# <a name="inventory-of-pre-production-environment"></a>Inventario dell'ambiente di preproduzione
Le sottoscrizioni di Visual Studio semplificano la gestione degli asset basandosi sul conteggio degli utenti piuttosto che dei dispositivi.

Visual Studio amministratori devono assegnare Sottoscrizioni di Visual Studio a **utenti specifici denominati.** **Non sono consentite** le convenzioni di denominazione come Dev1, Dev2 o l'uso di nomi di team come "FeatureTeam".

Ecco alcuni modi per semplificare la creazione dell'inventario dell'ambiente di preproduzione:
- Verificare le assegnazioni degli utenti. Microsoft offre un sito Web denominato [portale di amministrazione di Visual Studio](https://manage.visualstudio.com/) per tenere traccia delle assegnazioni delle sottoscrizioni di Visual Studio.
- Usare il servizio Active Directory locale o basato sul cloud per elencare gli utenti. Se si usa Active Directory per gestire l'accesso degli utenti, si potrebbe riuscire a identificare gli utenti che si occupano di sviluppo e test in base all'appartenenza alla directory.
- Usare strumenti automatizzati per gestire gli inventari dei sistemi. Potrebbe anche essere necessario usare uno strumento di inventario software per facilitare la gestione degli asset software e distinguere gli ambienti di preproduzione da quelli di produzione. Molti clienti che usano Microsoft System Center creano convenzioni di denominazione per automatizzare questa parte del processo di inventario.
- Richiedere aiuto per la riconciliazione manuale. Coinvolgere il personale per semplificare le associazioni tra gli utenti di sviluppo e test e l'ambiente di sviluppo e test.

> [!NOTE]
> Il software incluso nelle sottoscrizioni di Visual Studio non è concesso in licenza per gli ambienti di produzione, inclusi gli ambienti a cui hanno accesso gli utenti finali per scopi diversi dai test di accettazione o dalla valutazione per commenti e suggerimenti, un ambiente che si connette a un database di produzione, ambienti per il supporto del ripristino di emergenza o come backup di produzione oppure ambienti usati per la produzione durante i periodi di picco delle attività. Fanno eccezione vantaggi specifici per determinati livelli di sottoscrizione, descritti nel [white paper sulle licenze per Visual Studio](https://aka.ms/vslicensing).  

## <a name="resources"></a>Risorse
- [White paper sulle licenze per Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio sottoscrizioni](https://aka.ms/vsadminhelp)
- [Condizioni per i contratti multilicenza](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle responsabilità per gli amministratori:
- [Responsabilità dell'amministratore](admin-responsibilities.md)
- [Gestire team di grandi dimensioni e collaboratori esterni](manage-teams.md)
- [Tenere traccia delle assegnazioni degli utenti ed elaborare gli ordini](assignments-orders.md)
- Usare [Utilizzo massimo](maximum-usage.md) per tenere traccia degli impegni di acquisto