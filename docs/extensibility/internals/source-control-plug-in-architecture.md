---
title: Architettura del plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705104"
---
# <a name="source-control-plug-in-architecture"></a>Architettura dei plug-in del controllo del codice sorgente
È possibile aggiungere il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporto del controllo del codice sorgente all'ambiente di sviluppo integrato (IDE) implementando e collegando un plug-in del controllo del codice sorgente. L'IDE si connette al plug-in del controllo del codice sorgente tramite l'API del plug-in del controllo del codice sorgente ben definita. L'IDE espone le funzionalità di controllo della versione del sistema di controllo del codice sorgente fornendo un'interfaccia utente (UI) costituita da barre degli strumenti e comandi di menu. Il plug-in del controllo del codice sorgente implementa la funzionalità del controllo del codice sorgente.

## <a name="source-control-plug-in-resources"></a>Risorse del plug-in del controllo del codice sorgenteSource Control Plug-in Resources
 Il plug-in controllo del codice sorgente fornisce risorse che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consentono di creare e connettere l'applicazione di controllo delle versioni all'IDE. Il plug-in del controllo del codice sorgente contiene la specifica API che deve essere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementata da un plug-in del controllo del codice sorgente in modo che possa essere integrato nell'IDE. Contiene inoltre un esempio di codice (scritto in C ) che implementa uno scheletro di controllo del codice sorgente plug-in che dimostra l'implementazione di funzioni essenziali compatibili con l'API plug-in controllo del codice sorgente.

 La specifica dell'API del plug-in del controllo del codice sorgente consente di sfruttare qualsiasi sistema di controllo del codice sorgente di propria scelta se si crea una DLL del controllo del codice sorgente con il set necessario di funzioni implementate in conformità con l'API del plug-in del controllo del codice sorgente.

## <a name="components"></a>Componenti
 Il pacchetto dell'adattatore del controllo del codice sorgente nel diagramma è il componente dell'IDE che converte la richiesta dell'utente per un'operazione del controllo del codice sorgente in una chiamata di funzione supportata dal plug-in del controllo del codice sorgente. A tale scopo, l'IDE e il plug-in controllo del codice sorgente deve disporre di una finestra di dialogo efficace che passa informazioni avanti e indietro tra l'IDE e il plug-in. Affinché questa finestra di dialogo avvenga, entrambi devono parlare la stessa lingua. L'API del plug-in del controllo del codice sorgente descritta in questa documentazione è il vocabolario comune per questo scambio.

 ![Diagramma dell'architettura del controllo del codice sorgenteSource Code Control Architecture Diagram](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagramma dell'architettura che mostra l'interazione tra VS e il plug-in del controllo del codice sorgente

 Come illustrato nel diagramma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'architettura, la shell, etichettata come shell VS nel diagramma, ospita i progetti di lavoro dell'utente e i componenti associati, ad esempio gli editor e Esplora soluzioni. Il pacchetto dell'adattatore del controllo del codice sorgente gestisce l'interazione tra l'IDE e il plug-in del controllo del codice sorgente. Il pacchetto dell'adattatore del controllo del codice sorgente fornisce la propria interfaccia utente del controllo del codice sorgente. È l'interfaccia utente di primo livello con cui l'utente interagisce per avviare e definire l'ambito di un'operazione di controllo del codice sorgente.

 Il plug-in del controllo del codice sorgente può avere la propria interfaccia utente, che può essere costituita da due parti, come illustrato nella figura. La casella denominata "Interfaccia utente fornitore" rappresenta gli elementi dell'interfaccia utente personalizzati forniti dall'autore del plug-in del controllo del codice sorgente. Questi vengono visualizzati direttamente dal plug-in del controllo del codice sorgente quando l'utente richiama un'operazione avanzata di controllo del codice sorgente. La casella denominata "Helper UI" è un set di funzionalità dell'interfaccia utente del plug-in del controllo del codice sorgente che vengono richiamate indirettamente tramite l'IDE. Il plug-in del controllo del codice sorgente passa i messaggi relativi all'interfaccia utente all'IDE tramite funzioni di callback speciali fornite dall'IDE. L'interfaccia utente helper facilita un'integrazione più semplice con l'IDE (spesso tramite l'uso di un pulsante **Avanzate)** e pertanto fornisce un'esperienza utente finale più unificata.

 Un plug-in del controllo del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] codice sorgente non può apportare modifiche alla shell e, di conseguenza, al pacchetto dell'adattatore del controllo del codice sorgente o all'interfaccia utente del controllo del codice sorgente fornita dall'IDE. Deve sfruttare al massimo la flessibilità offerta tramite l'implementazione delle varie funzioni API plug-in del controllo del codice sorgente che contribuiscono a un'esperienza integrata per l'utente finale. La sezione di riferimento della documentazione dell'API del plug-in del controllo del codice sorgente include informazioni per alcune funzionalità avanzate del plug-in del controllo del codice sorgente. Per sfruttare queste funzionalità, il plug-in controllo del codice sorgente deve dichiarare le funzionalità avanzate per l'IDE durante l'inizializzazione e deve implementare funzioni avanzate specifiche per ogni funzionalità.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
- [Glossario](../../extensibility/source-control-plug-in-glossary.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
