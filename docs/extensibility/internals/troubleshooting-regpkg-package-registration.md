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
ms.openlocfilehash: 65acd78ef2591a84a1f48bd6a694996f48078d68
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905125"
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
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
