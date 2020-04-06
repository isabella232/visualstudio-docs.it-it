---
title: L'istanza sperimentale Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699031"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
Per proteggere l'ambiente di sviluppo di Visual Studio da applicazioni non testate che potrebbero modificarlo, VSSDK fornisce uno spazio sperimentale che è possibile utilizzare per sperimentare. Si sviluppano nuove applicazioni utilizzando Visual Studio come di consueto, ma le si esegue utilizzando questa istanza sperimentale.

 Ogni applicazione che dispone di un pacchetto VSIX avvia l'istanza sperimentale di Visual Studio in modalità di debug.

 Se si desidera avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:

 " Percorso di installazione di*\<Visual Studio>*'Common7'IDE'devenv.exe" /RootSuffix Exp

> [!NOTE]
> L'istanza sperimentale viene scritta nel Registro di sistema sotto i `<version number>Exp` nodi e `<version number>Exp_Config` . Ad esempio, l'area del Registro di sistema sperimentale di Visual Studio 2015 è
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 È consigliabile eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, viene eseguita nell'istanza di sviluppo. Per ulteriori informazioni sulla registrazione delle applicazioni, vedere [registrazione di pacchetti VSPackage](../extensibility/internals/registering-vspackages.md).
