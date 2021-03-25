---
title: Panoramica dell'integrazione del controllo del codice sorgente | Microsoft Docs
description: 'Informazioni sulle differenze tra le due modalità di integrazione del controllo del codice sorgente in Visual Studio: un plug-in del controllo del codice sorgente e un pacchetto VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9feacd8e051b47b1fec6c3d3ad08e34e591fc57c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064319"
---
# <a name="source-control-integration-overview"></a>Panoramica dell'integrazione del controllo del codice sorgente
In questa sezione vengono confrontati i due modi per integrarsi nel controllo del codice sorgente di Visual Studio. un plug-in del controllo del codice sorgente e un VSPackage che fornisce una soluzione di controllo del codice sorgente ed evidenzia le nuove funzionalità del controllo del codice sorgente. Visual Studio consente il cambio manuale tra i pacchetti VSPackage del controllo del codice sorgente e i plug-in del controllo del codice sorgente, nonché il cambio automatico basato sulla soluzione.

## <a name="source-control-integration"></a>Integrazione del controllo del codice sorgente
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di opzioni di integrazione del controllo del codice sorgente. In tutte le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è ancora possibile integrare un plug-in in base all'API del plug-in del controllo del codice sorgente (in precedenza definita anche API MSSCCI), che fornisce la funzionalità di base del controllo del codice sorgente durante l'utilizzo dell'interfaccia utente di Visual Studio. Un VSPackage del controllo del codice sorgente, d'altra parte, fornisce un nuovo percorso di integrazione completa [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adatto per l'integrazione del controllo del codice sorgente che richiede un livello elevato di complessità e autonomia nel modello di controllo del codice sorgente.

 ![Cenni preliminari sul controllo del codice sorgente](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Tutte le versioni di Visual Studio supportano la specifica API del plug-in del controllo del codice sorgente versione 1,2 come percorso di integrazione. Un implementatore del plug-in del controllo del codice sorgente scrive una DLL che implementa le funzioni API del plug-in del controllo del codice sorgente per l'integrazione e la registrazione del controllo del codice sorgente, come descritto in [creazione di un plug-in del controllo](../../extensibility/internals/creating-a-source-control-plug-in.md) Con questo approccio, l'ambiente di sviluppo integrato (IDE) utilizza l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente per le finestre di dialogo, ad esempio archivia, Estrai, strumenti/Opzioni pagine delle proprietà, barre degli strumenti e glifi del controllo del codice sorgente. Una stretta aderenza all'API plug-in del controllo del codice sorgente assicura una facile integrazione in Visual Studio e un'esperienza senza problemi per l'utente. Questo significa che il plug-in del controllo del codice sorgente deve implementare la maggior parte delle funzioni e dei callback descritti in dettaglio nell'API.

 Per implementare un plug-in del controllo del codice sorgente tramite l'API del plug-in del controllo del codice sorgente, attenersi alla seguente procedura:

1. Creare una DLL che implementi le funzioni specificate nei [plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).

2. Registrare la DLL rendendo le voci del registro di sistema appropriate (descritte in [procedura: installazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Creare un'interfaccia utente di supporto e visualizzarla quando richiesto dal pacchetto di adattatori del controllo del codice sorgente (componente di Visual Studio che gestisce la funzionalità del controllo del codice sorgente tramite plug-in del controllo del codice sorgente)

   In risposta a un comando di controllo del codice sorgente, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni al plug-in del controllo del codice sorgente tramite le funzioni definite nell'API del plug-in del controllo del codice sorgente. Per le opzioni avanzate, è possibile chiamare il plug-in del controllo del codice sorgente per presentare una propria interfaccia utente, ad esempio l'esplorazione di un progetto incluso nel controllo del codice sorgente. Ciò significa che all'utente possono essere presentati due stili probabilmente diversi dell'interfaccia utente quando si utilizza il controllo del codice sorgente: l'interfaccia utente visualizzata da Visual Studio e l'interfaccia utente presente nel plug-in del controllo del codice sorgente. Questo è più evidente con le operazioni avanzate di controllo del codice sorgente.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Svantaggi dell'implementazione di un plug-in del controllo del codice sorgente

- Per le funzionalità avanzate, l'utente può visualizzare due stili diversi di interfacce, causando possibili confusioni.

- Il plug-in del controllo del codice sorgente è limitato al modello di controllo del codice sorgente, implicito nell'API del plug-in del controllo del codice sorgente.

- L'API del plug-in del controllo del codice sorgente può essere troppo restrittiva per alcuni scenari di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in del controllo del codice sorgente

- Visual Studio fornisce tutte le interfacce utente per tutte le operazioni di base del controllo del codice sorgente, in modo che il plug-in del controllo del codice sorgente non debba implementare un'interfaccia utente potenzialmente complessa.

- Grazie all'API Strict, il plug-in del controllo del codice sorgente può interagire prontamente con i programmi di controllo del codice sorgente esterni per fornire funzionalità più estese. Visual Studio non è rilevante per il modo in cui viene eseguita la funzionalità del controllo del codice sorgente, solo che viene eseguita in base all'API del plug-in del controllo del codice sorgente.

- È più facile implementare un plug-in del controllo del codice sorgente rispetto a un VSPackage del controllo del codice sorgente.

## <a name="source-control-vspackage"></a>VSPackage del controllo del codice sorgente
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] consente l'integrazione completa in Visual Studio con il controllo completo della funzionalità di controllo del codice sorgente e la sostituzione completa dell'interfaccia utente del controllo del codice sorgente fornita da Visual Studio. Un pacchetto VSPackage del controllo del codice sorgente viene registrato con Visual Studio e fornisce funzionalità di controllo del codice sorgente. Sebbene diversi VSPackage del controllo del codice sorgente possono essere registrati con Visual Studio, solo uno di essi può essere attivo in qualsiasi momento. Un VSPackage del controllo del codice sorgente ha il controllo completo sulla funzionalità e l'aspetto del controllo del codice sorgente in Visual Studio mentre è attivo. Tutti gli altri pacchetti VSPackage del controllo del codice sorgente che possono essere registrati nel sistema sono inattivi e non visualizzano alcuna interfaccia utente.

 Per l'implementazione di un pacchetto VSPackage del controllo del codice sorgente è necessaria una strategia "tutto o niente". L'autore di un pacchetto VSPackage di controllo del codice sorgente deve investire una notevole quantità di sforzi nell'implementazione di una serie di interfacce di controllo del codice sorgente e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente. Per altri dettagli, vedere [creazione di un pacchetto VSPackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md) .

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Svantaggi dell'implementazione di un pacchetto VSPackage del controllo del codice sorgente

- Il pacchetto VSPackage deve implementare una serie di interfacce complesse per integrarsi correttamente con Visual Studio.

- Il pacchetto VSPackage deve fornire tutta l'interfaccia utente necessaria per il controllo del codice sorgente. Visual Studio non fornirà assistenza in quest'area.

- Un VSPackage del controllo del codice sorgente è strettamente correlato a Visual Studio e non può funzionare con i programmi autonomi, quindi la funzionalità non può essere condivisa con facilità con una versione esterna del programma di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un pacchetto VSPackage del controllo del codice sorgente

- Poiché il pacchetto VSPackage ha il controllo completo sull'interfaccia utente e la funzionalità del controllo del codice sorgente, viene visualizzata un'interfaccia trasparente per il controllo del codice sorgente.

- Il pacchetto VSPackage non è confinato a un particolare modello di controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novità del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)
