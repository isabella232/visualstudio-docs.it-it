---
title: Risoluzione dei problemi di registrazione dei pacchetti RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 936cfbcdf64ae678626668fd5b20dc4de56d0107
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722063"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema. I file pkgdef vengono creati tramite il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Registrare un pacchetto usando RegPkg in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è necessario usare la versione di RegPkg appropriato per il pacchetto.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versioni RegPkg relativi alle versioni del pacchetto  
 Esistono due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Usare questa versione per registrare i pacchetti che sono stati compilati utilizzando uno degli assembly seguenti:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   È possibile registrare pacchetti che sono stati compilati con assembly shell precedenti.  
  
   La versione precedente di RegPkg può registrare i pacchetti che sono stati compilati con l'assembly di shell. Tuttavia, non è registrato i pacchetti compilati con versioni successive di tale assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Il rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)

