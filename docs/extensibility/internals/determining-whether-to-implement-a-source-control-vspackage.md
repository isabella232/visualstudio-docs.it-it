---
title: Quando implementare un VSPackage del controllo del codice sorgente
description: Informazioni sulle opzioni dei plug-in del controllo del codice sorgente e dei pacchetti VSPackage di controllo del codice sorgente disponibili per l'estensione delle soluzioni di controllo del codice sorgente di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80c86a8ab40b74d1b8f2838e3bf4359af41b0fc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963432"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinare se implementare un pacchetto VSPackage del controllo del codice sorgente

Questa sezione illustra le scelte dei plug-in del controllo del codice sorgente e dei pacchetti VSPackage per l'estensione delle soluzioni di controllo del codice sorgente e fornisce linee guida generali sulla scelta di un percorso di integrazione appropriato.

## <a name="small-source-control-solution-with-limited-resources"></a>Piccola soluzione di controllo del codice sorgente con risorse limitate

 Se si dispone di risorse limitate e non è possibile sovraccaricare il sovraccarico dovuto alla scrittura di un pacchetto di controllo del codice sorgente, è possibile creare plug-in basati su API del plug-in del controllo del codice sorgente. In questo modo è possibile lavorare side-by-side con i pacchetti del controllo del codice sorgente ed è possibile passare tra i plug-in del controllo del codice sorgente e i pacchetti su richiesta. Per ulteriori informazioni, vedere [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Soluzione di controllo del codice sorgente di grandi dimensioni con un set di funzionalità avanzato

 Se si desidera implementare una soluzione di controllo del codice sorgente che fornisce un modello di controllo del codice sorgente completo che non viene acquisito in modo adeguato tramite l'API del plug-in del controllo del codice sorgente, è possibile considerare un pacchetto del controllo del codice sorgente come percorso di integrazione. Questo vale soprattutto se si preferisce sostituire il pacchetto dell'adattatore del controllo del codice sorgente (che comunica con i plug-in del controllo del codice sorgente e fornisce un'interfaccia utente di base del controllo del codice sorgente), in modo da poter gestire gli eventi del controllo del codice sorgente in modo personalizzato. Se si dispone già di un'interfaccia utente del controllo del codice sorgente soddisfacente e si desidera mantenere tale esperienza in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , l'opzione del pacchetto del controllo del codice sorgente consente di eseguire questa operazione. Il pacchetto del controllo del codice sorgente non è generico ed è progettato solo per l'uso con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Se si desidera implementare una soluzione di controllo del codice sorgente che fornisce flessibilità e controllo più completo sulla logica e sull'interfaccia utente del controllo del codice sorgente, è possibile che si preferisca la route di integrazione del pacchetto del controllo del codice sorgente È possibile:

1. Registrare il pacchetto VSPackage del controllo del codice sorgente (vedere [registrazione e selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata (vedere [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Specificare i glifi da usare e gestire Esplora soluzioni eventi del glifo (vedere il [controllo Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Gestire gli eventi di modifica della query e di salvataggio delle query (vedere [query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Vedi anche

- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
