---
title: L'istanza sperimentale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773581e7cf9e0f12f507dcd3c768d88724da9f80
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316422"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
Per proteggere l'ambiente di sviluppo di Visual Studio da applicazioni non testate che è possibile modificarlo, VSSDK offre uno spazio sperimentale che è possibile usare per provare. Si sviluppano nuove applicazioni con Visual Studio come di consueto, ma vengono eseguiti con l'istanza sperimentale.

 Ogni applicazione che dispone di un pacchetto VSIX Avvia istanza sperimentale di Visual Studio in modalità di debug.

 Se si desidera avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:

 " *\<Percorso di installazione di visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp

> [!NOTE]
> L'istanza sperimentale è scritto nel Registro di sistema sotto la `<version number>Exp` e `<version number>Exp_Config` nodi. Ad esempio è l'area del Registro di sistema sperimentale di Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 È consigliabile eseguire l'estensione nell'istanza sperimentale, mentre lo sviluppi. Quando si distribuisce l'estensione, viene eseguito nell'istanza di sviluppo. Per altre informazioni sulla registrazione delle applicazioni, vedere [la registrazione di pacchetti VSPackage](../extensibility/internals/registering-vspackages.md).