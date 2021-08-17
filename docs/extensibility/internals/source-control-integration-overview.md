---
title: Panoramica dell'integrazione del controllo del codice | Microsoft Docs
description: 'Informazioni sulle differenze tra i due modi per integrare il controllo del codice sorgente in Visual Studio: un plug-in di controllo del codice sorgente e un VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0682f1d25ed01e5b7b3261718b7e2c261110137a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042101"
---
# <a name="source-control-integration-overview"></a>Panoramica dell'integrazione del controllo del codice sorgente
In questa sezione vengono confrontati i due modi per eseguire l'integrazione Visual Studio controllo del codice sorgente. Un plug-in del controllo del codice sorgente e un VSPackage che fornisce una soluzione di controllo del codice sorgente ed evidenzia le nuove funzionalità del controllo del codice sorgente. Visual Studio consente il passaggio manuale tra i pacchetti VSPackage del controllo del codice sorgente e i plug-in del controllo del codice sorgente, nonché il passaggio automatico basato su soluzioni.

## <a name="source-control-integration"></a>Integrazione del controllo del codice sorgente
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di opzioni di integrazione del controllo del codice sorgente. In tutte le versioni di è comunque possibile integrare un plug-in basato sull'API plug-in del controllo del codice sorgente (precedentemente definita anche API MSSCCI), che fornisce funzionalità di base per il controllo del codice sorgente durante l'uso dell'interfaccia utente del controllo del codice sorgente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Visual Studio. Un VSPackage di controllo del codice sorgente, d'altra parte, fornisce un nuovo percorso di integrazione approfondita adatto per l'integrazione del controllo del codice sorgente che richiede un elevato livello di sofisticatità e autonomia nel modello di controllo del codice [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sorgente.

 ![Panoramica del controllo del codice sorgente](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Tutte le versioni di Visual Studio supportano la specifica dell'API plug-in del controllo del codice sorgente versione 1.2 come percorso di integrazione. Un implementatore del plug-in del controllo del codice sorgente scrive una DLL che implementa le funzioni api del plug-in del controllo del codice sorgente per l'integrazione e la registrazione del controllo del codice sorgente, come descritto in Creazione di un plug-in del controllo [del codice sorgente.](../../extensibility/internals/creating-a-source-control-plug-in.md) In questo approccio, l'IDE (Integrated Development Environment) usa l'interfaccia utente per le finestre di dialogo, ad esempio archiviazione, estrazione, pagine delle proprietà strumenti/opzioni, barre degli strumenti e glifi del controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente. La rigorosa aderenza all'API plug-in del controllo del codice sorgente assicura una facile integrazione in Visual Studio e un'esperienza senza problemi per l'utente. Ciò significa che il plug-in del controllo del codice sorgente deve implementare la maggior parte delle funzioni e dei callback dettagliati nell'API.

 Per implementare un plug-in del controllo del codice sorgente usando l'API plug-in del controllo del codice sorgente, seguire questa procedura:

1. Creare una DLL che implementa le funzioni specificate nei [plug-in del controllo del codice sorgente.](../../extensibility/source-control-plug-ins.md)

2. Registrare la DLL impostando le voci del Registro di sistema appropriate (descritte in [Procedura: Installare un plug-in del controllo del codice sorgente).](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Creare un'interfaccia utente helper e visualizzarla quando richiesto dal pacchetto dell'adattatore di controllo del codice sorgente (il componente Visual Studio che gestisce la funzionalità di controllo del codice sorgente tramite plug-in del controllo del codice sorgente)

   In risposta a un comando di controllo del codice sorgente, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni al plug-in del controllo del codice sorgente tramite le funzioni definite nell'API del plug-in del controllo del codice sorgente. Per le opzioni avanzate, è possibile chiamare il plug-in del controllo del codice sorgente per presentare la propria interfaccia utente, ad esempio la ricerca di un progetto in controllo del codice sorgente. Ciò significa che all'utente possono essere presentati due stili dell'interfaccia utente probabilmente diversi quando si lavora con il controllo del codice sorgente: l'interfaccia utente presentata da Visual Studio e l'interfaccia utente presentata dal plug-in del controllo del codice sorgente. Questo è più evidente con le operazioni avanzate di controllo del codice sorgente.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Svantaggi dell'implementazione di un plug-in del controllo del codice sorgente

- Per le funzionalità avanzate, l'utente può visualizzare due stili diversi di interfacce, causando una possibile confusione.

- Il plug-in del controllo del codice sorgente è limitato al modello di controllo del codice sorgente implicito nell'API del plug-in del controllo del codice sorgente.

- L'API plug-in del controllo del codice sorgente potrebbe essere troppo restrittiva per alcuni scenari di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in del controllo del codice sorgente

- Visual Studio fornisce tutta l'interfaccia utente per tutte le operazioni di base del controllo del codice sorgente in modo che il plug-in del controllo del codice sorgente non deve implementare un'interfaccia utente potenzialmente complessa.

- A causa della rigida API, il plug-in di controllo del codice sorgente può interagire immediatamente con programmi di controllo del codice sorgente esterni per fornire funzionalità più complete; Visual Studio non è importante il modo in cui viene eseguita la funzionalità di controllo del codice sorgente, ma solo che viene eseguita in base all'API plug-in del controllo del codice sorgente.

- È più semplice implementare un plug-in del controllo del codice sorgente rispetto a un VSPackage del controllo del codice sorgente.

## <a name="source-control-vspackage"></a>VsPackage del controllo del codice sorgente
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]consente un'integrazione approfondita Visual Studio controllo completo della funzionalità di controllo del codice sorgente e sostituzione completa dell Visual Studio utente del controllo del codice sorgente fornita dall'utente. Un vspackage del controllo del codice sorgente viene registrato con Visual Studio e fornisce funzionalità di controllo del codice sorgente. Anche se è possibile registrare diversi VSPackage di controllo del codice sorgente con Visual Studio, solo uno di essi può essere attivo alla volta. Un VSPackage di controllo del codice sorgente ha il controllo completo della funzionalità e dell'aspetto del controllo del codice sorgente Visual Studio mentre è attivo. Tutti gli altri VSPackage del controllo del codice sorgente che possono essere registrati nel sistema sono inattivi e non visualizzano alcuna interfaccia utente.

 L'implementazione di un pacchetto VSPackage del controllo del codice sorgente richiede una strategia "tutto o niente". L'autore di un pacchetto VSPackage per il controllo del codice sorgente deve investire una notevole quantità di impegno nell'implementazione di una serie di interfacce di controllo del codice sorgente e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente. Per altri [dettagli, vedere Creazione di un pacchetto VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) per il controllo del codice sorgente.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Svantaggi dell'implementazione di un pacchetto VSPackage del controllo del codice sorgente

- Il pacchetto VSPackage deve implementare una serie di interfacce complesse per integrarsi correttamente con Visual Studio.

- Il pacchetto VSPackage deve fornire tutta l'interfaccia utente necessaria per il controllo del codice sorgente. Visual Studio non fornirà assistenza in quest'area.

- Un PACCHETTO VSPackage del controllo del codice sorgente è strettamente collegato a Visual Studio e non può funzionare con programmi autonomi, quindi le funzionalità non possono essere facilmente condivise con una versione esterna del programma di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un pacchetto VSPackage del controllo del codice sorgente

- Poiché il pacchetto VSPackage ha il controllo completo sull'interfaccia utente e sulle funzionalità del controllo del codice sorgente, all'utente viene presentata un'interfaccia trasparente per il controllo del codice sorgente.

- Il pacchetto VSPackage non è limitato a un modello di controllo del codice sorgente specifico.

## <a name="see-also"></a>Vedi anche
- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novità del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)
