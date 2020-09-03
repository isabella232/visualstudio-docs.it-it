---
title: Creazione di un plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709176"
---
# <a name="create-a-source-control-plug-in"></a>Creazione di un plug-in del controllo del codice sorgente
Visual Studio SDK fornisce risorse che consentono di aggiungere funzionalità di controllo del codice sorgente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE). Consente di utilizzare qualsiasi DLL plug-in conforme all'API del plug-in del controllo del codice sorgente descritta in questa documentazione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Operazioni preliminari](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Viene descritto come installare un plug-in del controllo del codice sorgente e vengono evidenziate le versioni dell'API del plug-in del controllo del codice sorgente attualmente disponibili.

- [Architettura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Usa un diagramma dell'architettura per illustrare l'integrazione di un plug-in del controllo del codice sorgente con l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Guida ai test](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Vengono fornite informazioni aggiuntive su come testare l'installazione e il funzionamento di un plug-in del controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un pacchetto VSPackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce funzionalità di controllo del codice sorgente ma sostituisce l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente

- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)

 Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per implementare il controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
