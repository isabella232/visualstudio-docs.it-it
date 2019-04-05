---
title: L'istanza sperimentale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 907b90f60ad2167b64e5a4ca8ff160190c625313
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955659"
---
# <a name="the-experimental-instance"></a>Istanza sperimentale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per proteggere l'ambiente di sviluppo di Visual Studio da applicazioni non testate che è possibile modificarlo, VSSDK offre uno spazio sperimentale che è possibile usare per provare. Si sviluppano nuove applicazioni con Visual Studio come di consueto, ma vengono eseguiti con l'istanza sperimentale.  
  
 Ogni applicazione che dispone di un pacchetto VSIX Avvia istanza sperimentale di Visual Studio in modalità di debug.  
  
 Se si desidera avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:  
  
 "*\<Percorso di installazione di visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  L'istanza sperimentale è scritto nel Registro di sistema sotto la `<version number>Exp` e `<version number>Exp_Config` nodi. Ad esempio è l'area del Registro di sistema sperimentale di Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 È consigliabile eseguire l'estensione nell'istanza sperimentale, mentre lo sviluppi. Quando si distribuisce l'estensione, viene eseguito nell'istanza di sviluppo. Per altre informazioni sulla registrazione delle applicazioni, vedere [la registrazione di pacchetti VSPackage](../extensibility/internals/registering-vspackages.md).
