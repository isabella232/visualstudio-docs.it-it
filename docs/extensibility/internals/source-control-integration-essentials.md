---
title: Informazioni di base sull'integrazione del controllo del | Microsoft Docs
description: 'Informazioni sui due tipi di integrazione del controllo del codice sorgente supportati Visual Studio: un plug-in di controllo del codice sorgente e una soluzione di controllo del codice sorgente basata su VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c3a74b54d332f7ae8176702cf1744fb576e19afd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034571"
---
# <a name="source-control-integration-essentials"></a>Nozioni fondamentali sull'integrazione del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di integrazione del controllo del codice sorgente: un plug-in del controllo del codice sorgente che fornisce funzionalità di base e viene compilato usando l'API plug-in del controllo del codice sorgente (precedentemente nota come API MSSCCI) e una soluzione di integrazione del controllo del codice sorgente basata su VSPackage che fornisce funzionalità più affidabili.

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Un plug-in del controllo del codice sorgente viene scritto come DLL che implementa l'API del plug-in del controllo del codice sorgente. La funzionalità di integrazione della registrazione e del controllo del codice sorgente viene fornita tramite l'API . Questo approccio è più semplice da implementare rispetto a un VSPackage del controllo del codice sorgente e usa l'interfaccia utente per la maggior parte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] delle operazioni di controllo del codice sorgente.

 Per implementare un plug-in del controllo del codice sorgente usando l'API plug-in del controllo del codice sorgente, seguire questa procedura:

1. Creare una DLL che implementa le funzioni specificate nei [plug-in del controllo del codice sorgente.](../../extensibility/source-control-plug-ins.md)

2. Registrare la DLL effettuando le voci del Registro di sistema appropriate, come descritto in [Procedura: Installare un plug-in del controllo del codice sorgente.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Creare un'interfaccia utente helper e visualizzarla quando richiesto dal pacchetto dell'adattatore di controllo del codice sorgente (il componente che gestisce la funzionalità di controllo del codice sorgente tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plug-in del controllo del codice sorgente).

   Per altre informazioni, vedere [Creazione di un plug-in del controllo del codice sorgente.](../../extensibility/internals/creating-a-source-control-plug-in.md)

## <a name="source-control-vspackage"></a>VsPackage del controllo del codice sorgente
 Un'implementazione VSPackage del controllo del codice sorgente consente di sviluppare una sostituzione personalizzata per l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente del controllo del codice sorgente. Questo approccio offre il controllo completo sull'integrazione del controllo del codice sorgente, ma richiede di fornire gli elementi dell'interfaccia utente e implementare le interfacce del controllo del codice sorgente che altrimenti verrebbero fornite con l'approccio plug-in.

 Per implementare un vspackage del controllo del codice sorgente, è necessario:

1. Creare e registrare il pacchetto VSPackage del controllo del codice sorgente, come descritto in [Registrazione e selezione.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

2. Sostituire l'interfaccia utente predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata. Vedere [Impostazioni Interfaccia utente](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Specificare i glifi da usare e gestire **Esplora soluzioni** glifi. Vedere [Controllo glifi.](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Gestire gli eventi Di modifica query e Salva query, come illustrato in [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Per altre informazioni, vedere Creazione [di un pacchetto VSPackage del controllo del codice sorgente.](../../extensibility/internals/creating-a-source-control-vspackage.md)

## <a name="see-also"></a>Vedi anche
- [Overview](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
