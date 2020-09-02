---
title: Istanza sperimentale | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699031"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
Per salvaguardare l'ambiente di sviluppo di Visual Studio da applicazioni non testate che potrebbero modificarlo, VSSDK fornisce uno spazio sperimentale che è possibile usare per sperimentare. Per sviluppare nuove applicazioni, è possibile usare Visual Studio come di consueto, ma è possibile eseguirle usando questa istanza sperimentale.

 Ogni applicazione che dispone di un pacchetto VSIX avvia l'istanza sperimentale di Visual Studio in modalità di debug.

 Se si vuole avviare l'istanza sperimentale di Visual Studio al di fuori di una soluzione specifica, eseguire il comando seguente nella finestra di comando:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/rootsuffix exp

> [!NOTE]
> L'istanza sperimentale viene scritta nel registro di sistema `<version number>Exp` nei `<version number>Exp_Config` nodi e. Ad esempio, l'area del registro di sistema sperimentale di Visual Studio 2015 è
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Si consiglia di eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, questa viene eseguita nell'istanza di sviluppo. Per ulteriori informazioni sulla registrazione di applicazioni, vedere la pagina relativa alla [registrazione di pacchetti VSPackage](../extensibility/internals/registering-vspackages.md).
