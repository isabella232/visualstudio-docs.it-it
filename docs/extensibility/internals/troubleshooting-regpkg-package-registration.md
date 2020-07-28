---
title: Risoluzione dei problemi di registrazione del pacchetto RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5266579ff235a0f6c4f3e555d79d5a00de2c194
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234861"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. Questo consente la distribuzione dell'estensione senza dover accedere al registro di sistema. I file pkgdef vengono creati usando l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Per registrare un pacchetto usando RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è necessario usare la versione di regpkg appropriata per il pacchetto.

## <a name="regpkg-versions-related-to-package-versions"></a>Versioni di RegPkg correlate alle versioni del pacchetto
 Sono disponibili due versioni di RegPkg. Una versione è inclusa in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Utilizzare questa versione per registrare i pacchetti compilati utilizzando uno degli assembly seguenti:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Non è in grado di registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll precedente.

   La versione precedente di RegPkg è in grado di registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll. Tuttavia, non è in grado di registrare i pacchetti compilati utilizzando versioni successive di tale assembly.

## <a name="see-also"></a>Vedere anche
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
