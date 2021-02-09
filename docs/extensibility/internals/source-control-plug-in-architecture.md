---
title: Architettura del plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni su come aggiungere il supporto del controllo del codice sorgente all'IDE di Visual Studio tramite l'implementazione e il collegamento di un plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 669ef527e65e56612199b8303f7cc99e8b993b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846400"
---
# <a name="source-control-plug-in-architecture"></a>Architettura dei plug-in del controllo del codice sorgente
È possibile aggiungere il supporto del controllo del codice sorgente all' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) tramite l'implementazione e il collegamento di un plug-in del controllo del codice sorgente. L'IDE si connette al plug-in del controllo del codice sorgente tramite il controllo del codice sorgente ben definito Plug-In API. L'IDE espone le funzionalità di controllo della versione del sistema di controllo del codice sorgente fornendo un'interfaccia utente (UI) composta da barre degli strumenti e comandi di menu. Il plug-in del controllo del codice sorgente implementa la funzionalità del controllo del codice sorgente.

## <a name="source-control-plug-in-resources"></a>Risorse del plug-in del controllo del codice sorgente
 Il plug-in del controllo del codice sorgente fornisce risorse che consentono di creare e connettere l'applicazione di controllo delle versioni all' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Il plug-in del controllo del codice sorgente contiene la specifica API che deve essere implementata da un plug-in del controllo del codice sorgente, in modo che possa essere integrato nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Contiene anche un esempio di codice (scritto in C++) che implementa un plug-in del controllo del codice sorgente che illustra l'implementazione di funzioni essenziali conformi all'API del plug-in del controllo del codice sorgente.

 La specifica dell'API del plug-in del controllo del codice sorgente consente di utilizzare qualsiasi sistema di controllo del codice sorgente di propria scelta se si crea una DLL del controllo del codice sorgente con il set di funzioni necessario implementato in base all'API del plug-in del controllo del codice sorgente.

## <a name="components"></a>Componenti
 Il pacchetto dell'adattatore del controllo del codice sorgente nel diagramma è il componente dell'IDE che converte la richiesta dell'utente per un'operazione di controllo del codice sorgente in una chiamata di funzione supportata dal plug-in del controllo del codice sorgente. Per eseguire questa operazione, l'IDE e il plug-in del controllo del codice sorgente devono avere una finestra di dialogo efficace che passa le informazioni tra l'IDE e il plug-in. Per poter eseguire questa finestra di dialogo, entrambi devono parlare della stessa lingua. L'API del plug-in del controllo del codice sorgente descritta in questa documentazione è il vocabolario comune per questo scambio.

 ![Diagramma dell'architettura di controllo del codice sorgente](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagramma dell'architettura che mostra l'interazione tra VS e il plug-in del controllo del codice sorgente

 Come illustrato nel diagramma dell'architettura, la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, etichettata come vs Shell nel diagramma, ospita i progetti di lavoro dell'utente e i componenti associati, ad esempio gli editor e Esplora soluzioni. Il pacchetto dell'adattatore del controllo del codice sorgente gestisce l'interazione tra l'IDE e il plug-in del controllo del codice sorgente. Il pacchetto dell'adattatore del controllo del codice sorgente fornisce l'interfaccia utente del controllo del codice sorgente. Si tratta dell'interfaccia utente di primo livello con cui l'utente interagisce per avviare e definire l'ambito di un'operazione di controllo del codice sorgente.

 Il plug-in del controllo del codice sorgente può avere una propria interfaccia utente, che può essere costituita da due parti, come illustrato nella figura. La casella etichetta "vendor UI" rappresenta gli elementi dell'interfaccia utente personalizzati forniti dall'autore del plug-in del controllo del codice sorgente. Questi vengono visualizzati direttamente dal plug-in del controllo del codice sorgente quando l'utente richiama un'operazione avanzata del controllo del codice sorgente. La casella "UI Helper" è un set di funzionalità dell'interfaccia utente del plug-in del controllo del codice sorgente richiamate indirettamente tramite l'IDE. Il plug-in del controllo del codice sorgente passa messaggi correlati all'interfaccia utente all'IDE tramite funzioni di callback speciali fornite dall'IDE. L'interfaccia utente di supporto facilita un'integrazione più semplice con l'IDE (spesso tramite un pulsante **avanzato** ) e offre quindi un'esperienza utente finale più unificata.

 Un plug-in del controllo del codice sorgente non può apportare modifiche alla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell e, di conseguenza, al pacchetto di adattatori del controllo del codice sorgente o all'interfaccia utente del controllo del codice sorgente fornita dall'IDE. Deve sfruttare al massimo la flessibilità offerta mediante l'implementazione delle varie funzioni API del plug-in del controllo del codice sorgente che contribuiscono a un'esperienza integrata per l'utente finale. La sezione di riferimento della documentazione dell'API del plug-in del controllo del codice sorgente include informazioni per alcune funzionalità avanzate del plug-in del controllo del codice sorgente. Per sfruttare queste funzionalità, il plug-in del controllo del codice sorgente deve dichiarare le sue funzionalità avanzate nell'IDE durante l'inizializzazione e deve implementare funzioni avanzate specifiche per ogni funzionalità.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
- [Glossario](../../extensibility/source-control-plug-in-glossary.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
