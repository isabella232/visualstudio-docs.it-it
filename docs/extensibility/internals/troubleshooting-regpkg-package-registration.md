---
title: Risoluzione dei problemi relativi alla registrazione dei pacchetti RegPkg Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704324"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione dei pacchetti RegPkg
> [!NOTE]
> Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'utilizzare i file con estensione pkgdef. Ciò consente la distribuzione delle estensioni senza dover accedere al Registro di sistema. I file Pkgdef vengono creati utilizzando [l'utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Per registrare un pacchetto utilizzando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]RegPkg in , è necessario utilizzare la versione di RegPkg appropriata per il pacchetto.

## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg Versioni correlate alle versioni del pacchetto
 Esistono due versioni di RegPkg. Una versione è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]inclusa in . Utilizzare questa versione per registrare i pacchetti compilati utilizzando uno dei seguenti assembly:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Non è possibile registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll precedente.

   La versione precedente di RegPkg può registrare i pacchetti compilati utilizzando l'assembly Microsoft.VisualStudio.Shell.dll. Tuttavia, non può registrare i pacchetti compilati utilizzando versioni successive di tale assembly.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
