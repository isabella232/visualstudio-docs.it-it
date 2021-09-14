---
title: Gestione delle opzioni di configurazione | Microsoft Docs
description: Informazioni su come gestire le impostazioni di configurazione di progetti e soluzioni in Visual Studio per controllare come verrà compilato, in pacchetto, distribuito ed eseguito il progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 067584e222765af13d5e331f71020cfa54954b54
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626093"
---
# <a name="managing-configuration-options"></a>Gestione delle opzioni di configurazione
Quando si crea un nuovo tipo di progetto, è necessario gestire le impostazioni di configurazione del progetto e della soluzione che determinano come verrà compilato, in pacchetto, distribuito ed eseguito il progetto. Negli argomenti seguenti viene illustrata la configurazione di progetti e soluzioni.

## <a name="in-this-section"></a>Contenuto della sezione
- [Overview](../../extensibility/internals/configuration-options-overview.md)

 Descrive in che modo i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono supportare più configurazioni.

- [Pagine delle proprietà](../../extensibility/internals/property-pages.md)

 Spiega che gli utenti possono visualizzare e modificare le proprietà dipendenti dalla configurazione del progetto e le proprietà indipendenti tramite le pagine delle proprietà.

- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)

 Vengono fornite informazioni sugli elementi archiviati nelle configurazioni della soluzione e sul modo in cui le configurazioni di soluzione indirizzano il comportamento dei **comandi Start** **e Build.**

- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)

 Viene illustrato come l'oggetto di configurazione del progetto gestisce la visualizzazione delle informazioni di configurazione nell'interfaccia utente.

- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)

 Viene illustrato come un elenco di configurazioni di soluzione per una determinata soluzione viene gestito dalla **finestra di dialogo Configurazioni** soluzione .

- [Configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Definisce l'atto di distribuzione e i due modi in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supportano i progetti che supportano la distribuzione.

- [Configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md)

 Illustra i processi di compilazione che ogni configurazione può supportare e le interfacce e i metodi con cui gli elementi di output possono essere resi disponibili.

## <a name="related-sections"></a>Sezioni correlate
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene fornita una panoramica dei progetti come blocchi predefiniti di base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
