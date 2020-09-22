---
title: Risoluzione dei problemi di registrazione del pacchetto RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839744"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. Questo consente la distribuzione dell'estensione senza dover accedere al registro di sistema. I file pkgdef vengono creati usando l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Per registrare un pacchetto usando RegPkg in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è necessario usare la versione di regpkg appropriata per il pacchetto.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versioni di RegPkg correlate alle versioni del pacchetto  
 Sono disponibili due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Utilizzare questa versione per registrare i pacchetti compilati utilizzando uno degli assembly seguenti:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Non è in grado di registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll precedente.  
  
   La versione precedente di RegPkg è in grado di registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll. Tuttavia, non è in grado di registrare i pacchetti compilati utilizzando versioni successive di tale assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)
