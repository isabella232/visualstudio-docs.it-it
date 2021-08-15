---
title: Istanza sperimentale | Microsoft Docs
description: Informazioni su come Visual Studio SDK fornisce uno spazio sperimentale per eseguire applicazioni non testate in modalità di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 70f9d10595e1d0b458fc7102b48a1e1df8ee9daf6d2f04b993e7814891c41273
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447610"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
Per proteggere l Visual Studio di sviluppo di applicazioni non testate che potrebbero modificarlo, VSSDK offre uno spazio sperimentale che è possibile usare per sperimentare. Si sviluppano nuove applicazioni usando Visual Studio come di consueto, ma si eseguono usando questa istanza sperimentale.

 Ogni applicazione con un pacchetto VSIX avvia l'Visual Studio istanza sperimentale in modalità di debug.

 Se si vuole avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:

 *\<Visual studio installation path>*"\Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> L'istanza sperimentale viene scritta nel Registro di sistema nei `<version number>Exp` nodi `<version number>Exp_Config` e . Ad esempio, l Visual Studio area del Registro di sistema sperimentale di 2015 è
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 È consigliabile eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, questa viene eseguita nell'istanza di sviluppo. Per altre informazioni sulla registrazione di applicazioni, vedere [Registrazione di pacchetti VSPackage.](../extensibility/internals/registering-vspackages.md)
