---
title: Elementi di progettazione VSPackage del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulla struttura che il controllo del codice sorgente VSPackage deve implementare e le interfacce e i servizi che il controllo del codice sorgente VSPackage può implementare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a694ddc6ddd6c9872e242311ce6d197cbefc9520957e5506e238063bf8e233b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414389"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
Negli argomenti di questa sezione viene descritta la struttura che il pacchetto VSPackage del controllo del codice sorgente deve implementare per una completa integrazione. Elenca anche le interfacce e i servizi che il controllo del codice sorgente VSPackage può implementare e le interfacce e i servizi che il pacchetto VSPackage del controllo del codice sorgente può usare da altri componenti per supportare il modello e la funzionalità del controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definisce la struttura del controllo del codice sorgente VSPackage.

- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Elenca le interfacce e i servizi correlati al pacchetto di controllo del codice sorgente.

- [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Descrive il servizio di controllo del codice sorgente fornito dal pacchetto VSPackage del controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce funzionalità di controllo del codice sorgente, ma può essere usato per personalizzare l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente del controllo del codice sorgente.
