---
title: Risoluzione dei problemi di registrazione dei pacchetti RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5424ca9a1a51088a020d04faa55754ad487d5723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910537"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema. I file pkgdef vengono creati tramite il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Registrare un pacchetto usando RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario usare la versione di RegPkg appropriato per il pacchetto.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versioni RegPkg relativi alle versioni del pacchetto  
 Esistono due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Usare questa versione per registrare i pacchetti che sono stati compilati utilizzando uno degli assembly seguenti:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   È possibile registrare pacchetti che sono stati compilati con assembly shell precedenti.  
  
   La versione precedente di RegPkg può registrare i pacchetti che sono stati compilati con l'assembly di shell. Tuttavia, non è registrato i pacchetti compilati con versioni successive di tale assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)