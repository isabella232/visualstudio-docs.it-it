---
title: Risoluzione dei problemi di registrazione dei pacchetti RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5b2ebc470d12586957d77bbe7b076c053567742
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519782"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [risoluzione dei problemi di registrazione del pacchetto RegPkg](https://docs.microsoft.com/visualstudio/extensibility/internals/troubleshooting-regpkg-package-registration).  
  
> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema. I file pkgdef vengono creati tramite il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Registrare un pacchetto usando RegPkg in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è necessario usare la versione di RegPkg appropriato per il pacchetto.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versioni RegPkg relativi alle versioni del pacchetto  
 Esistono due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Usare questa versione per registrare i pacchetti che sono stati compilati utilizzando uno degli assembly seguenti:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 È possibile registrare pacchetti che sono stati compilati con assembly shell precedenti.  
  
 La versione precedente di RegPkg può registrare i pacchetti che sono stati compilati con l'assembly di shell. Tuttavia, non è registrato i pacchetti compilati con versioni successive di tale assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Il rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)

