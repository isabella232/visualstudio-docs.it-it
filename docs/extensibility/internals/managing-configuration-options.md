---
title: Gestione delle opzioni di configurazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e18c308d74f8c20267c286c47d0e89bf82cd2850
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707305"
---
# <a name="managing-configuration-options"></a>Gestione delle opzioni di configurazione
Quando si crea un nuovo tipo di progetto, è necessario gestire le impostazioni di configurazione del progetto e della soluzione che determinano il modo in cui il progetto verrà compilato, inserito in un pacchetto, distribuito ed eseguito. Gli argomenti seguenti illustrano la configurazione di progetti e soluzioni.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica](../../extensibility/internals/configuration-options-overview.md)

 Descrive in che modo i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono supportare più configurazioni.

- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)

 Spiega che gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione del progetto e le proprietà indipendenti usando le pagine delle proprietà.

- [Configurazione soluzione](../../extensibility/internals/solution-configuration.md)

 Fornisce informazioni sugli elementi archiviati nelle configurazioni della soluzione e su come le configurazioni della soluzione indirizzano il comportamento dei comandi di **avvio** e **compilazione** .

- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)

 Viene illustrato il modo in cui l'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)

 Viene illustrato come un elenco di configurazioni della soluzione per una particolare soluzione venga gestito dalla finestra di dialogo **configurazioni soluzione** .

- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Definisce l'azione di distribuzione e i due metodi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supportati per i progetti che supportano la distribuzione.

- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)

 Vengono illustrati i processi di compilazione supportati da ogni configurazione e le interfacce e i metodi in base ai quali è possibile rendere disponibili gli elementi di output.

## <a name="related-sections"></a>Sezioni correlate
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene fornita una panoramica dei progetti come blocchi predefiniti di base dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE). Sono disponibili collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
