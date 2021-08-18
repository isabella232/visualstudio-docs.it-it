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
ms.openlocfilehash: 515183771fd4063b20d7ea2ade416d1b84c31cfb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137457"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
Per proteggere il Visual Studio di sviluppo da applicazioni non testate che potrebbero modificarlo, VSSDK offre uno spazio sperimentale che è possibile usare per sperimentare. Si sviluppano nuove applicazioni usando Visual Studio come di consueto, ma è possibile eseguirle usando questa istanza sperimentale.

 Ogni applicazione con un pacchetto VSIX avvia l'istanza Visual Studio sperimentale in modalità di debug.

 Se si vuole avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:

 *\<Visual studio installation path>*"\Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> L'istanza sperimentale viene scritta nel Registro di sistema nei `<version number>Exp` nodi e `<version number>Exp_Config` . Ad esempio, l'Visual Studio del Registro di sistema sperimentale di 2015 è
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 È consigliabile eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, viene eseguita nell'istanza di sviluppo. Per altre informazioni sulla registrazione di applicazioni, vedere [Registrazione di VSPackage.](../extensibility/internals/registering-vspackages.md)
