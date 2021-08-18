---
title: Quando implementare un VSPackage del controllo del codice sorgente
description: Informazioni sulle scelte dei plug-in del controllo del codice sorgente e dei pacchetti VSPackage del controllo del codice sorgente disponibili per l'estensione Visual Studio di controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5e16803a570c845e9283debcfb9e8d388b1cdd20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124659"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinare se implementare un VSPackage del controllo del codice sorgente

Questa sezione elabora le scelte dei plug-in del controllo del codice sorgente e dei pacchetti VSPackage del controllo del codice sorgente per l'estensione delle soluzioni di controllo del codice sorgente e fornisce linee guida generali sulla scelta di un percorso di integrazione appropriato.

## <a name="small-source-control-solution-with-limited-resources"></a>Soluzione di controllo del codice sorgente di piccole dimensioni con risorse limitate

 Se si dispone di risorse limitate e non è possibile sovraccaricarsi della scrittura di un pacchetto di controllo del codice sorgente, è possibile creare plug-in basati sull'API del controllo del codice sorgente. In questo modo è possibile lavorare side-by-side con i pacchetti di controllo del codice sorgente ed è possibile passare da plug-in del controllo del codice sorgente a pacchetti su richiesta. Per altre informazioni, vedere [Registrazione e selezione.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Soluzione di controllo del codice sorgente di grandi dimensioni con un set di funzionalità completo

 Se si vuole implementare una soluzione di controllo del codice sorgente che fornisce un modello di controllo del codice sorgente completo che non viene acquisito in modo adeguato tramite l'API plug-in del controllo del codice sorgente, è possibile considerare un pacchetto di controllo del codice sorgente come percorso di integrazione. Questo vale soprattutto se si preferisce sostituire il pacchetto dell'adattatore del controllo del codice sorgente (che comunica con i plug-in del controllo del codice sorgente e fornisce un'interfaccia utente di base del controllo del codice sorgente) con il proprio in modo da poter gestire gli eventi del controllo del codice sorgente in modo personalizzato. Se si dispone già di un'interfaccia utente soddisfacente per il controllo del codice sorgente e si vuole mantenere tale esperienza in , l'opzione del pacchetto di controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di eseguire questa operazione. Il pacchetto di controllo del codice sorgente non è generico ed è progettato esclusivamente per l'uso con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Se si vuole implementare una soluzione di controllo del codice sorgente che offre flessibilità e controllo più completo sulla logica del controllo del codice sorgente e sull'interfaccia utente, è preferibile usare la route di integrazione del pacchetto di controllo del codice sorgente. È possibile:

1. Registrare il pacchetto VSPackage del controllo del codice sorgente (vedere [Registrazione e selezione).](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata (vedere [Interfaccia utente personalizzata).](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Specificare i glifi da usare e gestire Esplora soluzioni glifi (vedere [Controllo glifi).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Gestire gli eventi Di modifica query e Salvataggio query (vedere [Query Edit Query Save).](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

## <a name="see-also"></a>Vedi anche

- [Creare un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
