---
title: Gestione delle opzioni di configurazione - Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707305"
---
# <a name="managing-configuration-options"></a>Gestione delle opzioni di configurazione
Quando si crea un nuovo tipo di progetto, è necessario gestire le impostazioni di configurazione del progetto e della soluzione che determinano la modalità di compilazione, creazione di pacchetti, distribuzione ed esecuzione del progetto. Negli argomenti seguenti viene illustrata la configurazione di progetti e soluzioni.

## <a name="in-this-section"></a>Contenuto della sezione
- [Panoramica](../../extensibility/internals/configuration-options-overview.md)

 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i progetti in possono supportare più configurazioni.

- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)

 Viene illustrato che gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione del progetto e le proprietà indipendenti utilizzando le pagine delle proprietà.

- [Configurazione soluzione](../../extensibility/internals/solution-configuration.md)

 Vengono fornite informazioni sugli elementi archiviati nelle configurazioni di soluzione e sul modo in cui le configurazioni di soluzione indirizzano il comportamento dei comandi **Avvia** e **Compila.**

- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)

 Viene illustrato come l'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione all'interfaccia utente.

- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)

 Viene illustrato come un elenco di configurazioni di soluzione per una determinata soluzione viene gestito dalla finestra di dialogo **Configurazioni soluzione.**

- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Definisce l'atto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] distribuzione e i due modi supportano i progetti che supportano la distribuzione.

- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)

 Vengono illustrati i processi di compilazione supportati da ogni configurazione e le interfacce e i metodi con cui è possibile resi disponibili gli elementi di output.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Fornisce una panoramica dei progetti come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] blocchi predefiniti di base dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
