---
title: Istanza sperimentale | Microsoft Docs
description: Informazioni su come Visual Studio SDK fornisce uno spazio sperimentale per l'esecuzione di applicazioni non testate in modalità di debug.
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
ms.workload:
- vssdk
ms.openlocfilehash: aefac4efc706d195d8471952da3914d35d27ddc2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055882"
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
