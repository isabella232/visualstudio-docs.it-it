---
title: Architettura del plug-in del controllo del codice | Microsoft Docs
description: Informazioni su come aggiungere il supporto del controllo del codice sorgente all'IDE Visual Studio implementando e collegando un plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a8a53a9e4c11b9a0a268221bd7ab068b7904409
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159100"
---
# <a name="source-control-plug-in-architecture"></a>Architettura dei plug-in del controllo del codice sorgente
È possibile aggiungere il supporto del controllo del codice sorgente all'ambiente di sviluppo integrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) implementando e collegando un plug-in del controllo del codice sorgente. L'IDE si connette al plug-in del controllo del codice sorgente tramite l'API del controllo del codice sorgente Plug-In ben definita. L'IDE espone le funzionalità di controllo della versione del sistema di controllo del codice sorgente fornendo un'interfaccia utente costituita da barre degli strumenti e comandi di menu. Il plug-in del controllo del codice sorgente implementa la funzionalità di controllo del codice sorgente.

## <a name="source-control-plug-in-resources"></a>Risorse plug-in del controllo del codice sorgente
 Il plug-in controllo del codice sorgente fornisce risorse che consentono di creare e connettere l'applicazione di controllo delle versioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] all'IDE. Il plug-in di controllo del codice sorgente contiene la specifica API che deve essere implementata da un plug-in di controllo del codice sorgente in modo che possa essere integrato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'IDE. Contiene anche un esempio di codice (scritto in C++) che implementa uno scheletro di plug-in di controllo del codice sorgente che illustra l'implementazione di funzioni essenziali conformi all'API plug-in del controllo del codice sorgente.

 La specifica dell'API plug-in del controllo del codice sorgente consente di sfruttare qualsiasi sistema di controllo del codice sorgente scelto se si crea una DLL del controllo del codice sorgente con il set necessario di funzioni implementate in base all'API del plug-in del controllo del codice sorgente.

## <a name="components"></a>Componenti
 Il pacchetto dell'adattatore di controllo del codice sorgente nel diagramma è il componente dell'IDE che converte la richiesta dell'utente per un'operazione di controllo del codice sorgente in una chiamata di funzione supportata dal plug-in del controllo del codice sorgente. A tale scopo, l'IDE e il plug-in del controllo del codice sorgente devono avere una finestra di dialogo efficace che passa le informazioni tra l'IDE e il plug-in. Perché questo dialogo si ssercii, entrambi devono parlare la stessa lingua. L'API plug-in del controllo del codice sorgente descritta in questa documentazione è il vocabolario comune per questo scambio.

 ![Diagramma dell'architettura del controllo del codice sorgente](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagramma dell'architettura che illustra l'interazione tra Visual Studio e il plug-in di controllo del codice sorgente

 Come illustrato nel diagramma dell'architettura, la shell, etichettata come shell di Visual Studio nel diagramma, ospita i progetti di lavoro dell'utente e i componenti associati, ad esempio gli editor e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Esplora soluzioni. Il pacchetto dell'adattatore di controllo del codice sorgente gestisce l'interazione tra l'IDE e il plug-in del controllo del codice sorgente. Il pacchetto dell'adattatore di controllo del codice sorgente fornisce la propria interfaccia utente del controllo del codice sorgente. È l'interfaccia utente di primo livello con cui l'utente interagisce per avviare e definire l'ambito di un'operazione di controllo del codice sorgente.

 Il plug-in del controllo del codice sorgente può avere una propria interfaccia utente, che può essere costituita da due parti, come illustrato nella figura. La casella con etichetta "Vendor UI" rappresenta gli elementi dell'interfaccia utente personalizzati forniti dall'autore del plug-in del controllo del codice sorgente. Questi vengono visualizzati direttamente dal plug-in del controllo del codice sorgente quando l'utente richiama un'operazione di controllo del codice sorgente avanzata. La casella "Interfaccia utente helper" è un set di funzionalità dell'interfaccia utente del plug-in del controllo del codice sorgente richiamate indirettamente tramite l'IDE. Il plug-in del controllo del codice sorgente passa i messaggi correlati all'interfaccia utente all'IDE tramite funzioni di callback speciali fornite dall'IDE. L'interfaccia utente helper facilita un'integrazione più semplice con  l'IDE (spesso tramite l'uso di un pulsante Avanzate) e offre quindi un'esperienza utente finale più unificata.

 Un plug-in del controllo del codice sorgente non può apportare modifiche alla shell e, di conseguenza, al pacchetto dell'adattatore di controllo del codice sorgente o all'interfaccia utente del controllo del codice sorgente fornita [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dall'IDE. Deve usare al massimo la flessibilità offerta tramite l'implementazione delle varie funzioni api plug-in del controllo del codice sorgente che contribuiscono a un'esperienza integrata per l'utente finale. La sezione di riferimento della documentazione dell'API plug-in del controllo del codice sorgente include informazioni su alcune funzionalità avanzate del plug-in del controllo del codice sorgente. Per sfruttare queste funzionalità, il plug-in del controllo del codice sorgente deve dichiarare le funzionalità avanzate all'IDE durante l'inizializzazione e deve implementare funzioni avanzate specifiche per ogni funzionalità.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
- [Glossario](../../extensibility/source-control-plug-in-glossary.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
