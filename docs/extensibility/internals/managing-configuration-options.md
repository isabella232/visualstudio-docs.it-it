---
title: Gestione delle opzioni di configurazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3b7c2c1cac1255c6234d2b9a8ed6ab4fd05820
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644536"
---
# <a name="managing-configuration-options"></a>Gestione delle opzioni di configurazione
Quando si crea un nuovo tipo di progetto, è necessario gestire impostazioni di configurazione di progetto e soluzione che determinano il modo in cui il progetto verrà compilato, nel pacchetto, distribuite ed eseguite. Gli argomenti seguenti descrivono la configurazione di progetto e soluzione.

## <a name="in-this-section"></a>In questa sezione
- [Panoramica](../../extensibility/internals/configuration-options-overview.md)

 Viene descritto come progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può supportare più configurazioni.

- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)

 Viene illustrato che gli utenti possono visualizzare e modificare proprietà dipendenti di configurazione di progetto e proprietà indipendenti tramite pagine delle proprietà.

- [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)

 Fornisce informazioni su ciò che viene archiviato nelle configurazioni di soluzione e come configurazioni soluzione istruiscono il comportamento dei **avviare** e **compilazione** comandi.

- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)

 Viene illustrato il modo in cui l'oggetto di configurazione di progetto gestisce la visualizzazione delle informazioni di configurazione per l'interfaccia utente.

- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)

 Illustra come viene gestito un elenco di configurazioni di soluzione per una particolare soluzione per il **configurazioni soluzione** nella finestra di dialogo.

- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Definisce l'azione di distribuzione e i due modi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta i progetti che supportano la distribuzione.

- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)

 Illustra i processi di compilazione in grado di supportare tutte le configurazioni e le interfacce e metodi da quale output gli elementi possono essere rese disponibili.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Viene fornita una panoramica di progetti come blocchi predefiniti di base del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.