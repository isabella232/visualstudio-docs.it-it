---
title: Creazione di un plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni su come creare un plug-in di controllo del codice sorgente che aggiunge una funzionalità di controllo del codice sorgente all'ambiente Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 652fe6311543e12965775218cc321a7a1542b3c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086742"
---
# <a name="create-a-source-control-plug-in"></a>Creare un plug-in del controllo del codice sorgente
L Visual Studio SDK fornisce risorse che consentono di aggiungere funzionalità di controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] all'ambiente di sviluppo integrato (IDE). Consente di usare qualsiasi DLL plug-in conforme all'API plug-in del controllo del codice sorgente descritta in questa documentazione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Operazioni preliminari](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Descrive come installare un plug-in del controllo del codice sorgente ed evidenzia le versioni attualmente disponibili dell'API Plug-in del controllo del codice sorgente.

- [Architettura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Usa un diagramma dell'architettura per spiegare l'integrazione di un plug-in di controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.

- [Guida ai test](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Fornisce indicazioni su come testare l'installazione e il funzionamento di un plug-in di controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un vspackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Viene illustrato come creare un vspackage del controllo del codice sorgente che non solo fornisce funzionalità di controllo del codice sorgente, ma sostituisce l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente del controllo del codice sorgente.

- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)

 Fornisce un elenco completo di tutti gli elementi nell'API plug-in del controllo del codice sorgente.

- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)

 Vengono illustrate le opzioni per l'implementazione del controllo del codice sorgente come funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
